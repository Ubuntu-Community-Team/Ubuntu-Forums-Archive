---
title: "Creating scrollable drawing widget Gtk+"
date: 2009-07-15
forum: Programming Talk
---

### Post by hofsmo on 2009-07-15
Hi, I need some help creating a scrollable widget, which I can draw on. I've managed to scroll a GtkDrawingArea with GtkScrolledWindow, however I haven't manage to create a new object that does the same. Could anyone give me an example of an instance_init function needed to create this functionality?

---

### Post by kknd on 2009-07-15
You really need this? Can't you use gtk_scrolled_window_add_with_viewport?

---

### Post by hofsmo on 2009-07-15
It is not completely neccessary to have it as a seperate widget, and I know how to do it with gtk_scrolled_window_add_with_viewport, however I've been trying to create this widget for a while now. So it would be nice to know how to do it, if not for practical reasons, so for learning reasons. I have recently started creating my own classes, probably getting a little bit to eager.

---

