---
title: "Need help : kernel header file"
date: 2007-07-24
forum: Programming Talk
---

### Post by wayanwolvie on 2007-07-24
Dear all,

I need to compile a C++ program which is using several kernel header files with this kind of writting pattern 
> #include <linux/xxx.h> 
and 
> #include <asm/xxx.h>. 
The problem is that the compiler cannot find  those header files. I have check the kernel header in
> /usr/src/linux-headers-2.6.18.1-custom/include
And all the files are there. I also boot using that kernel.

Is there anyway to solve this problem without changing the Makefile or the C++ codes?
Or any solutions without changing the C++ codes

By the way, I'm using Ubuntu 7.04 with a custom kernel 2.6.18.1

---

### Post by the_unforgiven on 2007-07-25
You could use a command like:
```
$ CXXFLAGS=-I /usr/src/linux-headers-2.6.18.1-custom/include make
```
The general convention is to use the CFLAGS (for C - gcc) and CXXFLAGS (for C++ - g++) env. variable to specify the options passed to the compiler.
So, if your Makefile is written according to the convention, the above command should work fine.

But, I doubt you can use the kernel code (function declarations etc) in any C++ code.
I hope you know what you're doing.
All the best ;)

---

### Post by wayanwolvie on 2007-07-26
It works, thanks

---

