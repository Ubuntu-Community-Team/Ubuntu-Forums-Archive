---
title: "Pygtk, pyclutter, pyqt, pyside..."
date: 2010-03-18
forum: Programming Talk
---

### Post by michaelmartin007 on 2010-03-18
Hi,

Let me explain a moment, with Qt you can develop an application
using pyqt or pyside. This is clear. They are two different projects targeted to qt.
At the beginning there was pygtk. Now there are pygobject, python-clutter, python-clutter-gtk, pygi, 
python bindings for gobject introspection...

I see all of this in this way:

pygtk (python using gtk+ widgets tool kit)
python-clutter (python using clutter widgets tool kit)


Now
Because is this so? "Clutter-Gtk is a library which allows the embedding of a Clutter canvas" (python-clutter-gtk)

Because is not posible coding in python-clutter without gtk+?
It is not posible to deprecate pygtk in favour of python-clutter?

I rode about this kind of thing but I am a little confuse. If you see to pyqt or pyside are clear the libraries. With python gnome it seem to me as if different technologies should mix and maybe should be giving differents answers. I don't know if all of this libraries have cohesion.

Finally, I use Ubuntu. This is not at all a qt vs gtk+. No in any way. It is a question about the gnome technologies targeting python.

Thanks.

---

### Post by nvteighen on 2010-03-18
> **michaelmartin007 said:**
> Hi,

Let me explain a moment, with Qt you can develop an application
using pyqt or pyside. This is clear. They are two different projects targeted to qt.
At the beginning there was pygtk. Now there are pygobject, python-clutter, python-clutter-gtk, pygi, 
python bindings for gobject introspection...

I see all of this in this way:

pygtk (python using gtk+ widgets tool kit)
python-clutter (python using clutter widgets tool kit)


Now
Because is this so? "Clutter-Gtk is a library which allows the embedding of a Clutter canvas" (python-clutter-gtk)

Because is not posible coding in python-clutter without gtk+?
It is not posible to deprecate pygtk in favour of python-clutter?

I rode about this kind of thing but I am a little confuse. If you see to pyqt or pyside are clear the libraries. With python gnome it seem to me as if different technologies should mix and maybe should be giving differents answers. I don't know if all of this libraries have cohesion.

Finally, I use Ubuntu. This is not at all a qt vs gtk+. No in any way. It is a question about the gnome technologies targeting python.

Thanks.

The GTK+ platform is quite flexible and allows you to extend it a lot. Moreover, the best development pattern for GTK+ is the one that seeks creating new custom widgets from the basic ones.

The only two modules you need for GTK+ are pygtk and gtk, which both are part of the python-gtk2 package. pygtk is just boilerplate to check the version of GTK+ (the pygtk.require("2.0") idiom) before importing the gtk module itself.

The rest is all about extended features. I guess python-clutter just imports pygtk and then adds the extended functionality to it. Why does it work that way? Modularity. If you import python-clutter, you'll get pygtk, but what if I just want GTK+?

---

