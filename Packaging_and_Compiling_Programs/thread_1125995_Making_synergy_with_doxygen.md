---
title: "Making synergy with doxygen"
date: 2009-04-14
forum: Packaging and Compiling Programs
---

### Post by lurikeen on 2009-04-14
Hi, ubuntu isn't letting me make synergy with doxygen. I did sudo apt-get install for synergy and doxygen successfully. The synergy website says 

> Synergy can automatically generate documentation from the comments in the code using doxygen. Use make doxygen to build it yourself from the source code into the doc/doxygen/html directory.

However, when I navigate to /usr/share/doc/synergy/doc, i dont see a folder named html.

I ran sudo doxygen -g in that directory (/usr/share/doc/synergy/doc) and tried to make doxygen, but it didn't work. I get this error message:

> make: *** No rule to make target `../configure.in', needed by `Makefile.in'.  Stop.

Can anyone help me please?

---

