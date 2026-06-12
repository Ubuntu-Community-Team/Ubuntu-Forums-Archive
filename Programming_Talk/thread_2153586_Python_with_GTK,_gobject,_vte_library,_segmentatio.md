---
title: "Python with GTK, gobject, vte library, segmentation error"
date: 2013-06-11
forum: Programming Talk
---

### Post by JonnyPython on 2013-06-11
Hey guys,
I want to write a python gtk(not PyGtk) application with an emulated terminal in a window. I found the vte gtk bindings for python. In the python interactiv mode I can import everything and instantiate everything without problems, like:
import gtk
import vte
import gobject

vte = vte.Terminal()

Works !

But when I run this program:

[http://coding.debuntu.org/python-embedding-virtual-terminal-gtk-widget-python-vte-library](http://coding.debuntu.org/python-embedding-virtual-terminal-gtk-widget-python-vte-library)

I get as the only error "Segmentatio fault", nothing else. And added to that, I'm very confused if I should use import Gtk or gtk or gobject(that's somehow related) something like resportoris blabla(sry can't really remember). And which of that works with vte and all that that.

I hope somebody can help me, I'm really motivated with that, but I'm also kind of sick of googleing all the time, and I didn't find much about it.
(python 2.7)

Greets

---

