---
title: "linker errors when compiling a simple gtk2 program"
date: 2011-12-02
forum: Programming Talk
---

### Post by napsy on 2011-12-02
Hello.

I use Ubuntu 11.10 x86-64 and tried to compile a simple Gtk+ 2.0 program using:
```

gcc `pkg-config --libs --cflags gtk+-2.0 glib-2.0 gthread-2.0` main.c -o main

```

The program is:

```

#include <gtk/gtk.h>
#include <glib.h>

int main(int argc, char **argv)
{
	GtkWidget *window;
	g_thread_init(NULL);
	gtk_init(&argc, &argv);

	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_widget_show_all(window);
	gtk_main();
	return 0;
}

```
But still, I get the following errors:

```

main.o: In function `g_once_init_enter':
/usr/include/glib-2.0/glib/gthread.h:350: undefined reference to `g_once_init_enter_impl'

```

The development packages for Gtk+ are installed. Please help, the same program compiles and links on other systems.

---

### Post by napsy on 2011-12-02
Solved, the system had three gcc versions. After choosing the oldest one (4.4), it compiled and linked w/o errors.

---

### Post by Bachstelze on 2011-12-02
The correct command is

```
gcc -o main main.c `pkg-config --libs --cflags gtk+-2.0 glib-2.0 gthread-2.0`
```

---

### Post by Favux on 2011-12-02
11.10 has the new toolchain.  The new syntax has the libraries at the end.  Presumably why the oldest version still worked.  I believe the other distros are also going to the new toolchain shortly.

---

