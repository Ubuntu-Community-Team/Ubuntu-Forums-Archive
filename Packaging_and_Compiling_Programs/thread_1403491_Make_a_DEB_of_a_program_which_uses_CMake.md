---
title: "Make a DEB of a program which uses CMake?"
date: 2010-02-10
forum: Packaging and Compiling Programs
---

### Post by gusnan on 2010-02-10
What is the proper way to make a deb from a program that uses CMake?
I am trying to package my program which I code using Cmake, but when I package it I got warnings about 
make and make clean - So I thought - of course - How should it know about cmake and the CMakelists.txt stuff? So I expected it to need a Makefile or autotools stuff - Said and done - I made a Makefile, and managed to get through that part of the package building process. But now - running pbuilder later in the packaging guide I see that it runs through a cmake ..? How come? - I have my program setup with a CMakelists.txt, and expect the user who build from source to create a build folder and run 'cmake ..' from there - and I didn't think the deb packaging stuff would know about this.

So - What is the proper way to build a package of a program that uses CMake as building system?

Should I keep all CMake stuff, and also make some kind of minimal Makefile that just tells the packaging
programs how to proceed?

---

### Post by SevenMachines on 2010-02-10
unless your build set up is especially unusually you'll might just want to use cdbs to package if possible. The nice debian people already have a cdbs class for cmake so you can just add

include /usr/share/cdbs/1/class/cmake.mk

to your debian/rules file and your packaging build should automagically work!

[EDIT] Note that if you dont use autotools or makefiles then you just need the cmake.mk class and debhelper.mk in your debian/rules 
see /usr/share/cdbs/1/rules/ and /usr/share/cdbs/1/class for all the useful cdbs magic

---

### Post by gusnan on 2010-02-10
Thank you! That was very helpful!

---

