---
title: "g++ question"
date: 2009-01-18
forum: Packaging and Compiling Programs
---

### Post by bo01 on 2009-01-18
Hello
I searched it but didn't find an answer.

I compile and run some programs in c++ with g++ and I use the flag **-lpq** in order to manage the build a program that uses an external library (database lib).

My question is what exactly does this (or these?) flag/s? First of all, I think -lpq is not one argument but I don't know (and I cannot find it) what -l does or -p or -pq or -q...

Is it so obvious???

THANX in advance

---

### Post by Catalyst2Death on 2009-01-18
I think (someone correct me) that the -lpq option refers to libpq.  This flag tells the linker that it needs code from the libpq library.

---

### Post by bo01 on 2009-01-18
Thank u Catalyst.
So its one flag and not two or three together in one? Can u be more specific? Why is this flag necessary as I have included the library in my program?
Thanks again

---

### Post by pansz on 2009-01-18
-lpq means link (-l) the libpq.a or libpq.so library, which should be in the library search path specified by -L

man gcc should give you everything detail.

---

### Post by snova on 2009-01-18
> **bo01 said:**
> So its one flag and not two or three together in one? Can u be more specific? Why is this flag necessary as I have included the library in my program?

Short answer; there are headers, and then there are libraries. You need both.

#include merely makes the library available to you by exposing its interface, but you need to link the library in before the finished program can actually use the code. This is what -lpq is for- it specifies a library to be linked in.

---

### Post by bo01 on 2009-01-19
Thanks a lot guys. Its clear now!

---

