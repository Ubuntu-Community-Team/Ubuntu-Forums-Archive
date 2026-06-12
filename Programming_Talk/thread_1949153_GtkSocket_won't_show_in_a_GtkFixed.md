---
title: "GtkSocket won't show in a GtkFixed"
date: 2012-03-29
forum: Programming Talk
---

### Post by mjoyce on 2012-03-29
I'm on Ubuntu 10.04 filesys, on a Marvell ARM CPU. kernel is 2.6.32.9.

        GtkWidget *fixed = gtk_fixed_new ();
        gtk_widget_show( fixed );
        socket = gtk_socket_new();
#if 1
// this line lets the code work
        gtk_container_add( GTK_CONTAINER( window ), socket );
#else
// with this line, it fails to show the contents of the socket
        gtk_fixed_put( GTK_FIXED( fixed ), socket, 0, 0 );
#endif
        gtk_widget_show( socket );

I need to use the (non-working) gtk_fixed_put scheme, since I need to add multiple widgets to the window.  I am getting a gtk critical error from the gtk_fixed_put li\
ne: assertion GTK_IS_ANCHORED (socket) failed.

Can anyone tell me why gtk_fixed_put is failing, when gtk_container_add works?

Thanks for any ideas,
-Michael

---

