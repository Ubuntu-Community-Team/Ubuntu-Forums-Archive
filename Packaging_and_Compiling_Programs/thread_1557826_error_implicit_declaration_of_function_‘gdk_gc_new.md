---
title: "error: implicit declaration of function ‘gdk_gc_new’"
date: 2010-08-21
forum: Packaging and Compiling Programs
---

### Post by sygin on 2010-08-21
I am trying to build the evolution packages with debuild, the build fails with:

e-spinner.c:702: error: implicit declaration of function &#8216;gdk_gc_new&#8217;

Usually this error is a warning.

How can I compile without getting this error, does e-spinner need another header file?

Is there a way to compile without getting the error?

From e-spinner.c:
...
    GdkGC *gc;
...
    window = gtk_widget_get_window (widget);

    gc = gdk_gc_new (window);
    gdk_draw_pixbuf (window, gc, pixbuf,
        dest.x - x_offset - allocation.x,
        dest.y - y_offset - allocation.y,
        dest.x, dest.y,
        dest.width, dest.height,
        GDK_RGB_DITHER_MAX, 0, 0);
    g_object_unref (gc);


Thanks.

---

### Post by MadCow108 on 2010-08-21
you can fix it by including gdk/gdkgc.h from the gtk include directory
it is also included in the main gdk file gdk/gdk.h

---

### Post by sygin on 2010-08-21
Thank you for the reply.

I will give it a go, and report back.

Thanks again,
Sygin

---

### Post by sygin on 2010-08-21
I found that the file was already using gdk/gdk.h.

I sovled the problem by removing:

-GDK_DISABLE_DEPRECATED

from configure.ac

---

### Post by MadCow108 on 2010-08-21
are you using the development or stable version of gtk?

gdk_gc_new has not been deprecated in stable, so your change should not have had effect.
Don't know about unstable.

And even if, instead of enabling deprecated functions you should fix the code to not use them

---

### Post by sygin on 2010-08-22
Yes that would be the proper way  of fixing the issue. 
I appreciate the advice, thank you.

I am hacking Evolution for Maverick. Evolution has a bug that deletes mail on a POP server. I managed to 'fix' the bug but could not get Evolution 2.30.2 to compile. With your help MADCOW, I managed to get Evolution compiled and installed. 

I will used the hacked Evolution until a fix is released. This allows me to test Maverick, as I could not test it further without Evolution to get my mail.  

Thanks again,
Sygin.

---

### Post by DidRocks on 2010-08-31
Hey sygin,

I'm interested to your fix, can you point me to a patch?

---

