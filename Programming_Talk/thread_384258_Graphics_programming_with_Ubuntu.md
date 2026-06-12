---
title: "Graphics programming with Ubuntu"
date: 2007-03-14
forum: Programming Talk
---

### Post by stolu on 2007-03-14
Hi,

I am a newbie at Linux graphics programming and I would like to know which graphics library Ubuntu uses? Also, where to find the header files and documentation etc.

Thanks
stolu

---

### Post by hod139 on 2007-03-14
A good place to start is OpenGL.  In Linux, the OpenGL API is implemented by mesa, so you need to install: libgl1-mesa-dev and libglu1-mesa-dev (glu is a set of commonly used extensions).  You will also probably want to display the graphics, so you need a windowing toolkit.  The easiest and most lightweight is GLUT.  You can install it by installing the package freeglut3-dev. A more feature rich toolkit is the Simple DirectMedia Layer (SDL).  This is a more complex library than GLUT, but offers more.  You can install it with the package libsdl1.2-dev.  For some tutorials using both glut and sdl, check out [http://nehe.gamedev.net/](http://nehe.gamedev.net/).

Edit:  To make more clear what to install:  
To install OpenGL (and GLU extensions)
```

sudo aptitude install libgl1-mesa-dev libglu1-mesa-dev

```For GLUT
```

sudo aptitude install freeglut3-dev

```For SDL
```

sudo aptitude install libsdl1.2-dev

```

---

### Post by lnostdal on 2007-03-14
For 2D work cairo is very good: [http://cairographics.org/](http://cairographics.org/)

I link to a short example that show how to use Cairo and GTK+ on the page mentioned in my signature. 

Before trying to compile the example do:
```

sudo aptitude install libcairo2-dev libgtk2.0-dev

```

---

### Post by Poisson_Pilote on 2007-03-14
Ubuntu itself uses various graphic libraries for different purposes. On Gnome, windows, widgets, etc use GTK+, while KDE uses QT. For 2D graphics, there is a large choice (SDL, Cairo, Allegro,...). For 3D Graphics, the main library is OpenGL.

Then, you have various implementations of those library: for example, if you want to program 3D applications, you can use Soya if you code in Python, Ogre for C++, etc.

The graphic library to use is relevant to what you want to do.

---

### Post by stolu on 2007-03-14
Thanks for the help

---

### Post by ghandi69_ on 2007-03-14
Can you use qt for anything in gnome??

---

### Post by lnostdal on 2007-03-14
Yes, QT applications will run in a Gnome desktop also. K3B and Amarok comes to mind.

---

### Post by squirrelix on 2007-05-14
Hey, thanks hod139, that was exactly the info I was looking for! Now I can run those tutorials from nehe! Woo! Off to OpenGL land!
-- Squirrel

---

### Post by moma on 2007-05-15
What you need is Code::Blocks IDE.  
It has templates for wxWidgets 2.6 and 2.8, GTK2 and OpenGL programming + many more.

See: [http://ubuntuforums.org/showthread.php?p=1962696#post1962696](http://ubuntuforums.org/showthread.php?p=1962696#post1962696)

---

### Post by nvacas on 2007-05-15
do you know this site? enjoy.
[http://www.linux3dgraphicsprogramming.org/](http://www.linux3dgraphicsprogramming.org/)

---

### Post by TKC747 on 2009-05-18
Never mind, I got the answer in another thread
sorry

---

