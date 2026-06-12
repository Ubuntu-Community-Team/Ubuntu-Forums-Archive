---
title: "Python + PyGTK?"
date: 2008-09-12
forum: Programming Talk
---

### Post by chris062689 on 2008-09-12
I want to start developing applications for GNOME / Ubuntu.
I'm a little confused though, I see a lot of GLADE packages...
I see glade-3, and glade-gnome-3.
Which one should I use?
Whats the differences?
What do all of the other developers use?
*confused*

---

### Post by jespdj on 2008-09-12
Did you look at the package descriptions of the packages glade-3 and glade-gnome-3 in Synaptic? For glade-gnome-3 it says:
> This package include the module that allows Glade to provide GNOME widgets in its palette.
So glade-gnome-3 is not the complete Glade package, it's just a module for Glade to provide GNOME widgets.

---

### Post by chris062689 on 2008-09-12
So most developers use the Gnome widgets where appropriate?

---

### Post by days_of_ruin on 2008-09-12
[Glade tutorial]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

[info on gnome widgets]("http://developer.gnome.org/arch/widgets/")

---

### Post by kknd on 2008-09-12
Do not use Gnome widgets, as it would add one more dependency and the widgets are being deprecated (see gtk project ridley). Most of then are part of GTK now (like GtkAboutDialog and GtkAssistant).

---

