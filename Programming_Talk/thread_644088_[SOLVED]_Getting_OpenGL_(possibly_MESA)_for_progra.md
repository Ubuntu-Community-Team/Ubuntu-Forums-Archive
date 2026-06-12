---
title: "[SOLVED] Getting OpenGL (possibly MESA) for programming"
date: 2007-12-18
forum: Programming Talk
---

### Post by Fixman on 2007-12-18
What should I download for using OpenGL on Ubuntu? Once I downloaded it, to what libraries should I link?

EDIT: found everything with a little google. I must get used to not ask here for everything

---

### Post by LaRoza on 2007-12-18
Search is Synaptic, it looks like "libglu1-mesa-dev" is what you need. 

I never used it, so I don't know.

---

### Post by Fixman on 2007-12-18
> **LaRoza said:**
> Search is Synaptic, it looks like "libglu1-mesa-dev" is what you need. 

I never used it, so I don't know.

To what libraries must I link for using it?

---

### Post by DougB1958 on 2007-12-18
> **Fixman said:**
> To what libraries must I link for using it?
These work for me:
```
-lglut -lGLU -lGL -lX11
```
(Those are options used with command-line GCC when linking an OpenGL/GLUT program for Ubuntu; adapt the syntax as needed for your development environment.)

---

