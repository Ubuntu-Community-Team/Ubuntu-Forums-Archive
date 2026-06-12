---
title: "How do I compile a .c file that uses glm.h? [&quot;undefined references&quot;]"
date: 2013-05-17
forum: Programming Talk
---

### Post by rehcarlos on 2013-05-17
Hello guys,

I'm writing a simple code (using **gedit** on **Ubuntu**) in **C** to import a 3d model (**.obj**).

In my code I'm using the library "**glm.h**" and I'm using the following commands:

GLMmodel* f16;
f16 = (GLMmodel*)malloc(sizeof(GLMmodel));
f16 = glmReadOBJ("./objs/f16.obj");

in order to compile, I'm using the following line:
gcc -Wall test.c -o test -lglut

but terminal prints the following errors:

"**undefined reference** to glmDraw
undefined reference to glmReadObj"

What can I do to compile my code correctly?

---

