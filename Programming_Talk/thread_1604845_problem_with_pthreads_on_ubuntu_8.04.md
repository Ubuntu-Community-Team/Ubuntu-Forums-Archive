---
title: "problem with pthreads on ubuntu 8.04"
date: 2010-10-24
forum: Programming Talk
---

### Post by dualslash on 2010-10-24
Hello. I am trying to run a c++ program using pthreads. But I get this error:

foodPass.o: In function `main':
foodPass.cpp:(.text+0x8bc): undefined reference to `pthread_create'
foodPass.cpp:(.text+0x907): undefined reference to `pthread_detach'
foodPass.cpp:(.text+0x972): undefined reference to `pthread_create'
foodPass.cpp:(.text+0x9b8): undefined reference to `pthread_detach'
collect2: ld returned 1 exit status
make: *** [foodPass] Error 1

I looked around for answers but I didn't find any that worked for me.

---

### Post by NovaAesa on 2010-10-24
It looks like you are having a linker problem (note the line that says "ld returned 1 exit status"). This is probably because you don't have the -lpthread flag passed into the linker. Try sticking this flag in to the command when you either try to link all the objects into one executable, or if you just have one file stick the flag straight in when you compile. Note: this is all coming from my memory... you might have to mess around with where the flag goes a litle bit, at least it will give you more ideas of what exactly to google for.

---

