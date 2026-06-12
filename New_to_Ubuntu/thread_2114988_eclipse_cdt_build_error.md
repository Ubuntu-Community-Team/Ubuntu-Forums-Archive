---
title: "eclipse cdt build error"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by linux spartan on 2013-02-11
help...i am a newbie and trying to build and compile c projects in eclipse indigo using the cdt plugin.i first make a new c project aloisi then make a new source file lol.c and on the console i get the following output 
**** Build of configuration Debug for project aloisi ****

make all 
Building target: aloisi
Invoking: GCC C Linker
gcc  -o "aloisi"  ./lol.o   
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [aloisi] Error 1

**** Build Finished ****

the errors specified are:
Description                                   Resource      Type
make: *** [aloisi] Error 1            aloisi             C/C++ Problem
undefined reference to `main'    aloisi             C/C++ Problem

in the project explorer no binaries are getting displayed from which i can run
and only displayes includes lol.c and debug which contains lol.o,lol.d,makefile,objects.mk,sources.mk,subdir.mk

---

### Post by linux spartan on 2013-02-12
made new thread in programming [http://ubuntuforums.org/showthread.php?p=12506309&posted=1#post12506309](http://ubuntuforums.org/showthread.php?p=12506309&posted=1#post12506309)

---

