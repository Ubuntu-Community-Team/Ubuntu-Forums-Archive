---
title: "install libg++ failed."
date: 2008-09-17
forum: Programming Talk
---

### Post by tmtmtmtm on 2008-09-17
I need to install libg++-2.7.2 for my project, not 2.8 or later.

It is an ancient libg++ in 1996.

I have downloaded the libg++ src package from [ftp://prep.ai.mit.edu/pub/gnu/](ftp://prep.ai.mit.edu/pub/gnu/).

THere is a error when I build it, as below.
>./configure
......
>make
.....
gcc -02 -c -g -I. -I./../include strerror.c
strerror.c:459: conflicting types for 'sys_errlist'
/usr/include/bits/sys_errlist.h:28: previous declaration of 'sys_errlist'
make[1]:***[strerror.o] Error 1

-----------------------------------
sys_errlist is a file of GNU C Library.
   
    Does it mean GNU C Library changed in these years, 
    so that my old libg++ cannot be built with it?

WHAT CAN I DO ABOUT IT???

---

