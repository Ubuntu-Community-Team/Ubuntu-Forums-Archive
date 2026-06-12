---
title: "GTK Cairo advanced usage (VSync) help"
date: 2007-03-29
forum: Programming Talk
---

### Post by ZDemon on 2007-03-29
Does anyone know how to make a cairo widget wait for vsync?

My program looks like it is visually choppy, although it seems to be fast.

Do i have to use OpenGL?

Thanks for any input.

---

### Post by lnostdal on 2007-03-29
hi,
[http://developer.gnome.org/doc/API/2.0/gdk/gdk-Windows.html#gdk-window-begin-paint-rect](http://developer.gnome.org/doc/API/2.0/gdk/gdk-Windows.html#gdk-window-begin-paint-rect)
[http://developer.gnome.org/doc/API/2.0/gdk/gdk-Windows.html#gdk-window-begin-paint-region](http://developer.gnome.org/doc/API/2.0/gdk/gdk-Windows.html#gdk-window-begin-paint-region)

---

### Post by ZDemon on 2007-03-29
Yeah it works now.

```
GdkRegion *draw=gdk_drawable_get_clip_region (drawable_widget->window);
gdk_window_begin_paint_region (drawable_widget->window,draw);
cairo_t* cr = gdk_cairo_create(drawable_widget->window);
..
..
..
..
gdk_window_end_paint (drawable_widget->window);
```

Thanks Inostdal.

---

