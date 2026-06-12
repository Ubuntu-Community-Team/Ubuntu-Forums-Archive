---
title: "Problem compileing GTK+ program."
date: 2007-12-10
forum: Programming Talk
---

### Post by Danikar on 2007-12-10
So I decited to check out GTK and I am following this tutorial.

[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)

I have libgtk2.0-dev installed. Not sure what else I need.

Thanks in advanced.

I am trying to compile this code

```
#include <gtk/gtk.h>

int main( int   argc,
          char *argv[] )
{
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show  (window);
    
    gtk_main ();
    
    return 0;
}
```

This is the error that I am getting

```

danikar@Merek:~/Documents$ gcc gtk_new.c -o rawr `pkg-config --cflags --libs gtk+-2.0`
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_free'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_sort_changed_iter'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_swap'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_hash_table_get_keys'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_get_length'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_new'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_iter_next'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_insert_before'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_get_end_iter'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_iter_prev'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_once_init_enter_impl'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_iter_get_sequence'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_get_begin_iter'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libpango-1.0.so: undefined reference to `g_unichar_get_script'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_remove'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_sort_iter'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_get_iter_at_pos'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_set'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_iter_get_position'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_get'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_iter_is_end'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_slice_copy'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_timeout_add_seconds_full'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_get_user_special_dir'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_once_init_leave'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_foreach'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_move'
/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../lib/libgtk-x11-2.0.so: undefined reference to `g_sequence_iter_is_begin'
collect2: ld returned 1 exit status

```

---

### Post by SledgeHammer_999 on 2007-12-10
I don't know what's your source compiles on my computer.
Try to reinstall libgtk2.0-dev.

---

### Post by Auria on 2007-12-10
try linking with glib... normally all needed libs should output but seems like it is not the case

---

### Post by MicahCarrick on 2007-12-10
Looks to me like GLib is out of date. Perhaps you have a newer version of GTK+ but older version of GLib.

The functions that are missing are new as of GLib 2.14. Try this command:
```
pkg-config --modversion glib-2.0
```

You should have 2.14 or greater.

---

### Post by Danikar on 2007-12-10
```
danikar@Merek:~/Documents$ pkg-config --modversion glib-2.0
2.12.13

```

How do I update glib?

---

### Post by MicahCarrick on 2007-12-10
Typically:

```
sudo aptitude update libglib2.0-dev
```

However, the odd thing is that you seem to have a newer version of GTK+ yet an older version of GLib.

Did you compile GTK+ from source or through a package? If you compiled it from source, did you also compile it's dependencies from source?

---

### Post by Danikar on 2007-12-10
No I think I got it from when I installed Anjuta.

Is there a way to uninstall everything and redo it?

---

### Post by MicahCarrick on 2007-12-10
It depends on how you installed it. If you used "configure, make, make install" to install it, then you go back to that same dir (or re-download the source) and do a 'make uninstall' to remove it (this would be for GTK). 

Then, using this:
```
sudo aptitude install libgtk2.0-dev
```

Will install the latest stable GTK+ including all the appropriate dependencies (including glib, cairo, atk, and a bunch of others).

---

### Post by Danikar on 2007-12-10
I did that and I am still getting the same error.

---

