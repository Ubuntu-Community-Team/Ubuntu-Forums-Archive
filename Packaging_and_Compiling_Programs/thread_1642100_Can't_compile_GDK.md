---
title: "Can't compile GDK"
date: 2010-12-09
forum: Packaging and Compiling Programs
---

### Post by Andruk Tatum on 2010-12-09
I am trying to get a small program working, here's my minimalist program:
```
#include <gdk/gdk.h>

int main (int argc, char** argv) {
	gint num_screens = 0;
	GdkDisplay *dpy;

	dpy = gdk_display_open(NULL);

	num_screens = gdk_display_get_n_screens (dpy);

	printf("num_screens: %d\n", (int)num_screens);

	return 0;
}
```

Here's how I'm trying to compile it:
```
gcc `pkg-config --cflags --libs gtk+-2.0` test2.c -g -o test
```

It runs, but I get this:
```
./test 

(process:18381): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.26.0/gobject/gtype.c:2710: You forgot to call g_type_init()

(process:18381): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:18381): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.26.0/gobject/gtype.c:2710: You forgot to call g_type_init()

(process:18381): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:18381): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Segmentation fault
```

I'm not a compiling guru, so does anybody have any advice for how to get this extremely simple example to compile and run?

---

### Post by Andruk Tatum on 2010-12-10
I found the answer here: [http://www.gtkforums.com/post-16215.html]("http://www.gtkforums.com/post-16215.html")

You need to put in a gtk_init(&argc, &argv) before any calls to GTK+ or GDK, so my program should look like this:
```
#include <gdk/gdk.h>

int main (int argc, char** argv) {
	gint num_screens = 0;
	GdkDisplay *dpy;

	gtk_init(&argc, &argv);

	dpy = gdk_display_open(NULL);

	num_screens = gdk_display_get_n_screens (dpy);

	printf("num_screens: %d\n", (int)num_screens);

	return 0;
}
```

---

