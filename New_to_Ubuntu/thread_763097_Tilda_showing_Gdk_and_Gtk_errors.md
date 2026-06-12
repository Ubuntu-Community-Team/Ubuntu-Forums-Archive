---
title: "Tilda showing Gdk and Gtk errors?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-04-22
Why is Tilda showing these Gdk and Gtk errors? (Ubuntu 7.10)

```
(tilda:5868): Gdk-CRITICAL **: gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed

(tilda:5868): Gtk-CRITICAL **: gtk_window_resize: assertion `height > 0' failed

(tilda:5868): Gtk-CRITICAL **: gtk_window_resize: assertion `height > 0' failed
```

The first error is only on startup, the last two errors come up any time that I try to retract/pull out the Tilda terminal. (for example, if I pull down Tilda, one error comes up about gtk_window_resize, not two)

---

### Post by linkmaster03 on 2008-04-23
Bump.

---

### Post by Perfect Storm on 2008-04-23
It's related to the GTK theme you are using. Nothing to worry about.
Sure you could open up a text editor and edit the configure file of the theme you are using - but it require a bit of knowledge to locate and change it.

---

