## 题目

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

示例:
```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

## Golang版本

### 思路
1. 简单遍历法
2. 利用Hash遍历

#### 1. 简单遍历法

将数组全部进行遍历，相加进行比较

##### Code
```
func twoSum(nums []int, target int) []int {
    var result []int
    for i := 0; i < len(nums); i ++ {
        for j := i + 1; j < len(nums); j ++ {
            if nums[i] + nums[j] == target {
                result = append(result, i)
                result = append(result, j)
            }
        }
    }
    return result
}
```
##### 分析

时间复杂度为O(n平方），空间复杂度为O(1)

##### 结果

执行用时：80 ms

内存消耗：3 MB

#### 2. 利用Hash遍历

通过以空间换取速度的方式，可以对运算时间进行优化

##### Code
```
func twoSum(nums []int, target int) []int {
    var maps = make(map[int]int, len(nums) - 1)
    result := make([]int,0)
    for index,val := range nums {
        if _,ok := maps[target - val];ok {
            result = []int{maps[target - val], index}
            break
        }
        maps[val] = index
    }
    return result
}

```
##### 分析

时间复杂度为O(n），空间复杂度为O(n)

##### 结果

执行用时：4 ms	

内存消耗：3.4 MB
