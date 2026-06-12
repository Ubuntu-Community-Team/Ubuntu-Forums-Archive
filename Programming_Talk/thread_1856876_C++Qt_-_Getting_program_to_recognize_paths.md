---
title: "C++/Qt - Getting program to recognize paths"
date: 2011-10-09
forum: Programming Talk
---

### Post by hakermania on 2011-10-09
Let's say I've made a simple program that checks and prints out the file size of the file that is being inserted as 1st argument:
```

./myprogram file.txt
file.txt: 209 Bytes

```The program will work OK if
a) you specify only the filename of the file and the file is in the current working directory
b) you specify the full path to the file
c) inside the path you specify there's the '~' (which leads to -> $HOME), because I have a replace statement (*path.replace(QString("~"), QDir::homePath())*)

However, I cannot get it to work so as to recognize the '..' (previous path) path. 
For example:
```

$ ls
folder1 file.txt
$ cd folder1
$ ls
myprogram
$ ./myprogram ../file.txt
../file.txt: No such file or directory

```Any tips?

---

### Post by ofnuts on 2011-10-09
> **hakermania said:**
> Let's say I've made a simple program that checks and prints out the file size of the file that is being inserted as 1st argument:
```

./myprogram file.txt
file.txt: 209 Bytes

```The program will work OK if
a) you specify only the filename of the file and the file is in the current working directory
b) you specify the full path to the file
c) inside the path you specify there's the '~' (which leads to -> $HOME), because I have a replace statement (*path.replace(QString("~"), QDir::homePath())*)

However, I cannot get it to work so as to recognize the '..' (previous path) path. 
For example:
```

$ ls
folder1 file.txt
$ cd folder1
$ ls
myprogram
$ ./myprogram ../file.txt
../file.txt: No such file or directory

```Any tips?
If it"s not some kind of problem with access rights, we can't tell much without the source code. Reduce it to the 20 useful lines and post here.

Also, you shouldn't have to expand the tilde. This is done by the shell when you enter "~" on the keyboard, and the called executable never see the tilde. And if you call it from a script the script should use $HOME.

---

### Post by hakermania on 2011-10-09
Surprisingly, everything seems to be working fine now :)

---

