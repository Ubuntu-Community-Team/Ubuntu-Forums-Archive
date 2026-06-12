---
title: "Python Application (kind of like a screensaver)"
date: 2007-03-17
forum: Programming Talk
---

### Post by saracen on 2007-03-17
I'm looking to create an application in Python that's kind of like a simple screensaver.  All it really has to do is be able to display in fullscreen mode some blobs of moving text and some colorful animations.  What libraries should I be looking to use in order to do this?

---

### Post by WW on 2007-03-17
You can do this with **pygame**.  Here is a cool example: [http://theory.lcs.mit.edu/~rivest/mst.py](http://theory.lcs.mit.edu/~rivest/mst.py)

---

### Post by pmasiar on 2007-03-17
[http://en.wikipedia.org/wiki/Pygame](http://en.wikipedia.org/wiki/Pygame) might be good start. Simplified GUI, and has vibrant community and plenty of tutorials. Disclaimer - I never used it - it is outside of my interests :-(

edit: WW beat me by 1 minute :-)

---

### Post by Wybiral on 2007-03-17
I'd suggest  pyOpenGL and GLUT.

GLUT is pretty simple to setup OpenGL with, and you're find more GLUT/OpenGL tutorials then PyGame (not always in Python, but they will still help). You can get it from the repositories.

Also, a small module I was working on that makes SDL and OpenGL easier in python is viper: [http://p13.wikispaces.com/viper](http://p13.wikispaces.com/viper)

I've also ported a number of NeHe OpenGL tutorials to work with viper, it's incredibly easy to use.

---

### Post by saracen on 2007-03-18
Thanks for the tips guys.  I will check them out.

---

### Post by 23meg on 2007-03-18
Check out [Clutter]("http://clutter-project.org/") as well; looks promising.

---

