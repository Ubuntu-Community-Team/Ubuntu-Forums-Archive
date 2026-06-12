---
title: "Help compiling program with cairo"
date: 2008-11-18
forum: Packaging and Compiling Programs
---

### Post by talguy on 2008-11-18
I am trying to compile on of my object files that use cairo of my program.  I keep getting an error saying cairo-features.h and cairo-deprecated.h were no found.  I checked out the usr/include/cairo directory and they are indeed in there.  Does anyone know what would be causing this error.  i am compiling my code using this command: g++ -c AnalogGauge.cpp.  Do i need to use a different compiler command.  Sorry if this is something stupid I am very new to linux (ubuntu) and I am using it as our base platform for my senior engineering project.  I did install cairo using this command sudo aptitude install libcairo2-dev.

Evan

---

### Post by Keith Hedger on 2008-11-18
u need to tell the compiler where to find the include files i think its -I/path/to/included/file

I always use autotools as they will generate a proper configure script maybe u should look into it?

---

### Post by talguy on 2008-11-18
ok thanks.

I started to make a makefile but could nt finish it until I knew all the right compiler commands I needed.

---

