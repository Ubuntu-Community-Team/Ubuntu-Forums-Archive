---
title: "gtk+ scrollbar help"
date: 2007-01-29
forum: Programming Talk
---

### Post by napsy on 2007-01-29
Hello!

How do I get the scrollbar to always stickto the top of the child widget no mather if the child expands in the scrolled window? For example gnome-terminal where all the new lines are always visible and the previous lines are hidden but still visible via scrolling up.

Tnx.

---

### Post by psychicdragon on 2007-01-29
You need to use a GtkViewport to add scrolling to most widgets. Use the function [gtk_scrolled_window_add_with_viewport()]("http://developer.gnome.org/doc/API/2.0/gtk/GtkScrolledWindow.html#gtk-scrolled-window-add-with-viewport") to create a GtkScrolledWindow (with GtkViewport) containing the widget you want to scroll.

---

### Post by napsy on 2007-01-29
I add a TreeView to the ScrolledWindow and I think GtkViewport is not neccesery here.

---

