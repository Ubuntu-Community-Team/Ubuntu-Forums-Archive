---
title: "gui api in ubuntu lucid"
date: 2010-07-10
forum: Programming Talk
---

### Post by aracky on 2010-07-10
hi,
1) what gui libraries comes with ubuntu lucid? the aim right now is to draw a pixel without installing any libraries other then those i already have.
2) can anyone give me a reference to <X11/bitmaps/*> programming?

---

### Post by aracky on 2010-07-10
ok, after additional search i'll ask something else:
how come that i don't have Xlib.h installed (i have ubuntu 10.04) and yet gui programs such as the desktop or firefox are running?

in other words, as a gui newbe, what libraries do i have to have in order to write gui programs and X11 gui based programs
?

---

### Post by pbrane on 2010-07-10
You probably already have the libraries. You need the header files, something like libx11-dev, for instance. I don't know what exactly you need to have, I have almost all X11, Gtk, Gtkmm, openGL, etc, header files installed. If you write some code and the compiler or linker complains about something, you should be able to figure out what you need from there.

Try **sudo apt-get install libx11-dev** for starters.

Although I would recommend looking at Gtk, Gtkmm or Qt for GUI programming. Something higher level than X11.

---

### Post by phrostbyte on 2010-07-10
Ubuntu comes with GTK+ which is the widget toolkit of Gnome. GTK+ lets you create buttons, input boxes, menus etc. and manages them for you. Most GUI apps are built on GTK+. GTK+ on the low level uses Cairo, which is a 2D graphics library. You can use it directly too. Even lower then that is Xlib, which is shared with Qt (another widget toolkit as well).

You need to install the *-dev package for every library you plan to develop with. This includes the header and pkg-src manifests. End users using the library do not require these packages.

---

### Post by nvteighen on 2010-07-11
GUIs in GNU/Linux systems is highly modularized and abstracted. So, the lowest layer is X, which manages the interface between rendering and hardware. The highest layer are the "GUI toolkit" libraries such as GTK+, Motif, Qt, Tk, wxWidgets, etc. which provide you with prebuilt structures and mechanisms to make your life much easier than manually writing how to create a button in X.

GTK+ is the official GUI toolkit for GNOME. Qt, the one for KDE. But nothing really prevents you to use any different choice (you can even use GTK+ in KDE and Qt in GNOME), it's just that GTK+ will look better on GNOME and Qt better on KDE...

---

### Post by aracky on 2010-07-11
thank you all, it was very helpfull.

---

