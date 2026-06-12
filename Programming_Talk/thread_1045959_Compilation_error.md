---
title: "Compilation error"
date: 2009-01-21
forum: Programming Talk
---

### Post by void_void on 2009-01-21
when i fire following command i got the following result

xlc_r –q64 –qarch=auto –qmkshrobj HelloWorld.c –o libhello.so

Ccommand not found

i am very new to ubuntu so please tell me how to overcome  it

THanks in advance

---

### Post by jpkotta on 2009-01-21
Did you install the xlc compiler?  IIRC, it's from AIX; I'm not even sure it can run on Linux.

Can your project build with GCC?  Did you install build-essential?

---

### Post by jespdj on 2009-01-21
Who told you to use "xlc"? That indeed seems to be [IBM's compiler for AIX](http://www.nersc.gov/nusers/resources/software/ibm/xlc.html).

Install build-essential:
```
sudo apt-get install build-essential
```
And use gcc to compile your program:
```
gcc hello.c -o hello
```
Read: [FAQ: Compiling your first C or C++ programs](http://ubuntuforums.org/showthread.php?t=689635) and [FAQ: Troubleshooting common C and C++ compilation errors](http://ubuntuforums.org/showthread.php?t=691451).

---

