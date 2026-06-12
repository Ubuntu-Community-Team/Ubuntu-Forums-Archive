---
title: "undefined reference error in c++"
date: 2011-01-26
forum: Programming Talk
---

### Post by afronova on 2011-01-26
Hey all,


I am trying to teach myself C++, but I keep running into this error when I try and call functions form the gtk library:

```
/usr/bin/ld: /tmp/ccrxlrYe.o: in function main:test.cc(.text+0xa): error: undefined reference to 'gdk_screen_get_default'
/usr/bin/ld: /tmp/ccrxlrYe.o: in function main:test.cc(.text+0x21): error: undefined reference to 'gdk_screen_get_height'
/usr/bin/ld: /tmp/ccrxlrYe.o: in function main:test.cc(.text+0x31): error: undefined reference to 'gdk_screen_get_width'
```

when I try and compile this:

```
#include <gdk/gdk.h>
#include <glib.h>

int main()
{	
	GdkScreen *theScreen;
	gint iHeight, iWidth;
	theScreen = gdk_screen_get_default();
	if(theScreen != NULL)
	{
		iHeight = gdk_screen_get_height(theScreen);
		iWidth = gdk_screen_get_width(theScreen);
	}
	
	return 0;
}
```

I'm just not sure what I'm doing wrong.
Any help would be monstrously appreciated!

thanks,

Afronova

---

### Post by worksofcraft on 2011-01-26
> **afronova said:**
> Hey all,


I am trying to teach myself C++, but I keep running into this error when I try and call functions form the gtk library:

```
/usr/bin/ld: /tmp/ccrxlrYe.o: in function main:test.cc(.text+0xa): error: undefined reference to 'gdk_screen_get_default'
/usr/bin/ld: /tmp/ccrxlrYe.o: in function main:test.cc(.text+0x21): error: undefined reference to 'gdk_screen_get_height'
/usr/bin/ld: /tmp/ccrxlrYe.o: in function main:test.cc(.text+0x31): error: undefined reference to 'gdk_screen_get_width'
```

when I try and compile this:

```
#include <gdk/gdk.h>
#include <glib.h>

int main()
{	
	GdkScreen *theScreen;
	gint iHeight, iWidth;
	theScreen = gdk_screen_get_default();
	if(theScreen != NULL)
	{
		iHeight = gdk_screen_get_height(theScreen);
		iWidth = gdk_screen_get_width(theScreen);
	}
	
	return 0;
}
```

I'm just not sure what I'm doing wrong.
Any help would be monstrously appreciated!

thanks,

Afronova

Well I compiled it with the following command:
```

gcc gdktest.c `pkg-config --cflags --libs gtk+-2.0 gmodule-2.0 gtkmm-2.4`

```

Most of that is probably not necessary, and my personal opinion is that all their "clever" systems are actually really stupid... but well if sledge hammers crack nuts why bother with nut crackers ?

p.s. note those are `back quotes` there around the pkg-config command... and `pkg-config` is a single command name not a pkg command with a -config option

---

### Post by afronova on 2011-01-26
Thanks, it worked!

But I'm confused as to why. Where there extra flags necessary to compile with functions from that library?

---

### Post by worksofcraft on 2011-01-26
> **afronova said:**
> Thanks, it worked!

But I'm confused as to why. Where there extra flags necessary to compile with functions from that library?

Yes... and I truly hate them for making simple things incredibly convoluted... but if you want to know exactly what extra compile options that invoked try the pkg-config command on it's own:
```

$ pkg-config --cflags --libs gtk+-2.0 gmodule-2.0 gtkmm-2.4
-pthread -D_REENTRANT -I/usr/local/include/freetype2 -I/usr/local/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include
 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0
 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/gtkmm-2.4
 -I/usr/lib/gtkmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/pangomm-1.4
 -I/usr/lib/pangomm-1.4/include -I/usr/include/gtk-unix-print-2.0 -I/usr/include/atkmm-1.6 -I/usr/include/gdkmm-2.4
 -I/usr/lib/gdkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0
 -I/usr/lib/sigc++-2.0/include -I/usr/include/cairomm-1.0 -I/usr/lib/cairomm-1.0/include  -pthread
 -Wl,--export-dynamic -L/usr/local/lib -lgtkmm-2.4 -latkmm-1.6 -lgdkmm-2.4 -lgiomm-2.4 -lpangomm-1.4 -lgtk-x11-2.0
 -lglibmm-2.4 -lcairomm-1.0 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm
 -lpangocairo-1.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  

```

sledgehammers ... say no more ;)

---

