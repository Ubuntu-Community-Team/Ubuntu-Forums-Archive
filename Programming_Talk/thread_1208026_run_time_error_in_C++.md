---
title: "run time error in C++"
date: 2009-07-08
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-07-08
```

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:764): Gdk-CRITICAL **: gdk_cursor_new_for_display: assertion `GDK_IS_DISPLAY (display)' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.20.1/gobject/gtype.c:2458: initialization assertion failed, use IA__g_type_init() prior to this function

(process:764): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:764): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed


(process:764): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)
```

---

### Post by Mirge on 2009-07-08
What was wrong with the first thread?

---

### Post by c0mput3r_n3rD on 2009-07-08
No one was responding, so I'm changing the question because I need to know something different.  It compiles but now it doesn't run

---

### Post by dwhitney67 on 2009-07-08
It would seem that you are not initializing the toolkit.

---

### Post by c0mput3r_n3rD on 2009-07-08
And how would I initialize the tool kit?

---

### Post by dwhitney67 on 2009-07-08
Look at this [link]("http://asis.epfl.ch/GNU.MISC/gtk-1.2.8/gdk_3.html").  At a minimum, your app should do exactly what is shown.

I am not familiar with the GDK library; I would assume you are since, after all, you are the one using it.  Surely you have appropriate documentation and/or a tutorial that walks you through the most basic of applications?

---

### Post by c0mput3r_n3rD on 2009-07-08
No that's the problem, it's out of text book that I'm learning it, and it gives nothing about compiling it, installing the packages, just how to code it.  I'll definitely check out that link though thank you.

---

