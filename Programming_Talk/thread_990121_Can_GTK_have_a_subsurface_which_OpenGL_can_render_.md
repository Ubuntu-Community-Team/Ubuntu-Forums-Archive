---
title: "Can GTK have a subsurface which OpenGL can render on?"
date: 2008-11-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-22
Can GTK have a subsurface which OpenGL can render on?

If not, what GUI toolkit can do that?

---

### Post by kknd on 2008-11-22
Yes! Look at GtkGLExt (other project, that enables OpenGL draw on any GTK widget)

---

### Post by crazyfuturamanoob on 2008-11-22
> **kknd said:**
> Yes! Look at GtkGLExt (other project, that enables OpenGL draw on any GTK widget)

If so, can GTK also capture mouse & keyboard presses, and give the coordinates?

And does it work in PyGTK?

---

### Post by nvteighen on 2008-11-22
PyGTK = GTK+ :) So, if X works in GTK+, X works in PyGTK...

---

### Post by skullmunky on 2008-11-22
Yes, you can use the mouse coordinates in your gtkglext widget.  lemme know if you get stumped, I have some basic code that does a trackball viewer in a gtkglext widget.

You can also do this with Qt 4 (and PyQt 4); [QGLWidget]("http://doc.trolltech.com/4.4/qglwidget.html") is a standard widget.  

Or if you want to go the other way around, making a GUI inside your GL inside of GL in your GUI, you can use [Crazy Eddie's GUI System]("http://www.cegui.org.uk/wiki/index.php/Main_Page")

---

