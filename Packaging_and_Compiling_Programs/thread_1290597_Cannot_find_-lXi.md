---
title: "Cannot find -lXi"
date: 2009-10-13
forum: Packaging and Compiling Programs
---

### Post by Shazzner on 2009-10-13
I'm trying to compile some of the examples from the ARToolkit, unfortunately I run  across this error when I make it:
```
~/ARToolKit/examples/simple$ make
cc -o ../../bin/simpleTest simpleTest.o  -pthread -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lxml2 -lglib-2.0 -L/usr/X11R6/lib -L/usr/local/lib -L../../lib -lARgsub -lARvideo -lAR -lpthread -lglut -lGLU -lGL -lXi -lX11 -lm
/usr/bin/ld: cannot find -lXi
collect2: ld returned 1 exit status
make: *** [../../bin/simpleTest] Error 1

```
This is a new installation of ubuntu so I might not have any of the required packages. I do have freeglut3-dev, but it seems I'm missing an X11 package but I can't seem to find any references to that.

Here's the page on compiling it in linux:
[http://www.hitl.washington.edu/artoolkit/documentation/usersetup.htm#comp_linux]("http://www.hitl.washington.edu/artoolkit/documentation/usersetup.htm#comp_linux")

---

### Post by Bachstelze on 2009-10-13
You can install the xorg-dev metapackage to install al the X11 headers. If you want individual packages, the lib you're looking for is in libxi6/libxi-dev.

---

### Post by Shazzner on 2009-10-13
Thanks! It compiled after grabbing that specific package.

---

### Post by sazawal on 2010-02-12
Thanks

I had the same problem

---

