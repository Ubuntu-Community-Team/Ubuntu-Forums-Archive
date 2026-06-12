---
title: "How can a GTK Status Icon be a drag &amp; drop target?"
date: 2008-08-30
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2008-08-30
I decided that some must-have functionality for Parcellite is the ability to drop text onto it as an alternative to the usual copy shortcut.

Here is the important part, in main.c (see last two lines)...

```
  /* Create status icon */
  if (!prefs.noicon)
  {
    status_icon = gtk_status_icon_new_from_stock(GTK_STOCK_PASTE);
    gtk_status_icon_set_tooltip(GTK_STATUS_ICON(status_icon), _("Clipboard Manager"));
    g_signal_connect(G_OBJECT(status_icon), "activate", G_CALLBACK(check_click), NULL);
    g_signal_connect(G_OBJECT(status_icon), "popup-menu", G_CALLBACK(show_parcellite_menu), NULL);
    gtk_drag_dest_set(GTK_STATUS_ICON(status_icon), GTK_DEST_DEFAULT_ALL, dnd_target_table, G_N_ELEMENTS (dnd_target_table), GDK_ACTION_COPY);
    g_signal_connect(G_OBJECT(status_icon), "drag-data-received", G_CALLBACK(dnd_receive_data), NULL);
  }
```

However, I get this error:
```
(parcellite:15560): Gtk-CRITICAL **: gtk_drag_dest_set: assertion `GTK_IS_WIDGET (widget)' failed

(parcellite:15560): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.4/gobject/gsignal.c:1669: signal `drag-data-received' is invalid for instance `0x65e640'

```

Some poking in documentation tells me that GTK_STATUS_ICON is descended straight from G_OBJECT, rather than any GTK widgets.
However, some more poking with wininfo reminded me that each status icon is indeed its own X window. Thus, in theory, this could work if I only knew which widget to use!

I can think of no examples for this functionality off hand, but I really really want it!
Will I have to implement the drag and drop stuff with a lower level API, or is there a really obvious solution? :)

Thanks!

---

### Post by mike_g on 2008-08-30
These are some ideas off the top of my head; not sure if they will be of any help, but anyway.

If in theory it should work, then you could try shutting up the GTK assertion and doing a straight cast. IE:
```
gtk_drag_dest_set(GtkStatusIcon*)status_icon, GTK_DEST_DEFAULT_ALL, ..
```
If the prog crashes then you can be pretty sure that it wont work.

You could also try creating a custom struct basically inheriting the GtkWidget and GtkStatusIcon features. Maybe that would work, but IDK :confused:

---

### Post by Mr. Picklesworth on 2008-08-30
Thanks for the try, Mike, but alas that did not work. (Nicely, however, the program does not crash; it goes on without. I love that...).

I did [some more reading]("http://library.gnome.org/devel/gtk/2.11/GtkStatusIcon.html#GtkStatusIcon.description")...
> Note that a GtkStatusIcon is not a widget, but just a GObject. Making it a widget would be impractical, since the system tray on Win32 doesn't allow to embed arbitrary widgets
So it looks like we can blame Windows. Hooray!
I know the notification area here can happily display real widgets, but I guess this has to be done with a different (eg: Not cross platform) API.

Thing is, I can only find info on doing it with GTK. Perhaps someone knows of an existing program that has a complex widget (not just a plain icon) for the notification area?

---

### Post by crdlb on 2008-08-30
If you really need the icon to be a widget, you can use the old EggTrayIcon in libegg: [http://svn.gnome.org/viewvc/libegg/trunk/libegg/tray/](http://svn.gnome.org/viewvc/libegg/trunk/libegg/tray/)

This is what people used to bundle with their apps to add a tray icon before GtkStatusIcon.

---

