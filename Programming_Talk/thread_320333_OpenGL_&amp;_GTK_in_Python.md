---
title: "OpenGL &amp; GTK in Python"
date: 2006-12-17
forum: Programming Talk
---

### Post by tpg on 2006-12-17
I am currently learning python, and I wanted to port a program I wrote a while ago in Delphi (on Windows!). In Delphi, I was able to have a window with normal controls on it, and within it a frame into which OpenGL could draw. Can I do a similar thing with python and GTK?

I have tried installing pygtkglext (1.1.0), however after installing, python does not find the gtkgl module. Does anyone know how to get pygtkglext working, or have any other ideas? Thanks in advance.

---

### Post by Wybiral on 2006-12-17
I've looked for a gtk opengl module myself and haven't had much luck. I have been able to use GLUT and pyOpenGL which works very nicely. Unfortunately it has a very event driven approach to it (you have to register a loop function that it takes over and calls). I would be interested in a plain gtk one myself. But, if you have to GLUT will work for most applications. I can post up some basecode if you'd like, to make sure you have GLUT installed and everything.

---

### Post by tpg on 2006-12-17
If you use pyOpenGL and GLUT, can you still have a GTK form with controls on it? I think both require some sort of message handling loop, so is it possible to have two such loops working together in the same program?

After installing pygtkglext, I've had a look around in my python site-packages folder, and found that the required gtkgl module is actually installed, only python doesn't seem to know its there! Is there some sort of script I need to run before python will detect it?

---

### Post by Wybiral on 2006-12-17
Python SHOULD detect it. Maybe try executing a python script in the same directory as the ".so" and see if it will work that way.

btw, GLUT has it's own event handling routines for key/mouse

Also, I think TKinter might even have an opengl extension...

---

### Post by tpg on 2006-12-17
No, it doesn't detect it, even when I copy one of the example files to the directory containing _gtkgl.so.

I've found the OpenGL.Tk module, altough I can't find any examples of how to use it!

---

