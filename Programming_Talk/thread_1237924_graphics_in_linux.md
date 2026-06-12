---
title: "graphics in linux"
date: 2009-08-11
forum: Programming Talk
---

### Post by nipunreddevil on 2009-08-11
What is used in linux analogous to graphics in turbo c++.
What all libraries are generally used?

---

### Post by nipunreddevil on 2009-08-11
What all programming languages are used for graphical programming.i have learnt c/c++/java/python

---

### Post by pepperphd on 2009-08-11
I think OpenGL has bindings for all of those languages.

---

### Post by slavik on 2009-08-12
but in some languages OpenGL is faster than in others and JOGL (Java OpenGL) is not complete afaik.

Are you looking for something like ncurses? or full 2D/3D (OpenGL)?

---

### Post by nipunreddevil on 2009-08-12
need something for homework assignment on computer graphics,where we are supposed to design a game.

---

### Post by nipunreddevil on 2009-08-12
Also something fro learning basic algorithms like dda.teacher recommended using tc,but i intend to work iwth open source equivalents.

---

### Post by slavik on 2009-08-12
> **nipunreddevil said:**
> need something for homework assignment on computer graphics,where we are supposed to design a game.
OpenGL.

---

### Post by nipunreddevil on 2009-08-12
OpenGL with gcc? or any other compiler?
Any good tutorials to get started.

---

### Post by slavik on 2009-08-12
look up nehe tutorials, you can use gcc, you will need to install mesa libraries for OpenGL stuff. (mesa is the Linux OpenGL implementation).

---

### Post by nipunreddevil on 2009-08-12
> **slavik said:**
> look up nehe tutorials, you can use gcc, you will need to install mesa libraries for OpenGL stuff. (mesa is the Linux OpenGL implementation).

Thanks a lot.

---

### Post by slavik on 2009-08-12
by the way, do you really need full graphics or will something like ncurses suffice?

---

### Post by phrostbyte on 2009-08-12
Might want to look at Ogre3D too.

---

### Post by nipunreddevil on 2009-08-12
Have no idea about ncurse .just started with graphics.When is it used?

---

### Post by nipunreddevil on 2009-08-12
Had a look at google images for openGL and Ogre3d,both look awesome.
What about doing some basic graphics algos like drawing lines using setpixel etc.What would be recommended/

---

### Post by phrostbyte on 2009-08-12
For 2D games:

[http://alleg.sourceforge.net/](http://alleg.sourceforge.net/)
[http://www.libsdl.org/](http://www.libsdl.org/)

These will give you **much more** then setting pixels or drawing lines. But then again, even something low level like Xlib will give you more then that. :)

---

### Post by Sockerdrickan on 2009-08-12
yes as said use SDL for 2d graphics if you are noob

---

### Post by nipunreddevil on 2009-08-12
What about pyGame?

---

### Post by glaze on 2009-08-12
> **nipunreddevil said:**
> What about pyGame?

Pygame is used with Python programming language.

---

### Post by nipunreddevil on 2009-08-12
Ya i know that,i was querying how often is pyGame used.And can we use any language to code using OpenGl?

---

