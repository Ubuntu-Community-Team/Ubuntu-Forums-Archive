---
title: "compile OpenGL c++"
date: 2014-11-18
forum: Packaging and Compiling Programs
---

### Post by roma.5 on 2014-11-18
Hello!
I attend a computergraphic class and have to some programming in OpenGL in c++. I tried to run my programm 
with: g++  -Wall myProg.cpp -o runme -lglut -lGLU  -lGLEW 
(this is the way we compile it in class, and there it works)
on my home pc (System: ubuntu) but the compiler gives me two errors:
/usr/bin/ld: /tmp/ccJmqaFS.o: undefined reference to symbol 'glClear'
and
//usr/lib/nvidia-331/libGL.so.1: error adding symbols: DSO missing from command line
I have searched for the errors in google quiete long, but without sucess, so I hope somebody has a hint for me.
(Glut und Glew is installed, direct rendering is working, glxgears also does what it should, i.e. shows the gears, rotating in different colors)
Thanks!
Roman

---

### Post by stelarcf on 2014-11-25
(Sorry for replying a week late)

I think you need to link -lGL too.

---

### Post by roma.5 on 2014-11-26
Hey,

yes you are right, this was exactly the solution to my problem!
Thank you ;-)

---

