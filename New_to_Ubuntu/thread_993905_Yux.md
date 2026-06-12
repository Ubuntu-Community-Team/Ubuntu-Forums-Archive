---
title: "Yux"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-11-26
Hello all!

Did somebody hear about a program called Yux? I got it from here:
[http://www.advogato.org/proj/Yux/](http://www.advogato.org/proj/Yux/)
I didn't manage to install it because I got some errors.
When I type "./configure" I get:
```
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
```
I continue with "make" and I get this:
```
troll@My-precious:~/Desktop/Yux$ make
make  all-recursive
make[1]: Entering directory `/home/troll/Desktop/Yux'
Making all in intl
make[2]: Entering directory `/home/troll/Desktop/Yux/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/troll/Desktop/Yux/intl'
Making all in po
make[2]: Entering directory `/home/troll/Desktop/Yux/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/troll/Desktop/Yux/po'
Making all in src
make[2]: Entering directory `/home/troll/Desktop/Yux/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -Wall 	 -g  -c support.c
In file included from /usr/include/gtk-2.0/gdk/gdkcairo.h:23,
                 from /usr/include/gtk-2.0/gdk/gdk.h:30,
                 from /usr/include/gtk-2.0/gtk/gtk.h:31,
                 from support.c:15:
/usr/include/gtk-2.0/gdk/gdkcolor.h:30:19: error: cairo.h: No such file or directory
In file included from /usr/include/gtk-2.0/gdk/gdkcairo.h:25,
                 from /usr/include/gtk-2.0/gdk/gdk.h:30,
                 from /usr/include/gtk-2.0/gtk/gtk.h:31,
                 from support.c:15:
/usr/include/pango-1.0/pango/pangocairo.h:58: error: expected ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:69: error: expected ‘)’ before ‘fonttype’
/usr/include/pango-1.0/pango/pangocairo.h:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pango_cairo_font_map_get_font_type’
/usr/include/pango-1.0/pango/pangocairo.h:83: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:87: error: expected ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:91: warning: type defaults to ‘int’ in declaration of ‘cairo_font_options_t’
/usr/include/pango-1.0/pango/pangocairo.h:91: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:92: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:99: error: expected declaration specifiers or ‘...’ before ‘PangoCairoShapeRendererFunc’
/usr/include/pango-1.0/pango/pangocairo.h:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pango_cairo_context_get_shape_renderer’
/usr/include/pango-1.0/pango/pangocairo.h:107: error: expected ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:108: error: expected ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:114: error: expected ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:117: error: expected ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:119: error: expected ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:122: error: expected ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:131: error: expected ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:134: error: expected ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:136: error: expected ‘)’ before ‘*’ token
/usr/include/pango-1.0/pango/pangocairo.h:139: error: expected ‘)’ before ‘*’ token
In file included from /usr/include/gtk-2.0/gdk/gdk.h:30,
                 from /usr/include/gtk-2.0/gtk/gtk.h:31,
                 from support.c:15:
/usr/include/gtk-2.0/gdk/gdkcairo.h:29: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gtk-2.0/gdk/gdkcairo.h:31: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gdk/gdkcairo.h:33: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gdk/gdkcairo.h:37: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gdk/gdkcairo.h:42: error: expected ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gdk/gdkcairo.h:44: error: expected ‘)’ before ‘*’ token
In file included from /usr/include/gtk-2.0/gdk/gdk.h:35,
                 from /usr/include/gtk-2.0/gtk/gtk.h:31,
                 from support.c:15:
/usr/include/gtk-2.0/gdk/gdkdrawable.h:196: error: expected specifier-qualifier-list before ‘cairo_surface_t’
In file included from /usr/include/gtk-2.0/gdk/gdk.h:50,
                 from /usr/include/gtk-2.0/gtk/gtk.h:31,
                 from support.c:15:
/usr/include/gtk-2.0/gdk/gdkscreen.h:51: error: expected specifier-qualifier-list before ‘cairo_font_options_t’
/usr/include/gtk-2.0/gdk/gdkscreen.h:107: warning: type defaults to ‘int’ in declaration of ‘cairo_font_options_t’
/usr/include/gtk-2.0/gdk/gdkscreen.h:107: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/gtk-2.0/gdk/gdkscreen.h:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from /usr/include/gtk-2.0/gtk/gtkprintoperation.h:31,
                 from /usr/include/gtk-2.0/gtk/gtk.h:137,
                 from support.c:15:
/usr/include/gtk-2.0/gtk/gtkprintcontext.h:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/gtk-2.0/gtk/gtkprintcontext.h:56: error: expected declaration specifiers or ‘...’ before ‘cairo_t’
make[2]: *** [support.o] Error 1
make[2]: Leaving directory `/home/troll/Desktop/Yux/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/troll/Desktop/Yux'
make: *** [all-recursive-am] Error 2
```

Can someone help?

Thanks in advance!

---

### Post by sirjoebob on 2008-11-26
I have no experience with this program. I use Pidgin for all my instant messaging needs.

---

### Post by Troll_the_Great on 2008-11-26
> **sirjoebob said:**
> I use Pidgin for all my instant messaging needs.

Me too, but I seem to have a problem with Pidgin (see my other thread) and I was searching for a replacement.

---

### Post by tibellus on 2008-11-26
Hello,

I might sound like "Captain Obvious", but did you get the libyahoo2-dev package? I will download the source and see if I get it to work on my computer. Please leave a reply though, and let me know if you have all the necessary libs.

A fellow Romanian. :)

**EDIT:** I think it might be some sort of typo in the "configure" script.

---

### Post by Troll_the_Great on 2008-11-26
Yep, I installed that package and no use. If you have more luck please let me know.
Numai bine!

---

### Post by tibellus on 2008-11-26
I get the same error as you do. I will try to edit the configure script, though. There must be some sort of problem in it, as the Yux project was abandoned 3 years ago and no more bugfixes were created since then. Anyway, I will check it out and probably will give you an answer tomorrow. I might think it's a programming error, not related to our systems.

---

### Post by Troll_the_Great on 2008-11-26
> **tibellus said:**
> I get the same error as you do. I will try to edit the configure script, though. There must be some sort of problem in it, as the Yux project was abandoned 3 years ago and no more bugfixes were created since then. Anyway, I will check it out and probably will give you an answer tomorrow. I might think it's a programming error, not related to our systems.

OK, I will wait.Thank you very much for the trouble.

---

