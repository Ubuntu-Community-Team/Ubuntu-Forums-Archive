---
title: "Need help getting OpenGL to work!"
date: 2006-12-19
forum: Programming Talk
---

### Post by mozza314 on 2006-12-19
I want to learn OpenGL and am trying to get it to work on my computer (through C/C++) but can't get it off the ground. I'm using Ubuntu 6.06.

What packages do I need to install?
What are some good tutorials?
What would a really basic sample program look like?
And what would I do to compile it?

Thanks

---

### Post by Wybiral on 2006-12-19
There are a couple of OpenGL tutorial here: [http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

Basically, you need MesaGL installed for linux. You will probably want a way to initialize an OpenGL enabled window, SDL is a god option with a lot of good tools, GLUT (for linux it's freeGLUT) is another good option but is a little more restrictive because it is very event driven (you give it the functions to call, and it calls them for you, you don't control the program flow after you hand it to GLUT).

And, if you feel like playing around with OpenGL in python, grab pyOpenGL and my new module [Viper]("http://p13.wikispaces.com/viper"). There's also pyGame and GLUT (even a pySDL) for python... But Viper's better ;)


EDIT:

Compiling...

When you use OpenGL with SDL it usually looks like this from the command line:
g++ program.cpp -lSDL -lGLU -lGL

And with GLUT it looks like this...
g++ program.cpp -lglut -lGLU -lGL

To include a library, usually you just add "-l" and then the library name.

---

