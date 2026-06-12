---
title: "can't build simple gtkmm app in Eclipse"
date: 2010-08-13
forum: Programming Talk
---

### Post by imax36581 on 2010-08-13
hi
i use this tutorial to build my first gtkmm application
[http://kapo-cpp.blogspot.com/2007/02/gtkmm-and-eclipse.html](http://kapo-cpp.blogspot.com/2007/02/gtkmm-and-eclipse.html)
but i get this error in console,when i try to build my project:

```
**** Build of configuration Release for project test001 ****

make all 
Building target: test001
Invoking: GCC C++ Linker
g++ `pkg-config --libs gtkmm-2.4` -o"test001"  ./main.o   
/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [test001] Error 1

```
i add gtkmm in include directories and follow the instruction i specified before but i dont know what this error mean....

---

