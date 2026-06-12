---
title: "OpenGL and Glut libraries"
date: 2006-11-09
forum: Programming Talk
---

### Post by snl on 2006-11-09
I need to compile a program which requires OpenGL and Glut libraries. I tried searching for glut, mesa, opengl, and it came up with several packages. Which package will I need to install?

Thank you.

---

### Post by motang on 2006-11-09
Good question I haven't done it myself yet but I shall try to take a shot at it.  First you need to the files (.h and .cpp I am assuming that it's a C++ program).  Now easy way to do it have a folder with the gult libraries and call for in your makefile.

OR

You can add the location of the files in .bash_profile I think it goes something like > PATH=location/of/your/files/ this should work unless if I have it wrong considering I haven't done this in 4 years.  I am going to try it out when I get home and I shall update you on it if it works out for me.

---

### Post by bukwirm on 2006-11-09
mesa-common-dev **libgl1-mesa-dev** **libglu1-mesa-dev** freeglut3-dev **libglut3-dev**

Those are the ones I appear to have installed - you may not need them all - try the ones in bold first and see if the rest install as dependancies.

---

### Post by slavik on 2006-11-09
when installing libfreeglut3-dev, it will install needed things as dependencies.

then you just link your program to glut via -lglut (it will link for OpenGL, GLU and GLUT)

---

### Post by mozza314 on 2006-11-18
Hi, I am also trying to compile in OpenGL. I have compiled simple C++ programs before just using:
g++ <file>

But I don't know how to compile a C++ OpenGL program. Can you please give me an explanation and an example which will compile a C++ OpenGL program? I'm pretty sure I have all the required libraries after looking into this a few days ago, but I couldn't manage to compile anything. I've been told I need to set some options at the command line.

Also, any good resources for learning OpenGL through C++?

Please shed some light on this for me.

---

### Post by fct on 2006-11-19
Compiling C++ files using glut is as simple as this:

$ g++ -lglut file.cpp

As for resources for learning glut with C++, the same ones for glut with C will serve.

Here is a nice introduction:

[http://mindfuck.de-brauwer.be/articles/glut/](http://mindfuck.de-brauwer.be/articles/glut/)

---

### Post by amo-ej1 on 2006-11-20
hey i wrote that page :D

---

### Post by fct on 2006-11-20
It was quite useful to me back in the CG course. :-D

---

### Post by galileon on 2006-11-20
cheers for the link, im looking into gl programming, and couldn't get anything to produce better than a blank window - the teapot appeared from the link, so its gonna work now...yay!

---

### Post by coder_ on 2006-11-20
I've been wanting to get back into 3D graphics programming (after quitting it for GUI application development in Linux), and that looks like a nice tutorial, amo-ej1.  :)

Do you think it is worth it doing raw OpenGL over a 3D engine like Irrlicht?  I'm not sure whether I want to use a prebuilt engine or not...

---

### Post by amo-ej1 on 2006-11-21
It depends, i've played with irrlicht some time ago and i found it really amazing how fast you could get results there... i believe the first tutorial was a quake model while their second tutorial already had you running with a quake 3 map with minimal lines of code.

I you want to play with low level things, it's better to tamper with opengl itself, if you want eyecandy fast it's better to play around with some high level engine.

Anyhow i'm not an expert myself, i simply like to play around with things it's only a shame that with such an availability of tools linux is still doing extremely bad (my honest opinion) in the games world.

---

