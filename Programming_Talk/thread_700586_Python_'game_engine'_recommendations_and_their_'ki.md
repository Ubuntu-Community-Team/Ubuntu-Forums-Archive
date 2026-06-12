---
title: "Python 'game engine' recommendations and their 'killer games'?"
date: 2008-02-18
forum: Programming Talk
---

### Post by maximilion on 2008-02-18
Just installed SPE, looking at PyGame screenshots wasn't awe-inspiring... :P

My needs: interface to API or similar that gives me frame buffer and fast functions to blit (with opacity), read mice/keyboards/joysticks, and mix sound effects and music.

Optionally to reasonably modern 3D (specular, bump, optionally pixel shaders, HDR).

I haven't ogled all the stuff available for Python yet, so feel free to educate me if SPE already interfaces to OpenGL/AL - I wouldn't mind OpenGL at all!

---

### Post by pmasiar on 2008-02-18
Pygame was used for [Galcon](http://www.imitationpickles.org/galcon/index.html) IIRC.

---

### Post by slavik on 2008-02-18
if you don't mind OGL at all, take a look at SDL. :)

---

### Post by Wybiral on 2008-02-18
> **slavik said:**
> if you don't mind OGL at all, take a look at SDL. :)

PyGame is a thing wrapper for SDL and some of its sister libraries (it's WAY friendlier). And yes, PyGame can be used to create an OpenGL context too (in fact, that's one of its more common uses).

As far as full-fledged engines go, there's PySoy, Soya3d, Pyrr, PyOGRE... Probably more...

---

### Post by slavik on 2008-02-18
there is also Torque, afaik the only game engine commercially designed to be that ...

---

