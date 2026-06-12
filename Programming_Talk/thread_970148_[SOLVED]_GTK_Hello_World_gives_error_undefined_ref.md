---
title: "[SOLVED] GTK Hello World gives error undefined reference to `gkt_init'"
date: 2008-11-03
forum: Programming Talk
---

### Post by fornix on 2008-11-03
I just installed ubuntu 8.10 to check the new intrepid ubuntu.
The last version I had used before switching to gentoo was 6.06

Just to make sure gtk apps would compile, I installed the gtk-dev package and tried to compile this hello world program.
```
#include <gtk/gtk.h>

int main (int argc, char *argv[])
{
	GtkWidget *window;
	gkt_init (&argc, &argv);
	window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
	gtk_window_set_title (GTK_WINDOW(window), "Hello World");
	gtk_widget_show_all (window);
	gtk_main ();
	return 0;
}
```

when I try to compile this using the following command, i get error
```
fornix@nanosoft:~/c/gtk$ gcc hello.c `pkg-config --cflags --libs gtk+-2.0`
/tmp/cchDlaaG.o: In function `main':
hello.c:(.text+0x1c): undefined reference to `gkt_init'
collect2: ld returned 1 exit status
```

I guess it has something to do with environment, etc...

The output of my pkg-config is as follows...
```
fornix@nanosoft:~/c/gtk$ pkg-config --libs gtk+-2.0
-lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0
fornix@nanosoft:~/c/gtk$ pkg-config --cflags gtk+-2.0
-I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12
```

Any help is appreciated

---

### Post by WW on 2008-11-04
EDIT 2: Ignore my comments below... you have a typo: it should be gtk_init(), not gkt_init().


------------------------- 

> **fornix said:**
> 
Just to make sure gtk apps would compile, I installed the gtk-dev package [...]

Just to be sure... do you mean you installed [libgtk2.0-dev](http://packages.ubuntu.com/intrepid/libgtk2.0-dev)?

EDIT: Probably yes, otherwise pkg-config would have given an error.

---

### Post by fornix on 2008-11-04
> **WW said:**
> Just to be sure... do you mean you installed [libgtk2.0-dev](http://packages.ubuntu.com/intrepid/libgtk2.0-dev)?

EDIT: Probably yes, otherwise pkg-config would have given an error.

Yes. Thats the package I installed
libgtk2.0-dev
It did pull in dev packages of glib, atk, etc...

---

### Post by WW on 2008-11-04
Check out the edited version of my first post.  Hard to believe how many times I read your post without seeing the typo--it's even in the subject!

---

### Post by fornix on 2008-11-04
LOL. Very sorry for the post.
I still couldn't find out the typo. Now when I looked carefully, I noticed :lolflag:
Thanks for the responses for a stupid problem

---

