---
title: "Python - widgets"
date: 2008-08-11
forum: Programming Talk
---

### Post by aktiwers on 2008-08-11
Hi

How do you create Python GUI apps that does not have the window border?

I want to write a small widget(or conky like app) and cant seam to find how to do this anywhere..  does anyone have any links on this?

Would be great!

---

### Post by shifty2 on 2008-08-11
There is a gtk setting for this: [http://library.gnome.org/devel/pygtk/2.12/class-gtkwindow.html](http://library.gnome.org/devel/pygtk/2.12/class-gtkwindow.html)

> gtk.Window.set_decorated

    def set_decorated(setting)

setting :
	if True decorate the window

The set_decorated() method sets the decorated flag to the value specified by setting. If setting is True the window will be decorated. By default, windows are decorated with a title bar, resize controls, etc. Some window managers allow PyGTK to disable these decorations, creating a borderless window. If you set the decorated property to False using this method, PyGTK will do its best to convince the window manager not to decorate the window. On Windows, this method always works, since there's no window manager policy involved.

---

### Post by aktiwers on 2008-08-11
Thanks! What about with Tkinter?

---

### Post by stevescripts on 2008-08-11
hmm ...

AFAIK - the closest you can come with Tkinter is a transient toplevel, see [http://www.bembry.org/technology/python/notes/tkinter_5.php]("http://www.bembry.org/technology/python/notes/tkinter_5.php")
for an example.

Somebody with lots of tkinter experience jump in here and correct me if I am wrong  (I just tinker with python and tkinter, so far ...)

You can also set the title blank if you wish

Hope this is a bit helpful

Steve

---

