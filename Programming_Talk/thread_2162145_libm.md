---
title: "libm"
date: 2013-07-13
forum: Programming Talk
---

### Post by sundaresh on 2013-07-13
I have a simple program which uses log and floor. When I try compiling it with gcc with -lm option it returns undefined reference to these functions and a.out is not generated. However if I just compile gcc -c myprogram.c it generates myprogram.o, and then if I link
with ld -lm myprogram.o it links with the libm but generates warning cannot find entry symbol start defaulting to "some address", but
a.out is generated.The funny thing is bash does not recognize this file when I try to execute it with ./a,out and gives an error message
no such file or directory.

---

### Post by trent.josephsen on 2013-07-13
ld by itself does not create an executable file; you need to give it extra options and link with libc. I forget the exact incantation. What output does gcc myprogram.o -lm give you?

---

### Post by sundaresh on 2013-07-13
gcc gives undefined reference to log and floor, ld exit status 1. 
I cannot find any libm.a or libm.so file in /lib or /usr/lib or /var/lib.
Where can I download this file and in which directory do I put it ?

---

### Post by steeldriver on 2013-07-13
It should be at /usr/lib/i386-linux-gnu/libm.so or /usr/lib/x86_64-linux-gnu/libm.so depending on the machine architecture - if it's not, try

```
sudo apt-get install build-essential
```

it will ensure you have the libc6-dev development headers and libraries

Also link ORDER is important - make sure you are linking the library AFTER your source code i.e.

```
gcc yourproj.c -lm
```

NOT

```
gcc -lm yourproj.c
```

---

