---
title: "GdkEventButton Documentation in gtkmm?"
date: 2008-07-30
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-07-30
I want to catch the [Gtk::Widget::signal_button_release_event()](http://gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1Widget.html#41cc715ff6cea7056beaea8a93cd0a3e) of a widget. It says that my callback has to be like this: callback(GdkEventButton* event). But I can't find any documentation in gtkmm for **GdkEventButton**. I want, when this signal is emited, to get the coordinates of the mouse. I suspect that I need to use the "GdkEventButton* event" but I don't know how. Can you help me?

---

### Post by SledgeHammer_999 on 2008-07-31
bump

---

### Post by kutya61 on 2008-08-21
Hi!
I made a little [program]("http://superdog14.extra.hu/gtkmm/gdkeventbutton.cpp") to show how to use [GdkEventButton]("http://library.gnome.org/devel/gdk/stable/gdk-Event-Structures.html#GdkEventButton") structure.

Hope this helps!

---

