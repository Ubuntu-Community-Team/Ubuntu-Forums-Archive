---
title: "C++ and f77 &quot;undefined reference&quot;...maybe missing lg2c?"
date: 2006-09-29
forum: Programming Talk
---

### Post by kamikaze04 on 2006-09-29
Hi all,

I'm trying to compile an application of my work, that is written in c++ and fortran. Everything compiles fine, until it says:

make[2]: Leaving directory `/home/km/project/build/myproj/Util'
make -C compiler
make[2]: Entering directory `/home/km/project/build/myproj/compiler'
make -C GCC
make[3]: Entering directory `/home/km/project/build/myproj/compiler/GCC'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/km/project/build/myproj/compiler/GCC'
make[2]: Leaving directory `/home/km/project/build/myproj/compiler'
rm -f myproj.a && ar r myproj.a `find . -name '*.o'`
ar: creating myproj.a
g++ -o mypro-3.5.0    myproj.a
myproj.a(reduce.o): In function `fndiam_':reduce.f:(.text+0x8e9): undefined reference to `s_wsle'
:reduce.f: (.text+0x907): undefined reference to `do_lio'
:reduce.f: (.text+0x924): undefined reference to `do_lio'
:reduce.f: (.text+0x942): undefined reference to `do_lio'
:reduce.f: (.text+0x960): undefined reference to `do_lio'
:reduce.f: (.text+0x97e): undefined reference to `do_lio'
:reduce.f: (.text+0x988): undefined reference to `e_wsle'
:reduce.f: (.text+0x99c): undefined reference to `s_stop'
:reduce.f: (.text+0xa7f): undefined reference to `s_wsle'
:reduce.f: (.text+0xa9d): undefined reference to `do_lio'

Why it is not recognizing nothing of fortran? It compiled fine, but here it seems to be missing something. It is compiling fine in a fedora core and gentoo...but here no...it's just a matter of packet...but which?
I have installed gcc,g++,g77 and make.

Any kind of idea? Every little comment will be very wellcome ](*,) 

Thanks forum!

---

### Post by junglepeanut on 2006-10-01
I have no idea, but you said every little comment might help.

1.) I am 90% sure you have not linked to a certain library.

2.) The library is linked but a fake library with paths is not linked. 

3.) Your path is no good for the library.

4.) What does your makefile look like? Is it calling the wrong compiler for fortran?

---

