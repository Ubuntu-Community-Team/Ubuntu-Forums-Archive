---
title: "gcc myprogram.c -o myprogram.o -lpthread"
date: 2009-07-15
forum: Programming Talk
---

### Post by rahul_shilps on 2009-07-15
Hi all,

I fire a command to compile my c program:

gcc ipsee.c -o ipsee.o -lpthread

where,

       ipsee.c - is the name of my c program

I want to know **what is**
           1) -o option
           2) .o file
           3) -lpthread
:popcorn:

---

### Post by dwhitney67 on 2009-07-15
> **rahul_shilps said:**
> Hi all,

I fire a command to compile my c program:

gcc ipsee.c -o ipsee.o -lpthread

where,

       ipsee.c - is the name of my c program

I want to know **what is**
           1) -o option
           2) .o file
           3) -lpthread
:popcorn:
The -o is used to indicate the name of the output file

The -lpthread is used to indicate that you will link with the pthread library.

Your command has an issue with it... you are indicating that you want to compile/link the source file (.c file) to form an executable, yet your output file has a .o extension, indicating that you perhaps wanted an object file.

The correct statement would be:
```

gcc ipsee.c -o ipsee -pthread

```

Alternatively:
```

gcc -c ipsee.c -o ipsee.o
gcc ipsee.o -o ipsee -lpthread

```
Note that when generating the object file using the -c option, specifying -o is optional.  The default will be to create a .o file using the name of the .c file.

If you do not specify the -o option when linking, then an a.out file will be created.  This file would be the executable file.  In the examples I provided above, 'ipsee' will be your executable file.

---

### Post by rahul_shilps on 2009-07-16
Yes ipsee.o becomes the executable file.
 
Yes. Whne i fire command "./ipsee.o" it executes the program and i can see the output.
 
Thanks a lot. I got an abstract concept but can you please elaborate the what is pthread and why i need to link it with my source file/ executable object file?
 
Thank you again.
-Rahul

---

### Post by credobyte on 2009-07-16
> **rahul_shilps said:**
> Yes ipsee.o becomes the executable file.
 
Yes. Whne i fire command "./ipsee.o" it executes the program and i can see the output.
 
Thanks a lot. I got an abstract concept but can you please elaborate the what is pthread and why i need to link it with my source file/ executable object file?
 
Thank you again.
-Rahul

[http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html) ;)

---

### Post by dwhitney67 on 2009-07-16
> **rahul_shilps said:**
> Yes ipsee.o becomes the executable file.
 
Yes. Whne i fire command "./ipsee.o" it executes the program and i can see the output.
 
Thanks a lot. I got an abstract concept but can you please elaborate the what is pthread and why i need to link it with my source file/ executable object file?
 
Thank you again.
-Rahul
I have no idea what your program, ipsee.c, does or entails.  Thus I do not know if you need to link pthread.so or not.

As for libpthread.so, it is a shared-object library located in /usr/lib.  A program that requires it would reference functions that are defined within this library during runtime.

If a program is dependent on an external library, and the program is not linked with that library, then undoubtedly "undefined reference" errors would occur and the executable would not be created.

---

