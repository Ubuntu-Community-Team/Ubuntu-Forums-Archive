---
title: "Compile Error"
date: 2008-05-29
forum: Programming Talk
---

### Post by Dambrosio on 2008-05-29
I am trying to compile a Qt4 application that is linked to a FORTRAN module. I am using qdevelop and I have successfully linked the same FORTRAN module with a small test program. 

I get this error when trying to build:
```
Build (make)...
g++ -Wl,--no-undefined -o bin/standardatmo build/dialogimpl.o build/main.o build/atmogroup.o build/atmosphere-mod.o build/moc_dialogimpl.o build/moc_atmogroup.o build/qrc_imgs.o  -L/usr/lib/g95/lib/gcc-lib/i686-pc-linux-gnu/4.0.3 -lf95   -L/usr/lib -lQtGui -lQtCore -lpthread 
/usr/lib/gcc/i486-linux-gnu/4.2.3/libstdc++.so: undefined reference to `_Unwind_GetIPInfo@GCC_4.2.0'
collect2: ld returned 1 exit status
make: *** [bin/standardatmo] Error 1
``` 

I edited the makefile (attached) so it would compile and link the FORTRAN object file.

I looked on some forums and it said my error has something to do with my g++ directories or something. Anyone have a idea?

Thanks,
Dan

---

