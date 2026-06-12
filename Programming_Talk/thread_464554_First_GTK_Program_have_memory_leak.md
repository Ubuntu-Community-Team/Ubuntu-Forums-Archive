---
title: "First GTK Program have memory leak"
date: 2007-06-04
forum: Programming Talk
---

### Post by antonym55 on 2007-06-04
Hello,
when I use valgrind to check my first GTK program, I get this
> 
==6779== ERROR SUMMARY: 13 errors from 11 contexts (suppressed: 83 from 1)
==6779== malloc/free: in use at exit: 211,984 bytes in 2,688 blocks.
==6779== malloc/free: 7,773 allocs, 5,085 frees, 751,269 bytes allocated.
==6779== For counts of detected errors, rerun with: -v
==6779== searching for pointers to 2,688 not-freed blocks.
==6779== checked 487,556 bytes.
==6779== 
==6779== LEAK SUMMARY:
==6779==    definitely lost: 156 bytes in 11 blocks.
==6779==      possibly lost: 52,520 bytes in 51 blocks.
==6779==    still reachable: 159,308 bytes in 2,626 blocks.
==6779==         suppressed: 0 bytes in 0 blocks.
==6779== Use --leak-check=full to see details of leaked memory.


This program revise  from the first example of follow link
[http://www.gtk.org/tutorial/c39.html]("http://www.gtk.org/tutorial/c39.html")

```

#include <gtk/gtk.h>

static gboolean delete_event( GtkWidget *widget,
        GdkEvent  *event,
        gpointer   data )
{
    g_print ("delete event occurred,exit window.\n");
    gtk_main_quit();
    return FALSE;
}

int main(int argc, char * argv[])
{
    /*-- Declare the GTK Widgets used in the program --*/
    GtkWidget *window;

    /*--  Initialize GTK --*/
    gtk_init(&argc, &argv);

    /*-- Create the new window --*/
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
   
    g_signal_connect (G_OBJECT (window), "delete_event",
            G_CALLBACK (delete_event), NULL);

    /*-- Display the widgets --*/
    gtk_widget_show(window);

    /*-- Start the GTK event loop --*/
    gtk_main();

    /*-- Return 0 if exit is successful --*/
    return 0;
}

```

I compile it using:
```

gcc -g -o gtk main.c `pkg-config gtk+-2.0 --cflags --libs`

```

How can I fix the errors? It seems don't have "gtk_window_delete"  :( ](*,)

Thanks.

---

### Post by pragmatine on 2007-06-04
There is no real memory leak - when you call gtk_main_quit() and your program finishes, it automatically de-allocates all of its memory. Also, by default, after calling your delete_event signal handler, the window widget should be deleted automatically.

Don't worry - it looks fine, and is fine as far as I can tell.

---

