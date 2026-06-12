---
title: "c++ Gtkmm segmentation fault problem"
date: 2006-09-28
forum: Programming Talk
---

### Post by anansi on 2006-09-28
Im using Gtkmm 2.4 to create an interface in c++.

When i add the line
Gtk::ScrolledWindow m_ScrolledWindow;
to a header file of a class, it compiles as it should, but when i run the executable, i simply get segmentation fault. 
There is a reported Gtkmm bug similar to this (see [http://bugzilla.gnome.org/show_bug.cgi?id=78578](http://bugzilla.gnome.org/show_bug.cgi?id=78578) ), but i dont think it applies, as i have the updated gcc and gtkmm.

Im a gtkmm newbie, so the solution is probably quite trivial.

The segmentation fault is simply due to the addition of the line:
 Gtk::ScrolledWindow m_ScrolledWindow;
in the header file.

---

### Post by anansi on 2006-09-28
ok, the daft issue was sorted out, a mod should remove this thread

---

### Post by hrstefanov on 2008-11-25
Sorry for bumping an old thread but couldn't find an answer anywhere.

Does someone know how to solve this ?

---

