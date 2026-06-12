---
title: "GTK stay on top window"
date: 2008-10-09
forum: Programming Talk
---

### Post by techmarks on 2008-10-09
Is there a property to set that will make it so a GTK window always remains on top?

That is it can't be covered by other windows on the desktop.

Thanks for any information.

---

### Post by Paul Miller on 2008-10-09
Keeping windows on top falls under the category of managing windows.  Since the window manager is responsible for managing windows, I don't think you can do this from GTK+.

---

### Post by Hairy_Palms on 2008-10-09
paul is right, this would be to do with metacity, not GTK

---

### Post by techmarks on 2008-10-09
right, don't think it could be done with GTK.

I tried this;
```
gtk_window_set_keep_above(GTK_WINDOW(window),FALSE);
```

It sort of works, it keeps the window always on top, but it still allows the other windows to slide underneath it.

I'm trying to create a panel at the top of the screen so that other windows just bump up against it at the top.

---

### Post by mali2297 on 2008-10-09
Have you tried using [GDK_WINDOW_TYPE_HINT_DOCK](http://library.gnome.org/devel/gdk/2.14/gdk-Windows.html#GdkWindowTypeHint)?

---

