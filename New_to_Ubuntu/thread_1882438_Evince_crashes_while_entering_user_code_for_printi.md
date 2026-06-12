---
title: "Evince crashes while entering user code for printing"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by kumardeepu on 2011-11-17
Hello everyone, 

at work I have to use a user code to print but the moment I try to press any button in the user custom code filed, evince crashes. It was not a problem in ubuntu before but in ubuntu 11.10 only. 

It is really annoying to see that things which were working properly in the previous versions don't seem to work well. How can this be messed up in a newer version of ubuntu. 

please help if you know what's wrong.

---

### Post by Sealbhach on 2011-11-17
Start up evince from the terminal, just type

```
evince
```

and press enter. When it crashes again, there may be some information in the terminal. 

Unfortunately, nobody can help you unless you provide more information.

It might just be a bug in the theme, try changing the desktop theme to something else, see what happens.

.

---

### Post by kumardeepu on 2011-11-17
Oh thank you for that suggestion. Here is my output after evince crashed: 

```
dpu@oldleaf:~/Documents/papers$ evince 

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(evince:3151): Gtk-WARNING **: /build/buildd/gtk+3.0-3.2.0/./gtk/gtkcontainer.c:939: container class `GtkScrolledWindow' has no child property named `top-attach'

(evince:3151): Gtk-WARNING **: /build/buildd/gtk+3.0-3.2.0/./gtk/gtkcontainer.c:939: container class `GtkScrolledWindow' has no child property named `top-attach'

(evince:3151): Gtk-WARNING **: /build/buildd/gtk+3.0-3.2.0/./gtk/gtkcontainer.c:939: container class `GtkScrolledWindow' has no child property named `top-attach'
Segmentation fault

```

Thanks,

---

### Post by kumardeepu on 2011-12-01
bump...

also, changing the theme doesn't help.

---

