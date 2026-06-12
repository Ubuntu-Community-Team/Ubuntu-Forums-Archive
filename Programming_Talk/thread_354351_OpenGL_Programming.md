---
title: "OpenGL Programming"
date: 2007-02-05
forum: Programming Talk
---

### Post by molex on 2007-02-05
I recently purchased the "Redbook" from my local book store, and downloaded the accompanying code from opengl-redbook.com . I opened the code using Anjuta but received linking errors. Is there a tutorial on the web that can help me create a project that links correctly when compiling? 

I am fairly new to C++ in Linux (I use Java for AP CompSci at school) although I am able to program fine using the C++ standard libraries (Thus I have never used linking before). 

What steps should I take to get OGL and GLUT working?
What packages should I download?
How can I create a Project that compiles these correctly, and w/o needing to compile from command line (Rather compiling and executing within the IDE)?
Are there any good tutorials for coding and compiling OGL+GLUT in Ubuntu.
Has anyone compiled a binary of Dev-C++ to Ubuntu, I like that app?


I'm pretty excited to learn OpenGL, I have been stuck using primarily Java2D for my gaming, and my school amigos told me OpenGL was the next step I should take. :)

---

### Post by Wybiral on 2007-02-05
Well... Assuming all of the GL/GLUT code is correct, and that you have the freeGLUT and MesaGL development files (you can get them from synaptic...

I know you don't want to use the command line, but I'm not much of an IDE user (although you should be able to use these flags in the IDE anyway...)

"g++ myprogram.cpp -lglut -lGLU -lGL"

That will do it for you.

---

### Post by molex on 2007-02-05
Will G++ compile C as well?

---

### Post by Wybiral on 2007-02-05
If it's C, then use "gcc program.c -lglut -lGLU -lGL"

---

### Post by madsravn on 2007-02-21
I don't know if you've already figured it out by trying, but g++ will also compile most C.

---

