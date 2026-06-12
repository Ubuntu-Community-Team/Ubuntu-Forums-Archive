---
title: "pkg-config + OpenGL"
date: 2008-06-17
forum: Packaging and Compiling Programs
---

### Post by GhostCoder on 2008-06-17
Hi

I wonder why pkg-config doesn't find anything opengl-related stuff on my box (8.04). I googled that "pkg-config --libs gl" should work, but it won't. Is this correct? "pkg-config --libs glut" doesn't work either.

I still have gl/glut development packages (freeglut3) installed and I have used a manual setup so far and linked with -lglut. 

Is there something wrong with my setup or is there some other way to check where OpenGL stuff lies?

---

### Post by WW on 2008-06-20
A library is only visible to pkg-config if an appropriate configuration file (with extension .pc) is put in the directory /usr/lib/pkgconfig (or some other standard location where pkg-config looks, such as /usr/local/lib/pkgconfig).  If the authors (or packagers) of the library did not create such a file, the library will not be seen by pkg-config.

Apparently the authors of freeglut3 have not created a .pc file. In Debian and its derivatives (including Ubuntu), the .pc file is usually included with the -dev packacge.  [This list of freeglut3-dev files](http://packages.ubuntu.com/hardy/i386/freeglut3-dev/filelist) does not contain a .pc file, so this library is not visible to pkg-config.  Likewise, the file lists for libglu1-mesa-dev and other GL/GLU packages do not include .pc files.

---

