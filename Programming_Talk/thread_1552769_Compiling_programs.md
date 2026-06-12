---
title: "Compiling programs?"
date: 2010-08-14
forum: Programming Talk
---

### Post by BlackKinght on 2010-08-14
Hi, so this may be a VERY noob question but when i try and compile a program using gcc it always says "there is no such file or directery" or "gcc: no input". I am just trying to get the a.out i think but not sure. I am using the command "gcc firstprog.c", am I doing something worng? Thanks for your help and please go easy on me I am new to this haha

---

### Post by jtarin on 2010-08-14
What program are you trying to compile?

---

### Post by lisati on 2010-08-14
[Edit: Moved to "Programming talk"]

If your current working directory[*] is the same as where the source file is stored, it's usually something like:
```
gcc filename.c
```
where "filename.c" is your source file.

You can also use: 
```
gcc filename.c -o outputfile 
```
(where "outputfile" is the name you want to give the executable program)

If you use the first one and there are no errors, you can run the program with:
```
./a.out
```

With the second example, you can run the program with:
```
./outputfile
```



[*]Use the "cd" command to navigate to the directory where the source file is stored.

---

### Post by ssam on 2010-08-14
you should probably get familiar with a few basic commands.
[https://help.ubuntu.com/10.04/basic-commands/C/](https://help.ubuntu.com/10.04/basic-commands/C/)

---

