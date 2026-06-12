---
title: "What's this GTK widget?"
date: 2010-03-31
forum: Programming Talk
---

### Post by blazemore on 2010-03-31
How can I use this in Python GTK (Newb question I know, but I can't find any decent description of all the GTK widgets)

---

### Post by cdekter on 2010-03-31
This is a gtk.Frame object. It has a label (which is the part that you've highlighted in the image) and contains one or more child controls. Back in the day the Frame would display a visible frame/box around its child controls, but the new Gnome HIG recommends not having the frame visible, hence why you don't see it any more.

[http://library.gnome.org/devel/pygtk/stable/class-gtkframe.html](http://library.gnome.org/devel/pygtk/stable/class-gtkframe.html)

---

### Post by blazemore on 2010-03-31
> **cdekter said:**
> This is a gtk.Frame object. It has a label (which is the part that you've highlighted in the image) and contains one or more child controls. Back in the day the Frame would display a visible frame/box around its child controls, but the new Gnome HIG recommends not having the frame visible, hence why you don't see it any more.

[http://library.gnome.org/devel/pygtk/stable/class-gtkframe.html](http://library.gnome.org/devel/pygtk/stable/class-gtkframe.html)

Thanks. I thought it might have been a formatted label and it was.
I made one using pango.
I thought there might have been a dedicated Title object or something.

---

