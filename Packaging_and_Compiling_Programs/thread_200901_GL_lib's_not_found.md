---
title: "GL lib's not found"
date: 2006-06-20
forum: Packaging and Compiling Programs
---

### Post by realrbman on 2006-06-20
I upgraded my xorg drivers from xorg's to the proprietary ATI drivers. I messed around with things to get direct rendering to work. 
Some where along the way i messed up my OpenGL lib's. 
So now i can't compile my OpenGL code.

When i try i get:

[php]
burny@sixtybit:~/code/GL_examples$ make
gcc -L/usr/lib -L/usr/X11R6/lib -O2 lightposition.o glm.o sgi.o -lX11 -lGL -lGLU -lglut -lm -lXmu -lXi -o lightposition
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [lightposition] Error 1

[/php] 
Any idea's on how i could reverse this?

I've already tried reinstalling xorg-server, xorg-core and the regular xorg-firegl drivers.

Brian,

---

### Post by sykosayoko on 2006-08-04
I just tried:
ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
And it worked for me.

---

