---
title: "Compiling OpenGL"
date: 2006-01-28
forum: Packaging and Compiling Programs
---

### Post by hafunui on 2006-01-28
I've been trying to learn OpenGL with c++ but I couldn't get it to compile in windows. Now that im in linux, what would i need to compile OpenGL with c++?

And how would I compile?

---

### Post by bartbes on 2006-01-28
In linux and windows you have different headers (ofcourse) and I think you should check for what the source is made, and if you are making it yourself I would start with GLUT (was the 1st I started with). OpenGL is usually already available GLUT isn't and maybe you need some headers that you don't have.. check it

---

### Post by hafunui on 2006-01-31
Well, I've never actually compiled anything before. But im guessing I need a C++ compiler?

What one do you suggest, and how do I compile with it?


Thanks

---

### Post by InvaderSteve on 2006-04-11
try installing this:

sudo apt-get install build-essential freeglut3-dev

or install these packages from synaptic.

build-essential will install the things you need to compile c++ and use makefiles

freeglut3-dev will give you the libraries you need to make opengl programs

---

### Post by wangkeit on 2010-08-01
have installed the libraries needed by OpenGL, but I do not know how to compile programs that I have made..??

---

### Post by cyrion on 2010-08-02
gcc yourfile.cpp -lglut -lGLU -o appname

---

