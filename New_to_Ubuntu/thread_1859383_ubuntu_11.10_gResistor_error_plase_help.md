---
title: "ubuntu 11.10 gResistor error plase help"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by qpens on 2011-10-13
(gresistor:3215): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gresistor:3215): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gresistor:3215): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gresistor:3215): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/local/bin/gresistor", line 17, in <module>
    from SimpleGladeApp import SimpleGladeApp
  File "/usr/local/lib/python2.7/dist-packages/SimpleGladeApp.py", line 28, in <module>
    import gtk.glade
ImportError: No module named glade


How to fix this problem?

---

### Post by vajorie on 2011-10-14
I think it wants you to install libglade2-0 from the repos...

---

### Post by qpens on 2011-10-20
didn't help

---

### Post by qpens on 2011-10-22
glade-gtk2 fix the problem

---

