---
title: "Gtk+ Window Management"
date: 2007-05-21
forum: Programming Talk
---

### Post by fophillips on 2007-05-21
When you destroy a window in Gtk, is there a simple way to get it back to its default without rebuilding everything from scratch on a button press?

For example: There is a window with three buttons, you close the window, click an icon in the system tray, the window appears again with the three buttons.

Thanks.

---

### Post by loell on 2007-05-21
you can use gdk_window_hide 

then use

gdk_window_show to show the window

---

### Post by fophillips on 2007-05-21
But what about when a user closes the window?

---

### Post by loell on 2007-05-21
i see, the usual situtaion.


i think you'll be using a function that returns a gtkwidget <-- the window , and in that function ,the window and other widget building is performed.

that way when it gets destroyed, an you want the window to be shown again, just call that function again to rebuild it then show it.

---

### Post by fophillips on 2007-05-21
Thanks, works perfectly now.

---

### Post by duff on 2007-05-21
you could also capture the close event, and prevent the window from being destroyed.  That'll also save the state of the window, so you may need to reset the widgets.

---

