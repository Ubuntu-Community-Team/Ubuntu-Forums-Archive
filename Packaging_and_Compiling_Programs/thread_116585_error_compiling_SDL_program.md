---
title: "error compiling SDL program"
date: 2006-01-13
forum: Packaging and Compiling Programs
---

### Post by transkinetic on 2006-01-13
I wrote a small bitmap editor in DevC++ using SDL today. It's my first program and I'm needless to say quite thrilled with it.

Trying to compile it on ubuntu with gcc produced the following error.

spacepopeye@yimmy:~/SDL/zombie$ gcc zombie3.cpp -o sdltest `sdl-config --cflags --libs`
/tmp/ccH6rpJv.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

I have no idea how to use gcc. The parameters there are from some SDL tut. Is their a good indroduction to GCC somwhere?

---

### Post by asimon on 2006-01-14
zombie3.cpp, is it a c++ program? Then you should use g++ instead of gcc. If it's pure C, try to rename it to zombie.c and use gcc.

For an intro see [An Introduction to GCC by Brian Gough](http://www.network-theory.co.uk/docs/gccintro/). And 'man gcc' is also a good source if you need to look-up some flags.

---

### Post by transkinetic on 2006-01-15
Perfect, thanks.

---

