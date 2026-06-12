---
title: "GTK/GDK keyboard events assistance"
date: 2008-04-01
forum: Programming Talk
---

### Post by jazzor on 2008-04-01
there is a nice function called gdk_window_get_pointer which will give me details about the mouse button state for a window, so what happened to its keyboard equivalent?

i want to get the keyboard status (keypresses and shifts etc) for a window or even globally, but i cannot find such functions in gdk/gtk.

am i forced to use x11 libraries too?

---

### Post by kknd on 2008-04-01
> **jazzor said:**
> there is a nice function called gdk_window_get_pointer which will give me details about the mouse button state for a window, so what happened to its keyboard equivalent?

i want to get the keyboard status (keypresses and shifts etc) for a window or even globally, but i cannot find such functions in gdk/gtk.

am i forced to use x11 libraries too?

You can create a callback that catches keyboard events.

---

### Post by jazzor on 2008-04-02
I am not too familiar with gtk/gdk, but after looking through the reference i cannot find an appropriate function that will allow me to create a callback to catch keyboard events globally. If you would be so kind as to suggest how i could go about this? thanks.

---

