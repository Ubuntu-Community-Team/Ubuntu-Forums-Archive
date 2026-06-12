---
title: "lost configure recently"
date: 2007-11-13
forum: Packaging and Compiling Programs
---

### Post by Axehammer on 2007-11-13
Greetings,

yesterday I tried compiling a program for the first time since I upgraded to Gutsy.  I haven't been able to configure so that I can then make the program.  

I was going through the standard 
./configure
make 
make install

but the configure command was missing.  

three weeks ago I was able to build one fine with Feisty.  Has anyone else had this problem, and what did you do to get the command back?

thanks

---

### Post by geraldm on 2007-11-13
The smaller the project, the less likely it is to use the automated tools.

Small projects often do not use configure.  There usually will be a 
Makefile, README, or INSTALL file.  Get it where the source is to 
be found.  That place should be within one of the files in the package.

If configure is missing, it is too much trouble to recreate it.  Make do
without it.

Gerald

---

### Post by dholbach on 2007-11-15
If you come across Makefile.am, configure.ac and other files in the source directory, try running autoreconf -i to regenerate the Makefiles and the configure script. (Also make sure you have all the necessary build dependencies installed.)

---

