---
title: "Including files in C, what am I doing wrong?"
date: 2007-04-30
forum: Programming Talk
---

### Post by Laterix on 2007-04-30
I'm learning C and GTK+ programming and I have a problem with including more source files. I use Anjuta and libglade for UI. I use libglade **glade_xml_signal_autoconnect** function to bind callback functions to UI. Everything works as long as every function is in the same **main.c** file. But there are a lot of callbacks and I would like to put them in different file called **main_window_callbacks.c** and then include this file in **main.c**. I do this and include statement is exactly in the place where those functions were when they were in **main.c**. But this doesn't work.

Here is the beginning of my main.c
```
/* Created by Anjuta version 1.2.4a */
/*	This file will not be overwritten */

#ifdef HAVE_CONFIG_H
#  include <config.h>
#endif

#include <gnome.h>
#include <glade/glade.h>

/* Global pointer to glade XML */
GladeXML *xml;

/* GTK (Glade) - User interface callbacks */
#include "main_window_callbacks.c"
```

one of my callbacks look like this (located in **main_window_callbacks.c**)
```
void
set_fullscreen (GtkWidget * widget, gpointer used_data)
{}
```

Now, when this function is in separated file, I get this compile error:
```
main_window_callbacks.c:3: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
```

I'm confused.

---

### Post by Compyx on 2007-04-30
You don't include "*.c" files, you include "*.h" files.

So in your case you would create a file "main_window_callbacks.h" in which you put the prototypes of the functions in the corresponding .c file. So you would put:
```

#include <glade/glade.h>
#include <gnome.h>

void set_fullscreen (GtkWidget * widget, gpointer used_data);

```
in "main_window_callbacks.h". The includes (at least gnome.h) are necessary for the declaration of GtkWidget and gpointer (I assume gnome.h includes gtk.h (which in turn includes gdk.h) which provides these types). You can then #include your .h file in your .c files which need them (including the corresponding .c file itself).


I suggest getting a good book on C programming, such as the excellent 'The C Programming Language, 2nd Edition" by Brain W. Kernighan and Dennis M. Ritchie (usually referred to as 'K&R2' on usenet and internet) and perhaps "Expert C Programming - deep C secrets" by Peter van der Linden, a book with some excellent advise and insights into the common pitfalls that come with programming in C (and quite humorous as well, at least for programmers).

I would also suggest that if you really want to learn to program in C, you should lay of the Gtk+ and other non-standard libraries until you've mastered C a little. Just stick to ANSI/ISO-C and use and learn the standard library first. That way you'll find it much easier to write portable code by keeping code that deals with non-standard libraries separated from the portable code.

---

### Post by Laterix on 2007-04-30
Thanks for the reply. I got it to work. It's true that GTK is probably not the easiest way to learn C. I have written [C++ application]("http://www.taimila.com/bluelink/") before and many Java and PHP applications. So it's frustrating to start from the bottom. :) I think that the hardest part with C is not the code itself, but the infrastructure around it. I mean, all this autotools, libtool etc. stuff. In Java and PHP, I don't need to worry about such a things.

But anyway, It works now and I'm learning. :) Thanks.

---

