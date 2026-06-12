---
title: "What is the c++ compiler for ubuntu?"
date: 2009-05-11
forum: Packaging and Compiling Programs
---

### Post by shababhsiddique on 2009-05-11
I am using netbeans IDE. I cannot compile c++ codes. The compiler directories shows empty.
 I have installed multi language bundle package. It works fine with C and java codes. 
pleeaaaseeeeee help

---

### Post by Bodsda on 2009-05-11
Not sure about your problem, but to answer the thread title question,

g++

---

### Post by shababhsiddique on 2009-05-12
I installed Netbeans IDE 6.5 multi language. But I cannot compile any c++ code. 
it gives these errors-

Running "/usr/bin/make  -f Makefile CONF=Debug" in /home/shabab/NetBeansProjects/Welcome_1

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/shabab/NetBeansProjects/Welcome_1'
/usr/bin/make  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/welcome_1
make[2]: Entering directory `/home/shabab/NetBeansProjects/Welcome_1'
mkdir -p build/Debug/GNU-Linux-x86
rm -f build/Debug/GNU-Linux-x86/welcome.o.d
cpp-4.3    -c -g -MMD -MP -MF build/Debug/GNU-Linux-x86/welcome.o.d -o build/Debug/GNU-Linux-x86/welcome.o welcome.cc
cpp-4.3: "-c" is not a valid option to the preprocessor
make[2]: *** [build/Debug/GNU-Linux-x86/welcome.o] Error 1
make[2]: Leaving directory `/home/shabab/NetBeansProjects/Welcome_1'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/shabab/NetBeansProjects/Welcome_1'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.

It prompts for -"resolve missing native build tools" and show directories of C,C++ and fortran compiler where c++ field is blank. If i browse to find the compilers. There are
 
/usr/bin/gcc selected for C compiler
C++ is left blank

I cannot find g++ on that directory. Where can i find it? Do I have to download it?

---

### Post by waspbr on 2009-05-12
paste this into terminal 
```
sudo apt-get install build-essential
```

---

### Post by shababhsiddique on 2009-05-13
> **waspbr said:**
> paste this into terminal 
```
sudo apt-get install build-essential
```

Thanks, but, whats this all about?? :o

---

### Post by lisati on 2009-05-13
> **shababhsiddique said:**
> Thanks, but, whats this all about?? :o

It installs a number of things useful for compiling, including a C++ compiler.

---

### Post by shababhsiddique on 2010-03-06
...... .....

---

