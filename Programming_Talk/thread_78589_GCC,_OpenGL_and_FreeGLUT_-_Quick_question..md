---
title: "GCC, OpenGL and FreeGLUT - Quick question."
date: 2005-10-18
forum: Programming Talk
---

### Post by SeanCallan on 2005-10-18
To date I have GCC and FreeGLUT installed and working fine.

I have a file light.c which simulates animation of a light source.  It compiles without warning/errors; however, when I run it I get this:

```
sean@Doomspork:~/Desktop$ ./light
freeglut (./light): OpenGL GLX extension not supported by display ':0.0'
```

Am I missing a repo?

---

### Post by mlomker on 2005-10-18
> OpenGL GLX extension not supported by display ':0.0'[/CODE]


Are you, by chance, running 64-bit?  That error [resembles the errors]("http://www.ubuntuforums.org/showthread.php?p=422244#post422244") that 64-bit ATI users are getting right now--3D is essentially broken in Breezy 64-bit.

Can you run other openGL applications, such as screen savers?

---

### Post by SeanCallan on 2005-10-18
I'm not using 64bit actually and I have an nvidia card.

I have no problem with previewing the screen savers, I don't have one set to run though.

---

### Post by ubuntu_123 on 2005-10-19
Hi, there

Can somebody help me to install OpenGL and Glut?

I am new to ubuntu, or can you direct me to some helpful source?

Thank you.
yasir.

---

