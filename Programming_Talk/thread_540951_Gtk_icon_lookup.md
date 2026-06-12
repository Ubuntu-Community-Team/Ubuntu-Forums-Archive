---
title: "Gtk icon lookup"
date: 2007-09-02
forum: Programming Talk
---

### Post by tsg1zzn on 2007-09-02
Hi
I'm trying to display icons for the .desktop file entries in /usr/share/applications. Of course I am looking for a built-in (or easy) way of selecting the correct icon. The icons will displayed in a list, so they can not be larger than the requested size, as one larger icon will destroy the entire table layout. The exact pixel size isn't all that important.

If I simply use gdk_pixbuf_new_from_file() with the value of the Icon field from the .desktop file, most icons are not found. Bluefish, Geany and GIMP's icons are found, though, because they are written with the full path. Also I can't control the size (although I can scale the icons afterwards).

If I use gtk_icon_theme_get_default() followed by gtk_icon_theme_load_icon() then many icons are still not found, including Bluefish, Geany and GIMP! Quite a lot of the other icons are found, though, but there still is a severe problem. When I ask for icons at size 16 the icons for GnomeBaker and Transmission comes out at 32x32 and destroys the layout. When I ask for icons at size 22 or 24 those two icons comes out at 48x48. If I specify 32 the icon is sized at 64x64. If I specify 48 the icons are 100x100. If I specify 100 the icon is scaled up to a blurry and massive 256x256!
Unfortunately I can't simply specify 16 when I want 32 because all the other icons are scaled correctly.

Surely there must be a working icon lookup function in GTK+ as all but the most basic programs will need to show icons? What can I do to get all the icons at reasonable sizes?

---

