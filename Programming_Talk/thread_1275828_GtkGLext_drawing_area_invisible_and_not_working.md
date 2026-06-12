---
title: "GtkGLext drawing area invisible and not working"
date: 2009-09-26
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-09-26
I'm trying to make a program, which uses ODE to create heaps of 3D objects, then save the piles as new 3D models.

So far, the program only shows a window full of widgets that do nothing. It loads the interface from ui.xml, which I made with Glade Interface Designer.

ui.xml has an event box, and the event box has a drawing area. Drawing area has events set to GDK_EXPOSURE_MASK, and it has callbacks for realize, configure and expose.

The problem is, I can't get OpenGL rendering to the drawing area. The drawing area is invisible, I see just gray background of the window there. It's supposed to be pitch black.

Here's the realize callback of drawing area:
```

void da_realize( GtkWidget *da, gpointer user_data )
{
    GdkGLConfig *glconfig;

    g_print( "realize\n" );

    glconfig = gdk_gl_config_new_by_mode ( GDK_GL_MODE_RGB | GDK_GL_MODE_DEPTH | GDK_GL_MODE_DOUBLE );

    if ( !glconfig )
    {
        g_assert_not_reached();
    }

    if ( !gtk_widget_set_gl_capability( da, glconfig, NULL, TRUE, GDK_GL_RGBA_TYPE) )
    {
        g_assert_not_reached();
    }
}

```

I have tried using gtk_widget_realize, gtk_widget_show and gtk_widget_show_all, but da_realize gets never called (it never prints "realize").

During execution, it keeps printing this (obviously because da_realize never initialized OpenGL for the drawing area):
```

(Heaper:29500): GdkGLExt-CRITICAL **: gdk_gl_drawable_gl_begin: assertion `GDK_IS_GL_DRAWABLE (gldrawable)' failed

```

In Glade Interface Designer, the drawing area has callback signal for realize event, I have checked it at least 50 times.

So what could be the problem?


[b]EDIT: Solved :) :) :)

[quote=Tristan Van Berkom]
If your toplevel widget is visible=True in the glade file then
it will be shown by the time glade_xml_new() returns, so all
the realize handlers have already run before ever connecting
to the signal... if you hide the toplevel and do gtk_window_present()
yourself then you'll be able to get the signal.
[/quote]

[http://mail.gnome.org/archives/gtk-app-devel-list/2007-July/msg00150.html](http://mail.gnome.org/archives/gtk-app-devel-list/2007-July/msg00150.html)
[http://lists.ximian.com/pipermail/glade-devel/2003-December/000355.html](http://lists.ximian.com/pipermail/glade-devel/2003-December/000355.html)
[/b]

---

