---
title: "How to get the X windows id from GTKmm?"
date: 2008-07-18
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-07-18
I am experimenting with gstreamer and GTKmm as a hobby. Anywayz I discovered that in order to display "video" in a **given** window I need to pass to gstreamer the X Window Id of that window. So how do I get that id in GTKmm?

---

### Post by SledgeHammer_999 on 2008-07-18
bump

---

### Post by SledgeHammer_999 on 2008-07-18
I think I found the answer but it involves a little of GTK too(instead of GTKmm)
```
GDK_WINDOW_XID(Glib::unwrap(window.get_window()))
```

Is there an alternative to GDK_WINDOW_XID in GTKmm?

---

### Post by bruce89 on 2008-07-18
[FONT="Mono"]gdk_x11_drawable_get_xid (GdkDrawable *drawable)[/FONT] is a C function, but I can't find the gtkmm equivalent.

---

