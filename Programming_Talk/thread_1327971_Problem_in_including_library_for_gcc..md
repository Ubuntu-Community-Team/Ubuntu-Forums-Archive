---
title: "Problem in including library for gcc."
date: 2009-11-16
forum: Programming Talk
---

### Post by rohitkugve on 2009-11-16
Hi,

I have a C code that makes use of POSIX semaphores( sem_open(), sem_wait() etc...). the man page says "Programs using the POSIX semaphores API must be compiled with cc -lrt to link against the real-time library, librt". So I compile it with 

**$gcc -lrt -c mycode.c**

This compiles fine on my Ubuntu9.10 desktop. But it doesn't compile on a console-only PC104 board running kernel-2.6.23, with gcc version3.2.3, and ld version 2.14.90. I get the following error

[B]/usr/bin/ld: cannot find -lrt
collect2: ld returned 1 exit status
make[1]: *** [comm_handler] Error 1[/B]

I tried using -lposix4 instead of -lrt as suggested somewhere on net but same problem.

Should I install the real time library, if so how do I do that. Thank you.
-Rohit

---

### Post by Zugzwang on 2009-11-16
Did you install the "build-essential" package? According to the search function on "packages.ubuntu.com", it is contained in the "libc" package, for which the development version should definitely be installed when you install "build-essential", which you need for compiling in Ubuntu anyway.

---

### Post by dwhitney67 on 2009-11-16
By the way, the following statement makes no sense:
```

$gcc -lrt -c mycode.c

```
The -c option is telling gcc to compile mycode.c, and to produce an object file.  The -lrt never comes into play here because the linker is never called.

If later, you are performing a link to build the executable, then it would appear as:
```

$gcc mycode.o -lrt

```
Undoubtedly your code is dependent on the real-time library; not the other way around.  Thus you should specify the -l option after your object file, not before it.  The linker can sometimes be finicky if a library is not specified in the correct order.

Anyhow, if you do not have the file /usr/lib/librt.so (or /usr/lib/librt.a) on your system, then specifying -lrt is a moot point.

---

