---
title: "[SOLVED] curious why this X (GDK) code is not working"
date: 2008-02-21
forum: Programming Talk
---

### Post by dosh on 2008-02-21
I am curious why the following code is not working. what I am doing is creating an X window and I can show it using XMapWindow, however when I get the GDK window handle(?) using gdk_window_lookup and then use gdk_window_show it will not show why is this?

```

#include <X11/Xlib.h>
#include <gdk/gdk.h>
#include <gdk/gdkx.h>
#include <stdlib.h>  
#include <stdio.h>    
#include <unistd.h> 
#include <string.h> 

int main( )
{
/* Added*/
    GdkWindow *gwin;
/*end added*/

    const char *display_name;
    if( ( display_name = (char *) getenv("DISPLAY") ) == NULL )
        display_name = "";

    /* Open a connection to the X server */
    Display *dpy = XOpenDisplay( display_name );
 
     int screen = DefaultScreen( dpy );
  
    Window root = RootWindow( dpy, screen );
    
    /*// create a window that we can draw on.*/
  Window win = XCreateSimpleWindow( dpy, root, 100, 100, 200, 200, 0, black.pixel, black.pixel );

   /*
This was taken out 

   XMapWindow( dpy, win );*/

gwin=gdk_window_lookup(win);

gdk_window_show(gwin);
      
    XFlush( dpy );
    
    while(1)
    {
        
    }

    
    XFreeGC( dpy, gc );
    XCloseDisplay( dpy );
    return 0;
}


```

---

### Post by rodo-&gt;dave on 2008-02-21
Window (from XCreateSimpleWindow) is a long.

The GdkWindow is a structure and the info has not been filled in yet.

look in /usr/include/gtk-2.0/gdk/gdkwindow.h at the _GdkWindowObject struct.

The XID in /usr/include.../gdkx.h is (GDK_DRAWABLE_IMPL_X11(((GdkWindowObject *)win)->impl)->xid)

Hope that helps some 

Is there a reason you want to mix and match between X11 and GDK?

---

### Post by dosh on 2008-02-22
Thanks Rodo->Dave

I'll be looking at those a bit more had a quick glance.

In answer to your question in short I don't like GTK is short thats the reason why I'm looking at GDK and X11. I'm a really beginner and have been having problems actually displaying graphics GDK but seem to be able to do it OK with X11. So looking at a way of doing the mixing with the 2. Have done some text via Cario onto a GDK window, but not graphics. Maybe that should be my question. How do you display graphics using GDK (without using GTK)?

---

### Post by lnostdal on 2008-02-22
[http://common-lisp.net/~lnostdal/programming/c/cairo.c](http://common-lisp.net/~lnostdal/programming/c/cairo.c)

replace the GtkWindow stuff with GDK stuff if you want .. (but why bother?)

---

### Post by dosh on 2008-02-22
Inostdal you've posted GTK code which I'm trying to avoid and use GDK and maybe cairo to draw to the window. As I stated early in answer to your comment "Why bother?" is because my own person opinion is that I prefer not to use GTK.

---

### Post by lnostdal on 2008-02-22
it was meant as a suggestion, but never mind .. you can clearly see what is going on .. just replace the gtk window and event code with gdk "versions" of it and you will have a window using only gdk and cairo (which is what you wanted) ....

---

