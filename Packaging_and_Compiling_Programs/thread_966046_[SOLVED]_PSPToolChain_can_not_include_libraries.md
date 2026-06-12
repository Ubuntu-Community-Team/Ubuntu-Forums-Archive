---
title: "[SOLVED] PSPToolChain can not include libraries"
date: 2008-11-01
forum: Packaging and Compiling Programs
---

### Post by ajtaggs on 2008-11-01
I have installed and compiled a few simple programs using PSPtoolchain, however when ever I try to include a library that didn't come with the PSPtoolchain installation, I get an error.

```
ajtaggs@Programmer:~/Lesson4$ make
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -Wall -D_PSP_FW_VERSION=150   -c -o main.o main.c
main.c:11:17: error: png.h: No such file or directory
make: *** [main.o] Error 1
```

I have installed the necessary libraries (I believe), and I have png.h as you can see from this:

```
ajtaggs@Programmer:~$ whereis png.h
png: /usr/include/png.h /usr/share/man/man5/png.5.gz

```

Is there a way of telling psptoolchain to look in another directory for libraries?

Thanks

---

### Post by ajtaggs on 2008-11-02
NM, I just figured it out, thanks for all the replies lol

:)

---

