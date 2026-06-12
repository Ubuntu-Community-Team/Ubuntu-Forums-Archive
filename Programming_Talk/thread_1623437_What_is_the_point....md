---
title: "What is the point..."
date: 2010-11-16
forum: Programming Talk
---

### Post by worksofcraft on 2010-11-16
I really **do wonder** about some of these libraries we get to work with.

Now take the various "miscellaneous utility" functions of glib and there we find things like:
> 
void g_nullify_pointer (gpointer *nullify_location);
Set the pointer at the specified location to NULL.

nullify_location :
the memory address of the pointer.

... fascinating... so I wonder what a gpointer actually is then and it doesn't take too long to discover:

```

typedef void* gpointer;

```

Zomg... what is the point in writing code like this? If I have a pointer and doesn't even have to be a "gpointer" but I can simply **assign** NULL to it and I really don't need to learn about utility functions like this. There is enough to try and remember as it is :shock:

Can anyone think of a reason for creating functions and typedef's like that?

---

### Post by Arndt on 2010-11-16
> **worksofcraft said:**
> I really **do wonder** about some of these libraries we get to work with.

Now take the various "miscellaneous utility" functions of glib and there we find things like:

... fascinating... so I wonder what a gpointer actually is then and it doesn't take too long to discover:

```

typedef void* gpointer;

```

Zomg... what is the point in writing code like this? If I have a pointer and doesn't even have to be a "gpointer" but I can simply **assign** NULL to it and I really don't need to learn about utility functions like this. There is enough to try and remember as it is :shock:

Can anyone think of a reason for creating functions and typedef's like that?

Interesting. And I wonder why they say that they define NULL like this

```
#    define NULL        (0L)

```

---

### Post by saulgoode on 2010-11-16
> **worksofcraft said:**
> Can anyone think of a reason for creating functions and typedef's like that?

I certainly can.

---

### Post by worksofcraft on 2010-11-16
> **Arndt said:**
> Interesting. And I wonder why they say that they define NULL like this

```
#    define NULL        (0L)

```

:shock:... serious? They actually redefine NULL in glib ?
there is me thinking it is as follows:
```

/usr/include/linux/stddef.h:#define NULL ((void *)0)

```

p.s. perhaps we need a new standard where we redefine all the symbols to be something unexpected... like how about:
```

#define NULL 0xF0UL

```

---

### Post by wojox on 2010-11-16
It's just a pointer but Gnome style, hence the g.

---

### Post by worksofcraft on 2010-11-16
> **wojox said:**
> It's just a pointer but Gnome style, hence the g.

sure... but why would one need a miscellaneous-utility function for setting one to NULL? You know they could even make it more general purpose and have a function to set it to other values too like...

[php]
#define gTRUE ("Pigs" != "can fly")
#define gFALSE (gTRUE ^ gTRUE)

void g_setify_pointer (gpointer *g_setify_location, gpointer g_setify_value) {
   if (g_setify_value == NULL) {
      gpointer *nullify_location = &(*g_setify_location);
      g_nullify_pointer(nullify_location);
   }
   else if (gTRUE != gFALSE) {
        *g_setify_location = g_setify_value;
   }
   return;
}
[/php]

It just doesn't make any sense to me

---

### Post by worseisworser on 2010-11-16
> **worksofcraft said:**
> I really **do wonder** about some of these libraries we get to work with.

Now take the various "miscellaneous utility" functions of glib and there we find things like:

... fascinating... so I wonder what a gpointer actually is then and it doesn't take too long to discover:

```

typedef void* gpointer;

```

Zomg... what is the point in writing code like this? If I have a pointer and doesn't even have to be a "gpointer" but I can simply **assign** NULL to it and I really don't need to learn about utility functions like this. There is enough to try and remember as it is :shock:

Can anyone think of a reason for creating functions and typedef's like that?

You can pass *g_nullify_pointer* around; do higher-order programming.

As for the *gpointer* typedef I suppose it makes things explicit, and perhaps they'd like to change all *gpointer*s to something else than *void** later.

---

### Post by saulgoode on 2010-11-16
> **worksofcraft said:**
> sure... but why would one need a miscellaneous-utility function for setting one to NULL? 

So it can be [passed as a callback.](http://www.gtk.org/api/2.6/gobject/gobject-The-Base-Object-Type.html#GWeakNotify)

---

### Post by worksofcraft on 2010-11-16
> **saulgoode said:**
> So it can be [passed as a callback.](http://www.gtk.org/api/2.6/gobject/gobject-The-Base-Object-Type.html#GWeakNotify)

... but it's no use for that:
```

void (*GWeakNotify) (gpointer data, GObject *where_the_object_was);

```

See... wrong number of parameters.

and it's no use for gtk call backs either because they need a bit more than a gpointer:
```

	// window configure event means it was moved or resized
	gboolean on_window1_configure_event(
		GtkWidget *pW, // the Window that received this signal
		GdkEventConfigure *E, // GdkEventConfigure received
		MyApp * pMyAppData) { ...

```

---

### Post by saulgoode on 2010-11-16
[GCallback ()]("http://library.gnome.org/devel/gobject/unstable/gobject-Closures.html#GCallback")

> void                (*GCallback)                        (void);

The type used for callback functions in structure definitions and function signatures. This doesn't mean that all callback functions must take no parameters and return void. **The required signature of a callback function is determined by the context in which is used** (e.g. the signal to which it is connected). Use G_CALLBACK() to cast the callback function to a GCallback.

---

### Post by Arndt on 2010-11-17
> **worksofcraft said:**
> :shock:... serious? They actually redefine NULL in glib ?
there is me thinking it is as follows:
```

/usr/include/linux/stddef.h:#define NULL ((void *)0)

```



I don't know if they actually do, but when I got to the description that you quoted, I could click on the "NULL", and then I got to their definition.

---

### Post by nvteighen on 2010-11-17
From /usr/include/glib-2.0/glib/gmacros.h:

```

/* We include stddef.h to get the system's definition of NULL
 */
#include <stddef.h>

```

---

### Post by Arndt on 2010-11-17
> **nvteighen said:**
> From /usr/include/glib-2.0/glib/gmacros.h:

```

/* We include stddef.h to get the system's definition of NULL
 */
#include <stddef.h>

```

Hurrah!

Strange that they even feel the need to comment it, I think.

---

### Post by Reiger on 2010-11-17
Well they also define NULL. So essentially what they've done is say: 
```

Do we have a sane system default:
Yes -> use it
No  -> use 0L

```

Presumably this stuff is ported to systems which don't have a sane default for it?

---

### Post by worksofcraft on 2010-12-12
> **Arndt said:**
> Hurrah!

Strange that they even feel the need to comment it, I think.

Yes very good point I have been wondering about the practice of commenting code...
[php]

enum layer_order_e {
	layer_unsorted, //------layer_unsorted
	layer_direct,   //------layer_direct
	layer_inverse   //------layer_inverse
};
[/php]

IMO with comments like that, they might as well abandon said practice :P

---

### Post by unknownPoster on 2010-12-12
> **worksofcraft said:**
> Yes very good point I have been wondering about the practice of commenting code...
[php]

enum layer_order_e {
    layer_unsorted, //------layer_unsorted
    layer_direct,   //------layer_direct
    layer_inverse   //------layer_inverse
};
[/php]IMO with comments like that, they might as well abandon said practice :P

[B]&#8220;Documentation is like sex: when it is good, it is very, very good; and when it is bad, it is better than nothing&#8221; --**** Brandon
[/B]

Edit: The language filter is blocking his name. :P

---

### Post by worksofcraft on 2010-12-12
> **unknownPoster said:**
> [B]“Documentation is like sex: when it is good, it is very, very good; and when it is bad, it is better than nothing” --**** Brandon
[/B]

Edit: The language filter is blocking his name. :P

Yes I'm glad of that :)
IMO "nothing" would actually be vastly superior to that complete waste of space :D

---

