---
title: "Make Command"
date: 2010-10-14
forum: Packaging and Compiling Programs
---

### Post by cppgraphics on 2010-10-14
Hi folks,

I'm new bee to linux os, trying to set a plugin development environment in my linux. 

mkdir -p $HOME/devkit/cd $HOME/devkit/cp -r /usr/autodesk/maya/devkit/plug-ins .make Cleanmake


In the 4th step, I'm getting the following error

"make: *** No targets specified and no makefile found.  Stop."



Please somebody explain, how can I use of Make command in a proper way?

Thanks.

---

### Post by MadCow108 on 2010-10-14
when this is exactly what you typed into the terminal it can not work.

if you want to chain commands onto a single line you either have to split them with semicolons or mostly better with &&

&& will only execute the next command when the one before returns a success exit code (= zero)

also usually the clean target is written small, but it depends on the makefile.
(clean target removes all temporary files created by compilation if the makefile is well behaved)

This is probably the correct command:
mkdir -p $HOME/devkit/ && cd $HOME/devkit/ && cp -r /usr/autodesk/maya/devkit/plug-ins . && make clean && make

make requires a file named Makefile in the directory you are executing it.
If there is non something is wrong with the instructions.

---

