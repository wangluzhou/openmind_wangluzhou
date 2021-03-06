# 2017-07-26
创建

# exercise 5:
```Python
print "Let's talk about %s." % my_name
print "He's %d inches tall." % my_height
```
各类格式符汇总：
- %s:字符串 (采用str()的显示)
- %r:字符串 (采用repr()的显示)
- %c:单个字符
- %b:二进制整数
- %d:十进制整数
- %i:十进制整数
- %o:八进制整数
- %x:十六进制整数
- %e:指数 (基底写为e)
- %E:指数 (基底写为E)
- %f:浮点数
- %F:浮点数，与上相同
- %g:指数(e)或浮点数 (根据显示长度)
- %G:指数(E)或浮点数 (根据显示长度)
- %%：字符"%",**如果要在格式化字符串里面包括百分号，那么必须使用`%%`**。举例如下：
```Python
print "The year-on-year growth of CPI is %s%%." % "1.6"
# output:
# The year-on-year growth of CPI is 1.6%
```

注：
 1. 如果是列表或者是字典的话，格式化后只是一个值，只有元组可以格式化成多个值
 2. 多个转换变量需要用圆括号括起来

参考资料：
- [Python字符串格式化学习一](http://www.cnblogs.com/mingaixin/archive/2012/10/12/2720914.html)

# exercise 8:
```Python
# encoding: utf-8
formatter = "%r %r %r %r"
print formatter % (
    "I had this thing.",
    "That you could type up right.",
    "But it didn't sing.",
    "So I said goodnight."
)
```
使用`%r`转换符的时候，如果转换变量本身为字符串，那么会自带`''`,但是如果转换变量本身含有`''`,那么最外面的单引号将会变成双引号。


exercise 10:
转义字符汇总：

|转义字符|	描述|
|-------|------|
|\(在行尾时)|	续行符|
|\\	|反斜杠符号|
|\'|	单引号|
|\"|	双引号|
|\a|	响铃|
|\b|	退格(Backspace)
|\e|	转义|
|\000|	空|
|\n|	换行|
|\v|	纵向制表符
|\t|	横向制表符
|\r|	回车|
|\f|	换页|
|\oyy|	八进制数yy代表的字符，例如：\o12代表换行|
|\xyy|十进制数yy代表的字符，例如：\x0a代表换行|
|\other|	其它的字符以普通格式输出|

`'''`和`"""`效果是一样的。

输入以下代码来测试`%r`和`%s`的效果:
```Python
print "%s" % "\"\"\'\'dada"
print "%r" % "\"\"\'\'dada"
```
输出结果如下：
```shell
""''dada
'""\'\'dada'
```
很奇怪，双引号的转义符号没有打印出来，但是单引号的转义符号打印出来了。

# exercise 11
注意： `raw_input`在python3中已经被'input'取代。
关于`raw_input`和`input`的区别。（[参考资料](http://www.cnblogs.com/way_testlife/archive/2011/03/29/1999283.html)）
```Python
>>> raw_input_A = raw_input("raw_input: ")
raw_input: abc
>>> input_A = input("Input: ")
Input: abc
# 产生报错信息
Traceback (most recent call last):
  File "<pyshell#1>", line 1, in <module>
    input_A = input("Input: ")
  File "<string>", line 1, in <module>
NameError: name 'abc' is not defined
>>> input_A = input("Input: ")
Input: "abc"
>>>
```
从这个例子可以看出，`raw_input`和`input`虽然都可以接受字符串，但是`input`必须读取一个合法的Python字符串，即需要在字符串前后加入双引号或者单引号。
此外，`raw_input`把所有的输入都默认设置成`str`类型,而`input`可以根据输入数据的特征进行类型归类，比如输入数字可能是`float`或者`int`型。

# exercise 12:
查看 内间函数文档：
```shell
pydoc 函数名
```

# exercise 14:
## error：
```
Traceback (most recent call last):
  File "ex14.py", line 3, in <module>
    script, user_name = argv
ValueError: need more than 1 value to unpack
```
写执行命令的时候总是忘记写arguments

---
## error：
`else`后面不小心添加了冒号.

---

# exercise 15:

- `open`函数获得一个`file`对象，然后调用`file`对象的`read`方法。

- 关于PythonAPI查询，推荐网站：[Python文档](https://docs.python.org)
- 我觉得使用argv的方法显得好一点。主要原因在高效快捷，减少程序占用资源的时间。
- 不需要看那些包含 __ （两个下划线）的命令，这些只是垃圾而已。

---

## error:
总是把文件名和脚本名称写错

---

# exercise 16

关于file对象的操作：
- close：关闭文件
- read: 读取文件内容，并返回string 对象
- readline: 读取文本文件的一行
- write(stuff): 将stuff写入文件
- open()中加入参数'w',就会变成写模式，程序就有了权限修改文件，同时如果一开始没有文件，程序也可以自动创建文件。

# exercise 17
- cat命令
- 如果我直接写
`indata = open(from_file).read()`
那这个文件对象如何close()呢？
- 关于`file.close()`:如果你不调用close方法，是无法完成文件的写入的。另一方面，文件数据会占据缓存，如果不及时释放的话，会一直占据，浪费资源空间。当然由于这里我们写的是脚本，体现不出这个问题。

# exercise 18:
 1. 函数定义以def开始
 2. 函数名称由字符串和下划线组成
 3. 函数名称后紧跟着括号`()`
 4. 括号里可以包含参数也可以不包含，多个参数以逗号隔开
 5. 参数名称不可以重复
 6. 紧跟着参数的是括号和冒号 ):
 7. 紧跟着函数定义的代码需要使用 4 个空格的缩进 (indent)
 8. 函数结束的位置也要缩进

# exercise 20:
`file.seek(offset[, whence])`
file.seek()方法标准格式是：seek(offset,whence=0)
- offset：开始偏移量，也就是代表需要移动偏移的字节数。
- whence：给offset参数一个定义，表示要从哪个位置开始偏移；0代表从文件开头开始算起，1代表从当前位置开始算起，2代表从文件末尾算起。

# exercise 25:
- `import` 的时候不需要加`.py`后缀
- 当函数的输入参数为列表时，那就是引用传递，函数内对列表任意的改动，都会导致列表本身的改动。
- 使用help(ex25)可以打印出函数列表和各自的注释。

# exercise 29:
- if 为下一行代码提供条件入口，下一行代码从属于if子块，因此需要缩进。

# erercise 32:
- range的用法：
 1. range(10) -> [0,1,2,3,4,5,9],注意最后一位不是10
 2. range(1, 10) ->[1,2,3,4,5,9],注意最后一位不是10，但是第一位是1，类似于[)区间
 3. range(0, -10, -1)->[0, -1, -2, -3, -4, -5, -6, -7, -8, -9],确定步长-1

# exercise 33:
- 尽量少用while-loop，尽量多用for-loop,防止程序意外陷入死循环。

----

- 在print语句中总是忘记写入格式化字符了
- `def while_loop(lim=6, step=1,numbers):
SyntaxError: non-default argument follows default argument`
在函数的argument中，没有默认值的必须排在有默认值的前面。
- File ".\ex33.py", line 13, in <module>
    while_loop(lim, numbers, step)
NameError: name 'while_loop' is not defined
Python解释器是逐行读取的，因此，在调用函数前，一定要把函数定义写在调用语句前面，确保在调用函数前，解释器已经都到了函数的定义。
- range如果要确定步长，必须将起始点，结束点都写进去，即`range(start, end, step)`
----

# exercise 33:
- 序数ordinal number)和基数(cardinal number)：

|Cardinal|Ordinal|
|--------|-------|
|one|first|
|two|second|
|three|third|

# exercise 35:
- int()的用法：Return an integer object constructed from a number or string x, or return 0 if no arguments are given.
- exit()是操作系统提供的，作用为退出应用程序，删除进程使用的内存空间，并将应用程序的一个状态返回给OS，这个状态表示了应用程序的一些运行信息，0为正常退出，1为非正常退出。
- 判断一个字符串是否为数字可以用isdigit()方法(正负号和小数点无法判断)

# erercise 36:
- 每一条if语句必须有一个else
- if语句嵌套不要超过两层
- if段落前面和后面都最好空一行
- 复杂的福尔运算最好事先存放在一个变量里面
- 除了while TRUE 尽量不要用while-loop
- 最好的调试方法是使用print在各个想要检查的的关键环节将关键变量打印出来。
- 让程序一步一步运行起来，不要等一个很长的脚本写完之后才去运行它。

# exercise 37:
- 几个不熟悉的操作运算符：

|符号|含义|
|---|---|
|//|求商|
|//=|求商|
|%=|求余数|
|**=|幂|

# exercise 39:
- dir(something)用于查看对象的所有属性。
- print 最后加上逗号的目的是使得所有输出在同一行
```Python
while True:
    print "State? (ENTER to quit)",
    state = raw_input("> ")
    if not state: break
```

# exercise 40:
读代码的三种技巧：
1. 从前向后
2. 从后向前
3. 逆时针方向：从中间出发，左，右，左，右....

# exercise 41:
有限状态机(finite state machine)：有限状态自动机 (FSM：Finite State Machine)，简称状态机，是表示有限多个状态以及在这些状态之间转移和动作的数学模型。状态存储关于过去的信息，它反映从系统开始到现在时刻输入的变化；转移指示状态变更，用必须满足来确使转移发生的条件来描述它；动作是在给定时刻要进行的活动描述。

# exercise 42:
- `getattr()`:Get a named attribute from an object; getattr(x, 'y') is equivalent to x.y.
When a default argument is given, it is returned when the attribute doesn't exist; without it, an exception is raised in that case.
- python中的函数和变量一样，都是可以传递和赋值的，唯一的区别就是函数后面可以加()进行调用。
- `__init__`里面定义的成员变量只存在于实例的`__dict__`，而对象中定义方法只有在对象的`__dict__`才有
