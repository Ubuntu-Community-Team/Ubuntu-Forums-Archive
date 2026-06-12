---
title: "How to toggle GTK menu images on/off by software?"
date: 2009-06-27
forum: Programming Talk
---

### Post by resander on 2009-06-27
There is a bool GTK property named gtk-menu-images that controls if images are to be shown in menuitems. I tried:

   g_object_set ((GObject *)window, "gtk-menu-images", false, NULL);

but it did not have any effect. Was that the right way?

There are many properties in GTK. How do I change them by software?

---

### Post by kknd on 2009-06-27
Usually you don't change style properties. If you wan't to change for the whole application, change that property in GtkSettings ([http://library.gnome.org/devel/gtk/stable/GtkSettings.html](http://library.gnome.org/devel/gtk/stable/GtkSettings.html)).

---

### Post by resander on 2009-06-28
Thanks for suggestion...

I have been to the GtkSettings page, which shows routines for setting string, long and double properties but none for bool properties.

However, I tried:

GtkSettings * gs = gtk_settings_get_default() ;
gtk_settings_set_long_property ( gs , "gtk-menu-images", 0 , "" );

and it worked. Hopefully, it only writes a single bool byte. Otherwise the neighbouring properties might get clobbered.

The GObject lists gtk-menu-images as one of its properties. All other objects inherit from GObject, so I thought it should be possible to change the gtk_menu_images property in my app via the the top window (window) using g_object_set.

Any ideas why it didn't work?

---

### Post by crdlb on 2009-06-28
"gtk-menu-images" is indeed a property, but only of GtkSettings objects. If you change your original code to use the GtkSettings* from gtk_settings_get_default () instead of window, it should work.

---

