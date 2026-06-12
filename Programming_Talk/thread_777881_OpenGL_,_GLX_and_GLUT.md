---
title: "OpenGL , GLX and GLUT"
date: 2008-05-01
forum: Programming Talk
---

### Post by sireel on 2008-05-01
I have a slightly bizarre problem with the titled things, in that I've got OpenGL and GLX devellopment packages all installed, but I can't seem to get GLUT dev packages installed, if I install them and attempt to compile an openGL program, every singl gl* function throws an error of 'function not defined' whereas without GLUT installed, these don't come up (just complaints that glut.h doesn't exist)

the second part of the problem is that I had thought it would be easier to just learn GLX instead, but I can't find a single tutorial on how to use it, despite rather a lot of googling. Maybe I'm being stupid, I don't know. 

Im using ubuntu Hardy, proprietry nvidia driver, with nvidia-new-glx-dev for the openGL libs. Any help with either problem would be greatly appreciated.

Edit: It should be noted that I'm new to programming for linux so I'm likely to have made stupid mistakes somewhere.

---

### Post by kknd on 2008-05-02
How you are compiling your program?

Here, a "gcc source.c -o exec -lglut" works fine

---

### Post by sireel on 2008-05-02
aha! thankyou very much. I'm afraid when i said i was new to coding for linux i really meant it, i'm used to compilers being ran from whatever IDE i'm using, so all the options that could be supplied to the compiler are a bit of a mystery to me.

---

