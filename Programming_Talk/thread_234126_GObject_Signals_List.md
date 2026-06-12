---
title: "GObject Signals List"
date: 2006-08-11
forum: Programming Talk
---

### Post by jeff_ on 2006-08-11
I'm looking for a list of the strings like 'window_opened' or 'write' that can be used as signals for GObject. For example the signals used in g_signal_connect().

---

### Post by kostkon on 2006-08-11
You mean you want to know all the signals that you can use because all the widget objects inherit from the GObject. 

GObject has only one signal but the widgets that inherit from it have many signals attached to themselves.

I think this [part]("http://gtk.org/tutorial/a2700.html") from the GTK tutorial from [gtk.org]("http://www.gtk.org/") may help you.

EDIT: forgot to put the link.

---

### Post by asimon on 2006-08-11
And in the [GTK+ Reference Manual](http://developer.gnome.org/doc/API/2.0/gtk/index.html) you can find the signals of some specific widget in the 'signals box'. Here the example for [GtkLabel](http://developer.gnome.org/doc/API/2.0/gtk/GtkLabel.html#id3033222).

---

### Post by jeff_ on 2006-08-11
Thanks guys, but I guess what I was actually looking for was a list of signals that could be used with wnck. I eventually found them in a .c file here [http://cvs.gnome.org/viewcvs/libwnck/libwnck/test-wnck.c?rev=1.13](http://cvs.gnome.org/viewcvs/libwnck/libwnck/test-wnck.c?rev=1.13)

As far as I can tell this is the only place to find a list of signals that can be used with wnck.

---

