---
title: "OpenGL preformance question"
date: 2009-02-21
forum: Programming Talk
---

### Post by Ferrat on 2009-02-21
Well I'm started adding OpenGL to my game engine and I want an easy init of it and create a simple window containing OpenGL, I don't need any menus etc like with QT or GTK give etc but don't care what I really use but there doesn't seem to be a consensus on what to use.
GLUT seems easiest just for a simple window since the rest is to be done with OpenGL but I've heard that GLUT has some performance issues compared to the other ways? 

If anyone could point me in the right direction on what to use this would be great, simple to create and not performance hindering, first OpenGL implementation I do and been looking around but can't seem to find anything other than flame wars or contradictions.

EDIT:
Also don't want to use SDL.

---

### Post by Vadi on 2009-02-21
[http://clutter-project.org/](http://clutter-project.org/) ?

---

### Post by Ferrat on 2009-02-21
Thanks but that more or less looks like a finished engine, not just for creating a window?

---

### Post by Vadi on 2009-02-21
Ah sorry, thought you wanted windows inside the opengl thing.

I know that Savage 2 uses "pure xlib+glx", bypassing the SDL issues with making fullscreen apps.

---

### Post by Gordon Bennett on 2009-02-21
Use Glut and (for cross-compatible sound and more later on) SDL.

Glut is an app-level wrapper to OpenGL - performance is very good - some of the high-level functions such as generating 3D models consume time, but that is the same if you wrote that code yourself :)

For an efficient engine, use OpenGL display lists and shared texture objects to start with.

Edit - p.s.  I released a simple example (public domain) to use OpenGL with GTK: [http://mil-tdd-41p.net/?p=39](http://mil-tdd-41p.net/?p=39)

---

### Post by Vadi on 2009-02-21
Be warned though that making an opengl app that goes fullscreen and is able to alt+tab is impossible in SDL. It's why 99% of Linux games lack this basic ability.

---

### Post by Ferrat on 2009-02-21
As stated in the first post, won't use SDL but seems that GLUT or Savage solution is the way to go, thx =)

---

