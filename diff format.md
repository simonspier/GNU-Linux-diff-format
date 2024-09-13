Linux中的diff指令用来对比两个文件之间的变化，返回一个patch(补丁)来说明两者之间的区别或变化。说明文件更新迭代很有帮助。
主要介绍两种diff format。分别是context format上下文格式和unified format统一格式。unified format相比context format格式的优势是更加简洁，相反的context format的优势是信息更加完整。
diff命令的格式大致形式为 diff [arguement] [from_file] [to_file]，这篇介绍中arguement参数主要是两种<-c>和<-u>，对应以上两种返回的patch的格式。


from_file:

```
The Way that can be told of is not the eternal Way;
The name that can be named is not the eternal name.
The Nameless is the origin of Heaven and Earth;
The Named is the mother of all things.
Therefore let there always be non-being,
  so we may see their subtlety,
And let there always be being,
  so we may see their outcome.
The two are the same,
But after they are produced,
  they have different names.
```

to_file:

```
The Nameless is the origin of Heaven and Earth;
The named is the mother of all things.

Therefore let there always be non-being,
  so we may see their subtlety,
And let there always be being,
  so we may see their outcome.
The two are the same,
But after they are produced,
  they have different names.
They both may be called deep and profound.
Deeper and more profound,
The door of all subtleties!
```


**context格式：**
执行命令 diff -C 1 from_file to_file

patch：
```
*** from_file 2002-02-21 23:30:39.942229878 -0800
--- to_file	2002-02-21 23:30:50.442260588 -0800
***************
*** 1,5 ****
- The Way that can be told of is not the eternal Way;
- The name that can be named is not the eternal name.
  The Nameless is the origin of Heaven and Earth;
! The Named is the mother of all things.
  Therefore let there always be non-being,
--- 1,4 ----
  The Nameless is the origin of Heaven and Earth;
! The named is the mother of all things.
! 
  Therefore let there always be non-being,
***************
*** 11 ****
--- 10,13 ----
    they have different names.
+ They both may be called deep and profound.
+ Deeper and more profound,
+ The door of all subtleties!
```

其中：
`*表示from_file，-表示to_file`
`***number1，number2 ***`表示from_file的number1行到number2行
--- number1，number2 ---表示to_file的number1行到number2行

每一行前面的字符一共三种：
[space] 表示两者没有变化
[!]表示此行有差异
[-]表示from_file存在但是to_file没有
[+]表示to_file存在但是from_file没有


**unified format格式：**
执行命令 diff -u  from_file to_file

patch：

```
--- from_file 2002-02-21 23:30:39.942229878 -0800
+++ to_file	2002-02-21 23:30:50.442260588 -0800
@@ -1,7 +1,6 @@
-The Way that can be told of is not the eternal Way;
-The name that can be named is not the eternal name.
 The Nameless is the origin of Heaven and Earth;
-The Named is the mother of all things.
+The named is the mother of all things.
+
 Therefore let there always be non-being,
   so we may see their subtlety,
 And let there always be being,
@@ -9,3 +8,6 @@
 The two are the same,
 But after they are produced,
   they have different names.
+They both may be called deep and profound.
+Deeper and more profound,
+The door of all subtleties!
```

其中：
@@ -1,7 +1,6 @@
表示from_file从第1行开始往后7行，to_file从第一行开始往后6行
