---
title: "How to find executable file if you don't know it?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by garyed on 2008-09-09
I know how to use "which" to find where an executable is & to check a programs launcher if its on the desk top but what if I had no idea of what the name of the executable file is. Is there a command that will list only executable files? Of course in Windows you can just search for .exe files & take your pick but since Linux is wiser & doesn't need to see an extension it creates a problem for the unwise.

---

### Post by hakimaki on 2008-09-09
look in /usr/bin

---

### Post by ronnielsen1 on 2008-09-09
Games will be in /usr/games or /usr/local/games

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

> /usr - This is one of the most important directories in the system as it
contains all the user binaries. X and its supporting libraries can be
found here. User programs like telnet, ftp etc are also placed here.
/usr/doc contains useful system documentation. /usr/src/linux contains the
source code for the Linux kernel.

---

### Post by howlingmadhowie on 2008-09-09
```
find . -perm /u+x -type f

```

should do it

---

### Post by lazyart on 2008-09-09
if you installed it from package manager you can go there, find the package and see what files it installed.

---

### Post by gabak on 2010-06-21
hi
how can i use ur command to find VLC executable?



> **howlingmadhowie said:**
> ```
find . -perm /u+x -type f

```

should do it

---

### Post by dim3000 on 2010-06-21
try:
```
whereis vlc
```

---

### Post by gabak on 2010-06-21
thank you so much
it worked like a charm.
anyways if you know how to use the other command that the other guy told here , that will be great.
a new thing to learn. ;-)

---

### Post by bigsmitty64 on 2010-06-21
> **dim3000 said:**
> try:
```
whereis vlc
```
so simple....everyday I learn :)   Thanks

---

### Post by Paqman on 2010-06-21
Just one tip: on Linux you don't actually need to know the full path to the executable to launch it.

For example, to launch VLC the command is simply:
```
vlc
```
...you don't need to supply the whole /usr/bin or whatever. In general, the command to launch an application is the same as the package name in Synaptic. If that doesn't work then hitting the manual page at:
```
man *packagename*
```
might help out. Unfortunately most man pages are appallingly badly written, but they do contain a lot of useful info.

---

### Post by gabak on 2010-06-21
yes i know that but when i decide to open a file in graphic mode it ask you where it is the file that you want to use to open a file like for instance AVI or MPG

if u want to use other than totem , like vlc ex

---

