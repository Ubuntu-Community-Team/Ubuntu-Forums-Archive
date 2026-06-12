---
title: "How to write one's own GUI toolkit like QT or GTK?"
date: 2009-10-24
forum: Programming Talk
---

### Post by csstudent on 2009-10-24
I tried searching on the internet but all results simply talk
about using one of the kits not making one's own.Please give a certain direction as to what to study to do the above

---

### Post by diesch on 2009-10-24
[XLib](http://en.wikipedia.org/wiki/Xlib) provides the low level functions you need to draw your widgets, iplement event handling and such.

See the source code of Gtk, Qt, FLTK, ... for some ideas.

---

### Post by froggyswamp on 2009-10-24
It does sound tempting to create your own tk but it turns out its such a huge pile of learning and work that in the middle one realizes it's better to contribute to the existing project(s) rather than creating from scratch. Better sameness isn't gonna live long. Unless there's something in between.

---

### Post by mmix on 2009-10-24
See sources like,

GTK/QT/Xorg, directfb, SDL, kernel frame buffer driver, Haiku GUI

---

