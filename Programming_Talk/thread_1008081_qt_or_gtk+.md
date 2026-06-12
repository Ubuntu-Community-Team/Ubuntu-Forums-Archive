---
title: "qt or gtk+"
date: 2008-12-11
forum: Programming Talk
---

### Post by ettercap on 2008-12-11
This might be silly but anyways....
can any1 please explain the difference between 

1:QT / QT designer
2:GTK/ GLADE

i mean if i know how to use the  designer/ glade then why learn the who framework ?

and also which 1 to learn ?

plz help

---

### Post by pansz on 2008-12-11
The answer is what do you think programming is.

If design the ui is all that you write program for, then the whole framework might not be much useful for you.

I think Qt manual has said enough on this, it saids that you should have basic understanding of Qt anyway.

---

### Post by ettercap on 2008-12-11
u mean to say that glade n qt deginer just create gui ...
whereas gtk+/qt programming is needed to use the impleted gui ?

---

### Post by cb951303 on 2008-12-11
I like Glade and libglade better. It's easier to make good looking GUIs in glade. But i find QT to be simpler and easier to code. Especially GObject system used by GTK+ is confusing for me. Also with newest technologies such as qgtkstyle if you program in QT your application will look exactly same in both KDE and GNOME however it's not yet true for GTK. Sure there is gtk-qt-theme but it's no where near perfect. Also you should consider that QT is a C++ library whereas GTK is a C library. Personally I think the only downside of QT over GTK is the designer application and it's not such a big deal.

EDIT: I may be flamed to say this but if you're new to OOP paradigm I would stay away from Glib (GObject) which is used by GTK+

---

### Post by nvteighen on 2008-12-11
Qt and GTK+ are GUI toolkits: just stuff to help you write GUIs more quickly than getting yourself dirty with direct X11 programming... but you always use them "in" a certain programming language. As the others have said Qt is for C++ and GTK+ is for C, so you'll need to use those languages to be able to program with them... or to use bindings like PyQt and PyGtk (for Python, but there are for other languages too).

The designer is a help. You don't need it **in theory** to be able to have a nice GUI... but **in practice** they're the only sane way to have a working GUI. Nevertheless, it's good to start without a designer (but restricting yourself to simple GUIs) in order to understand the toolkit's basic behaivor.

---

