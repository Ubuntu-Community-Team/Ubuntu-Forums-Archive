---
title: "Problem compiling c and c++"
date: 2014-03-23
forum: Packaging and Compiling Programs
---

### Post by arg2810 on 2014-03-23
I'm trying to understand what is the error that appears when I compile  c or c++ file in ubuntu 13.10. The console output when I try to compile is the follow:

In file included from /usr/include/stdio.h:27:0,
                 from Ejercicio3.c:1:
/usr/include/features.h:371:25: fatal error: sys/cdefs.h: No existe el archivo o el directorio
 #  include <sys/cdefs.h>
In file included from /usr/include/stdio.h:27:0,
                 from Ejercicio3.c:1:
/usr/include/features.h:371:25: fatal error: sys/cdefs.h: No existe el archivo o el directorio
 #  include <sys/cdefs.h>

Maybe I missing some package, or something else but I really don't get what could be problem. 

Thanks a lot for your help in advance.

---

### Post by steeldriver on 2014-03-23
Hello and welcome to the forums

Make sure the libc6-dev package is installed (it is installed by default if you install the build-essential package, but may not have been if you just installed the bare gcc and/or g++ compilers)

---

### Post by arg2810 on 2014-03-23
I think is something else, I have installed build-essential package and also de the libc6 package...

---

### Post by spjackson on 2014-03-23
Does the file /usr/include/sys/cdefs.h exist and is it readable by you? If so, please post the source you are trying to compile and the command you are using to compile it.

---

### Post by arg2810 on 2014-03-23
The file doesn't exist, there is only a broken link. I'm trying to compile in a subcarpet on home and I'm compiling like this: "gcc archivo.c -o archivo" and "g++ archivo.cpp -o archivo" in both ways I have the error that I mentioned before.

---

### Post by spjackson on 2014-03-24
> **arg2810 said:**
> The file doesn't exist, there is only a broken link. I'm trying to compile in a subcarpet on home and I'm compiling like this: "gcc archivo.c -o archivo" and "g++ archivo.cpp -o archivo" in both ways I have the error that I mentioned before.
My mistake, I had referred to an old Ubuntu installation. On 13.10 (64-bit) cdefs.h is at /usr/include/x86_64-linux-gnu/sys/cdefs.h and this is provided by libc4-dev:amd64.

Nevertheless, if you have broken links in /usr/include, you probably have broken packages that should be reinstalled.

---

### Post by arg2810 on 2014-03-24
I can't find libc4-dev:amd64, I find a similar package call libc6-dev-amd64:i386 but for installed it I have to eliminated the package g++,gcc and build-essencial. I try it and it doesn't work either.

---

### Post by arg2810 on 2014-03-24
I found the problem, it seems to be a problem with a instalation of some package related with the compiler of C, after reinstall all the packages related with this everything works fine. Thanks a lot for your time.

---

### Post by mandar2 on 2014-05-22
Hello there arg2810,

I am trying to compile my atmega16 Helloworld.c program using avr toolchain for linux and i have same issue

/usr/include/features.h|374|fatal error: sys/cdefs.h: No such file or directory|

> after reinstall all the packages related

Please tell me which all packages do you mean?

I am strugling with it for days.

Regards.

---

