---
title: "Can't make kernel module (stopped working)"
date: 2015-04-13
forum: Programming Talk
---

### Post by rob18767 on 2015-04-13
Hi

I have been working as a hardware developed (Altera FPGA and PCI express) in conjunction with a guy who has been writing linux drivers, as well as user space applications for the embedded linux system we are developing. 

Unfortunately the guy no longer like the Midwest and has left to take a job at Microsoft (everyone can go boo now) in Seattle. 

While we have someone who can write the user space applications, as I have significant experience in embedded C programming and as I understand the hardware better than anyone else, I am getting the job of writing the drivers. 

I have been successfully using IOCTL calls to do the polling however now I need read and write system calls however, for a reason I do not understand, my make (Makefile) command causes an error. I wont post the lot of it as it is long. So here's a taste. 

> In file included from include/linux/init.h:4:0,                 from /home/rob/driver/mod_evio.c:1:
include/linux/compiler-gcc4.h:36:45: error: storage class specified for parameter ‘__UNIQUE_ID_license0’
 #define __UNIQUE_ID(prefix) __PASTE(__PASTE(__UNIQUE_ID_, prefix), __COUNTER__)
                                             ^
include/linux/compiler.h:48:23: note: in definition of macro ‘___PASTE’
 #define ___PASTE(a,b) a##b
                       ^
include/linux/compiler-gcc4.h:36:29: note: in expansion of macro ‘__PASTE’
 #define __UNIQUE_ID(prefix) __PASTE(__PASTE(__UNIQUE_ID_, prefix), __COUNTER__)
                             ^
include/linux/compiler.h:49:22: note: in expansion of macro ‘___PASTE’
 #define __PASTE(a,b) ___PASTE(a,b)




Basically I installed the Kernel sources and I am building against them.  I think the unique ID is what is giving me the problem but I am clueless for now. 

Any help would be appreciated as to what is going on.... 

Thank you.

---

### Post by ofnuts on 2015-04-14
Seen this?

[http://stackoverflow.com/questions/3676969/error-storage-class-specified-for-parameter](http://stackoverflow.com/questions/3676969/error-storage-class-specified-for-parameter)

---

