---
title: "OpenGL programming, missing GLUT"
date: 2007-12-23
forum: Programming Talk
---

### Post by witmann on 2007-12-23
Hello,

I have a problem with compiling programs written in C/C++ with openGL. I'm trying to link GLUT to gcc with -lglut command, but the compiler seems not to recognize the glut library installed on my system. I tried to download libglu1-mesa-dev with Synaptic. However it says, that this library needs libglu1-mesa (=6.5.2-3ubuntu7) and download stops, because i have 6.5.2-3ubuntu8 installed. What can I do with this problem?

---

### Post by revanthedarth on 2007-12-23
Package Manager has libglut3 and glutg3-dev. Those should be sufficent for lglut. If not, install freeglut3-dev.

libglu1-mesa-dev lets you use -lGLU, but you want -lglut.

---

### Post by witmann on 2007-12-23
Ok, i've forced Synaptic to change the version of libglu1-mesa to 6.5.2-3ubuntu7 and installed missing packets + new nvidia drivers. Everything works just fine.

---

