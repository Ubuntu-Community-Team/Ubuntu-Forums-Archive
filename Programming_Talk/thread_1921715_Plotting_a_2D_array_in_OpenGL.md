---
title: "Plotting a 2D array in OpenGL"
date: 2012-02-07
forum: Programming Talk
---

### Post by rocky7 on 2012-02-07
Hi all;

Nowadays, I started to learn OpenGL. I have a question. Now, I wanna do a program. This program will mainly plot a 2D array (array1) and then fill it with colors. I have a 2D array (array2) before plotting the array1. array1 will be filled with colors according to datas which in array2. I am new to OpenGL. Therefore, i am not sure even if this program can be done with OpenGL. I am also studying and searching lots of stuff about OpenGL. I will be glad to hear some advice, if you have about what should i do first? By the way, I am using C++. Thanks.

---

### Post by xytron on 2012-02-09
> **rocky7 said:**
> Hi all;

Nowadays, I started to learn OpenGL. I have a question. Now, I wanna do a program. This program will mainly plot a 2D array (array1) and then fill it with colors. I have a 2D array (array2) before plotting the array1. array1 will be filled with colors according to datas which in array2. I am new to OpenGL. Therefore, i am not sure even if this program can be done with OpenGL. I am also studying and searching lots of stuff about OpenGL. I will be glad to hear some advice, if you have about what should i do first? By the way, I am using C++. Thanks.

Your post is a bit unclear as to what exactly you are attempting to accomplish.

You can plot a curve with OpenGL.  You could have your data in a 2D array.

See the following link for more information about graphing a curve with OpenGL.

[http://en.wikibooks.org/wiki/OpenGL_Programming/Scientific_OpenGL_Tutorial_01]("http://en.wikibooks.org/wiki/OpenGL_Programming/Scientific_OpenGL_Tutorial_01")


They use GLUT to create the OpenGL window.  That's not a good idea.  If you are using Linux you can just create the OpenGL window with GLX, if you later need a full GUI then using one of the GUI toolkits is best such as GTK+, QT, wxWidgets, FLTK, they all let you create an OpenGL window to draw into.

---

