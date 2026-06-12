---
title: "GLib file utility functions... why?"
date: 2007-11-27
forum: Programming Talk
---

### Post by jespdj on 2007-11-27
The GLib library has a number of [file utility functions](http://library.gnome.org/devel/glib/2.14/glib-File-Utilities.html), such as g_fopen(), g_chmod() etc. which are wrappers for the standard POSIX file handling functions.

Two questions:

- Why does GLib have these functions when all they do is wrap functions existing in other libraries?

- Why is there no wrapper for fclose()? You're supposed to close a file with g_fopen() with fclose(). Why is there no g_fclose()? Ugly asymmetry... :-?

---

### Post by smartbei on 2007-11-27
In a similar vein, why does GLib use gint, gboolean, gchar, etc. when they are just typedef-ed to the basic variable type they represent (except for gboolean, which is an int (couldn't they have made it a char at least)).

And assuming that they do decide to use th g<type> series, why are 'int', 'void' (not gvoid? :D), etc. still in use in some of the functions?

Are they trying to use these to mark certain functions *for internal use*?

---

### Post by MicahCarrick on 2007-11-27
Much of this is discussed in the API docs. 

> Why does GLib have these functions when all they do is wrap functions existing in other libraries?

Basically, the wrapper functions and types are there to ensure that your code is cross-platform. Sometimes it is not necessary (yet) but allows for changes in the future,and then some are just there to complete the "set" so to speak (gint, gchar, etc.)

Often times, they may just wrap the libraries in POSIX systems and prehaps have to implement it or parts of it in Windows systems. Furthermore, should GLib be ported to other platforms in which these functions need to be implemented, it would be nice to have it behave the same in our GLib-based application regardless.

> In a similar vein, why does GLib use gint, gboolean, gchar, etc. when they are just typedef-ed to the basic variable type they represent (except for gboolean, which is an int (couldn't they have made it a char at least)).

If it was a char it wouldn't work like a boolean value. A boolean value IS an integer. Think: if (value) { do something } and if (!value). It helps readability in that you can see what that particular integer is being used for--especially in function prototypes and the like.

> And assuming that they do decide to use th g<type> series, why are 'int', 'void' (not gvoid? ), etc. still in use in some of the functions?

Not sure. void is still void, but I dont' know why int is used (or where it is used). I always use gint. There's also gpointer which is a void*

> Why is there no wrapper for fclose()? You're supposed to close a file with g_fopen() with fclose(). Why is there no g_fclose()? Ugly asymmetry...

I agree... there should be a g_fclose or g_close in this case. It would make things more "complete" I would think. However, I typically use GIOChannel over these functions.

---

### Post by llonesmiz on 2007-11-27
> **jespdj said:**
> 
- Why is there no wrapper for fclose()? You're supposed to close a file with g_fopen() with fclose(). Why is there no g_fclose()? Ugly asymmetry... :-?

From gtk-list:

> On Fri, 2007-09-14 at 07:02 +0200, [EMAIL="fred238@free.fr"]fred238@free.fr[/EMAIL] wrote:
[COLOR=#737373]> Hello all,[/COLOR]
[COLOR=#737373]> [/COLOR]
[COLOR=#737373]> With the g_fopen function, is there a g_close() or something ?[/COLOR]
[COLOR=#737373]> If not why there isn't ?[/COLOR]

because fclose() does not take a file name. the g_* variants are there
only because of the encoding of file names on different platforms (some
UTF-8, some in ISO codes, etc.), so you can use them to port
applications efficiently.

see: [http://library.gnome.org/devel/glib/stable/glib-File-Utilities.html](http://library.gnome.org/devel/glib/stable/glib-File-Utilities.html)

ciao,
 Emmanuele. 

From the api docs:

>  There is a group of functions which wrap the common POSIX functions  dealing with filenames ([g_open()]("http://library.gnome.org/devel/glib/stable/glib-File-Utilities.html#g-open"), [g_rename()]("http://library.gnome.org/devel/glib/stable/glib-File-Utilities.html#g-rename"), [g_mkdir()]("http://library.gnome.org/devel/glib/stable/glib-File-Utilities.html#g-mkdir"), [g_stat()]("http://library.gnome.org/devel/glib/stable/glib-File-Utilities.html#g-stat"),  [g_unlink()]("http://library.gnome.org/devel/glib/stable/glib-File-Utilities.html#g-unlink"), [g_remove()]("http://library.gnome.org/devel/glib/stable/glib-File-Utilities.html#g-remove"), [g_fopen()]("http://library.gnome.org/devel/glib/stable/glib-File-Utilities.html#g-fopen"), [g_freopen()]("http://library.gnome.org/devel/glib/stable/glib-File-Utilities.html#g-freopen")). The point of these  wrappers is to make it possible to handle file names with any Unicode  characters in them on Windows without having to use ifdefs and the  wide character API in the application code.

---

### Post by jespdj on 2007-11-28
Aha, thanks llonesmiz, that's a clear reason.
Still the asymmetry is a bit ugly...

---

