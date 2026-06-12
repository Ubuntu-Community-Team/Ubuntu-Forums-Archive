---
title: "32 bit libraries under 64 bit machine"
date: 2013-08-25
forum: Packaging and Compiling Programs
---

### Post by david-davidgf on 2013-08-25
Hi people,

THis has already been asked, but no answers so far. The thing is that I want to compile a program using -m32 (with gcc/g++).
The idea is that it will use the 32 bit libraries present in the system, but no luck so far. In another ubuntu machin I used to had there was (just an example) libgcc.a: 

/usr/lib/gcc/x86_64-linux-gnu/4.6/libgcc.a
/usr/lib/gcc/x86_64-linux-gnu/4.6/32/libgcc.a

And gcc/ld are smart enough to choose the appropiate one. But now with my Ubutnu 12.04.3 LTS it seems that the libraries are missing... If I try to install them using multiarch (like apt-get install libgcc1:i386) it fails, it tries to delete the 64 bit system libs :(

Any ideas? Thanks!

---

