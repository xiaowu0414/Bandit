---
date: 2025-11-18
---
## Level 0

要求描述：[BanditLevel_0](https://overthewire.org/wargames/bandit/bandit0.html)

使用ssh 即可连接到远程的服务器：ssh bandit0@bandit.labs.overthewire.org -p 2220，连接即可参与游戏

level0时，会先送你一个密码 bandit0，之后你会进入level 1，你的目标就是，找到level 1的密码，然后进入 level 2

---

## Level 0-1

进入服务器后，可以看到有个readme文件，打开就可以看到进入level1的密码了。

```bash
bandit0@bandit:~$ ll
total 24
drwxr-xr-x   2 root    root    4096 Oct 14 09:26 ./
drwxr-xr-x 150 root    root    4096 Oct 14 09:29 ../
-rw-r--r--   1 root    root     220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root    root    3851 Oct 14 09:19 .bashrc
-rw-r--r--   1 root    root     807 Mar 31  2024 .profile
-rw-r-----   1 bandit1 bandit0  438 Oct 14 09:26 readme
bandit0@bandit:~$ cat readme 
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

---

## Level 1-2

可以看到有个名为 - 的文件，查看他的内容即可

```bash
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

---

## Level 2-3

这一关文件名里有空格，需要用转义字符来限制space的意义.(否则bash会默认将space作为参数的分隔符)

实际上按 `Tab` 键就行

```bash
bandit2@bandit:~$ ll
total 24
drwxr-xr-x   2 root    root    4096 Oct 14 09:26 ./
drwxr-xr-x 150 root    root    4096 Oct 14 09:29 ../
-rw-r--r--   1 root    root     220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root    root    3851 Oct 14 09:19 .bashrc
-rw-r--r--   1 root    root     807 Mar 31  2024 .profile
-rw-r-----   1 bandit3 bandit2   33 Oct 14 09:26 --spaces in this filename--
bandit2@bandit:~$ cat ./--spaces\ in\ this\ filename-- 
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

---

## Level 3-4

这一关只需要移动到对应文件夹，然后打开文件即可

```bash
bandit3@bandit:~$ ll
total 24
drwxr-xr-x   3 root root 4096 Oct 14 09:26 ./
drwxr-xr-x 150 root root 4096 Oct 14 09:29 ../
-rw-r--r--   1 root root  220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root root 3851 Oct 14 09:19 .bashrc
drwxr-xr-x   2 root root 4096 Oct 14 09:26 inhere/
-rw-r--r--   1 root root  807 Mar 31  2024 .profile
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ll
total 12
drwxr-xr-x 2 root    root    4096 Oct 14 09:26 ./
drwxr-xr-x 3 root    root    4096 Oct 14 09:26 ../
-rw-r----- 1 bandit4 bandit3   33 Oct 14 09:26 ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ./...Hiding-From-You 
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

---

## Level 4-5

这一关打开文件时，记得使用 `./` 来说明这是文件，如此即可避免文件被误识别为参数选项

以及，这一关要求是唯一人类可读的文件。(可以使用file 来查看文件类型，ASCII text 为人类可读的)

```bash
bandit4@bandit:~$ ll
total 24
drwxr-xr-x   3 root root 4096 Oct 14 09:26 ./
drwxr-xr-x 150 root root 4096 Oct 14 09:29 ../
-rw-r--r--   1 root root  220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root root 3851 Oct 14 09:19 .bashrc
drwxr-xr-x   2 root root 4096 Oct 14 09:26 inhere/
-rw-r--r--   1 root root  807 Mar 31  2024 .profile
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ll
total 48
drwxr-xr-x 2 root    root    4096 Oct 14 09:26 ./
drwxr-xr-x 3 root    root    4096 Oct 14 09:26 ../
-rw-r----- 1 bandit5 bandit4   33 Oct 14 09:26 -file00
-rw-r----- 1 bandit5 bandit4   33 Oct 14 09:26 -file01
-rw-r----- 1 bandit5 bandit4   33 Oct 14 09:26 -file02
-rw-r----- 1 bandit5 bandit4   33 Oct 14 09:26 -file03
-rw-r----- 1 bandit5 bandit4   33 Oct 14 09:26 -file04
-rw-r----- 1 bandit5 bandit4   33 Oct 14 09:26 -file05
-rw-r----- 1 bandit5 bandit4   33 Oct 14 09:26 -file06
-rw-r----- 1 bandit5 bandit4   33 Oct 14 09:26 -file07
-rw-r----- 1 bandit5 bandit4   33 Oct 14 09:26 -file08
-rw-r----- 1 bandit5 bandit4   33 Oct 14 09:26 -file09
bandit4@bandit:~/inhere$ file . ./-file0*
.:         directory
./-file00: data
./-file01: OpenPGP Public Key
./-file02: OpenPGP Public Key
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./-file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

---

## Level 5-6

要求人类可读，大小为1033c，不可执行。

```bash
bandit5@bandit:~$ ll
total 24
drwxr-xr-x   3 root root    4096 Oct 14 09:26 ./
drwxr-xr-x 150 root root    4096 Oct 14 09:29 ../
-rw-r--r--   1 root root     220 Mar 31  2024 .bash_logout
-rw-r--r--   1 root root    3851 Oct 14 09:19 .bashrc
drwxr-x---  22 root bandit5 4096 Oct 14 09:26 inhere/
-rw-r--r--   1 root root     807 Mar 31  2024 .profile
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$ ll
total 88
drwxr-x--- 22 root bandit5 4096 Oct 14 09:26 ./
drwxr-xr-x  3 root root    4096 Oct 14 09:26 ../
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere00/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere01/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere02/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere03/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere04/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere05/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere06/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere07/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere08/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere09/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere10/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere11/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere12/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere13/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere14/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere15/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere16/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere17/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere18/
drwxr-x---  2 root bandit5 4096 Oct 14 09:26 maybehere19/
bandit5@bandit:~/inhere$ find . -type f ! -executable -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

---

## Level 6-7

任意位置查找文件

注意通过`2>/del/null` 将报错的输出扔掉

```bash
bandit6@bandit:/$ find -user bandit7 -group bandit6 -size 33c 2>/dev/null 
./var/lib/dpkg/info/bandit7.password
bandit6@bandit:/$ cat ./var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```

---

## Level 7-8

找到文件中的内容

```bash
bandit7@bandit:~$ grep 'millionth' ./data.txt 
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

---

## Level 8-9

查看，排序，计数并只保留一个，按第一列当作数字排序，只输出第一列

(实际上技术后可以直接 grep 1)

```bash
bandit8@bandit:~$ cat data.txt | sort | uniq -c | sort -k1n | head -n1
      1 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

发现一种更简便的实现方式：
（uniq -u 只输出唯一的，uniq -d 只输出重复的）

```bash
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

---

## Level 9-10

因为文件是二进制文件，所以不能直接用grep

```bash
bandit9@bandit:~$ file data.txt 
data.txt: data
bandit9@bandit:~$ strings data.txt | grep ==
========== the
========== password
f\Z'========== is
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

---

## Level 10-11

解码就行

```bash
bandit10@bandit:~$ base64 --decode ./data.txt
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

---

## Level 11-12

利用tr 来进行变换

```bash
bandit11@bandit:~$ cat data.txt | tr 'a-z' 'n-za-m' | tr 'A-Z' 'N-ZA-M'
	The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

---

## Level 12-13

他告诉你是16进制转储文件，用xxd -r 换回二进制，然后一步步查看文件类型，一步步重命名，解压即可

需要注意的是：linux 有一个特性，文件名后缀和文件格式可以不一样。

```bash
bandit12@bandit:/tmp/wuzizaizuobian$ file data.txt 
data.txt: ASCII text
bandit12@bandit:/tmp/wuzizaizuobian$ xxd -r data.txt data_0
bandit12@bandit:/tmp/wuzizaizuobian$ file data_0 
data_0: gzip compressed data, was "data2.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 564
bandit12@bandit:/tmp/wuzizaizuobian$ mv data_0 data_1.gz; gzip -d data_1.gz
bandit12@bandit:/tmp/wuzizaizuobian$ ll
total 10024
drwxrwxr-x     2 bandit12 bandit12     4096 Nov 19 12:16 ./
drwxrwx-wt 16182 root     root     10244096 Nov 19 12:16 ../
-rw-rw-r--     1 bandit12 bandit12      564 Nov 19 12:15 data_1
-rw-r-----     1 bandit12 bandit12     2573 Nov 19 11:24 data.txt
bandit12@bandit:/tmp/wuzizaizuobian$ file data_1
data_1: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/wuzizaizuobian$ mv data_1 data_2.bz2; bzip2 -d data_2.bz2
bandit12@bandit:/tmp/wuzizaizuobian$ ll
total 10024
drwxrwxr-x     2 bandit12 bandit12     4096 Nov 19 12:17 ./
drwxrwx-wt 16183 root     root     10244096 Nov 19 12:17 ../
-rw-rw-r--     1 bandit12 bandit12      423 Nov 19 12:15 data_2
-rw-r-----     1 bandit12 bandit12     2573 Nov 19 11:24 data.txt
bandit12@bandit:/tmp/wuzizaizuobian$ file data_2 
data_2: gzip compressed data, was "data4.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/wuzizaizuobian$ mv data_2 data_3.gz; gzip -d data_3.gz
bandit12@bandit:/tmp/wuzizaizuobian$ file data_3 
data_3: POSIX tar archive (GNU)
bandit12@bandit:/tmp/wuzizaizuobian$ mv data_3 data_4.tar; tar -xvf data_4.tar
data5.bin
bandit12@bandit:/tmp/wuzizaizuobian$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/wuzizaizuobian$ mv data5.bin data_6.tar; tar -xvf data_6.tar
data6.bin
bandit12@bandit:/tmp/wuzizaizuobian$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/wuzizaizuobian$ mv data6.bin data_7.bz2; bzip2 -d data_7.bz2
bandit12@bandit:/tmp/wuzizaizuobian$ ll
total 10064
drwxrwxr-x     2 bandit12 bandit12     4096 Nov 19 12:20 ./
drwxrwx-wt 16184 root     root     10244096 Nov 19 12:20 ../
-rw-rw-r--     1 bandit12 bandit12    20480 Nov 19 12:15 data_4.tar
-rw-r--r--     1 bandit12 bandit12    10240 Oct 14 09:26 data_6.tar
-rw-r--r--     1 bandit12 bandit12    10240 Oct 14 09:26 data_7
-rw-r-----     1 bandit12 bandit12     2573 Nov 19 11:24 data.txt
bandit12@bandit:/tmp/wuzizaizuobian$ file data_7
data_7: POSIX tar archive (GNU)
bandit12@bandit:/tmp/wuzizaizuobian$ mv data_7 data_8.tar; tar -xvf data_8.tar
data8.bin
bandit12@bandit:/tmp/wuzizaizuobian$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Tue Oct 14 09:26:06 2025, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/wuzizaizuobian$ mv data8.bin data_9.gz; gzip -d data_9.gz
bandit12@bandit:/tmp/wuzizaizuobian$ ll
total 10068
drwxrwxr-x     2 bandit12 bandit12     4096 Nov 19 12:21 ./
drwxrwx-wt 16184 root     root     10244096 Nov 19 12:21 ../
-rw-rw-r--     1 bandit12 bandit12    20480 Nov 19 12:15 data_4.tar
-rw-r--r--     1 bandit12 bandit12    10240 Oct 14 09:26 data_6.tar
-rw-r--r--     1 bandit12 bandit12    10240 Oct 14 09:26 data_8.tar
-rw-r--r--     1 bandit12 bandit12       49 Oct 14 09:26 data_9
-rw-r-----     1 bandit12 bandit12     2573 Nov 19 11:24 data.txt
bandit12@bandit:/tmp/wuzizaizuobian$ file data_9
data_9: ASCII text
bandit12@bandit:/tmp/wuzizaizuobian$ cat data_9
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```

---

## Level 13-14

注意，使用私钥登录时，密钥文件的权限应该是600才行.
之后使用私钥登录bandit14即可。

```bash
tulei@tulei:~$ chmod 600 bandit14_key 
tulei@tulei:~$ ssh -i bandit14_key bandit14@bandit.labs.overthewire.org -p 2220
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```

---

## Level 14-15

```bash
bandit14@bandit:~$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
```




