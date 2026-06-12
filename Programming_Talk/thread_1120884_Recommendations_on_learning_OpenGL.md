---
title: "Recommendations on learning OpenGL?"
date: 2009-04-09
forum: Programming Talk
---

### Post by TheBuzzSaw on 2009-04-09
I am committed to learning OpenGL. I believe in creating cross-platform software (games especially ^_^). I'm actually using/learning SDL for a 2D game right now.

How did you start learning OpenGL? What steps did you have to go through before you were comfortable with it? Just to give you some background, I am 25 years old and a 5th-year computer science major. I am good with numbers (5 out of 5 on my AP calc test in high school). I understand physics better than the average Joe (took AP physics), but I am by no means amazing at it (didn't even take the AP test afterwards). I understand some fundamentals of 3D theory, but I would have to learn a lot more before I could fully understand OpenGL.

I am completely comfortable working in C++. I have used it for almost a decade. :)

The library here has the OpenGL Superbible 4th edition. It looks really good; I just need to find the time to read it. XD

Recommendations? Good starting places? Solid tutorials?

---

### Post by soltanis on 2009-04-09
NeHe:

[http://nehe.gamedev.net/](http://nehe.gamedev.net/)

---

### Post by TheBuzzSaw on 2009-04-09
I should PayPal you a dollar. :P

Thanx!

(I'm still open to other feedback too. I won't ignore this thread, people!)

---

### Post by Nichy on 2009-04-09
Having a problem compiling code from those sites, what libraries should I have?

- Nichy

---

### Post by soltanis on 2009-04-09
First of all, a lot of that site has Visual C++ code. Wherever they use Windows code, you have to convert it to the linux equivalent.

You need the opengl headers and development libraries, and possibly glu/glut as well.

sudo apt-get install libglu1-mesa-dev libglut3-dev

---

### Post by tneva82 on 2009-04-10
> **soltanis said:**
> First of all, a lot of that site has Visual C++ code. Wherever they use Windows code, you have to convert it to the linux equivalent.

You need the opengl headers and development libraries, and possibly glu/glut as well.

sudo apt-get install libglu1-mesa-dev libglut3-dev

Atleast in tutorials most if not all(haven't checked all the more advanced ones) have linux/SDL packages as well.

---

### Post by moma on 2009-04-10
Hello,

Read also this thread:
[http://ubuntuforums.org/showthread.php?p=6972270#post6972270](http://ubuntuforums.org/showthread.php?p=6972270#post6972270)
-------

ps. Take a look at the demo-videos of gscereendump 0.2.
[http://code.google.com/p/gscreendump/downloads/list](http://code.google.com/p/gscreendump/downloads/list)
(screencast-[1-3].avi)
Gscreendump 0.3 which is now planned will be even better ;-)

---

### Post by hessiess on 2009-04-10
Seaing as you are already learning SDL, you can use that to set up OpenGL windows and get keybord/mouse input.

---

