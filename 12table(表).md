[TOC]

### table(表)的构造

```lua
-- 初始化表
mytable = {}

-- 指定值
mytable[1]= "Lua"

-- 移除引用
mytable = nil
-- lua 垃圾回收会释放内存
```

当我们为 table a 并设置元素，然后将 a 赋值给 b，则 a 与 b 都指向同一个内存。如果 a 设置为 nil ，则 b 同样能访问 table 的元素。如果没有指定的变量指向a，Lua的垃圾回收机制会清理相对应的内存。

### Table操作

-   table.concat(list [, sep [, i [, j]]])：提供一个列表，其所有元素都是字符串或数字，返回字符串 `list[i]..sep..list[i+1] ··· sep..list[j]`。 `sep` 的默认值是空串， `i` 的默认值是 1 ， `j` 的默认值是 `#list` 。 如果 `i` 比 `j` 大，返回空串。

    ```lua
    tab = {1, 2, 3}
    table.concat(tab, '_', 1, 2)
    > 1_2
    ```

-   table.insert(table, [pos,] value)：在table的数组部分指定位置(pos)插入值为value的一个元素. pos参数可选, 默认为数组部分末尾
-   table.remove(table [, pos])：删除元素，pos为删除的下标，默认是最后一个
-   table.sort(table, [, comp])：升序排序，comp为自定义比较函数，如果提供，它必须是一个可以接收两个列表内元素为参数的函数。 当第一个元素需要排在第二个元素之前时，返回真 （因此 `not comp(list[i+1],list[i])` 在排序结束后将为真）。