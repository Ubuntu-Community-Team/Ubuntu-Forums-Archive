---
title: "GdkWindow not a GdkDrawable?"
date: 2010-12-23
forum: Programming Talk
---

### Post by MacUntu on 2010-12-23
I'm trying to simply create a 22x22px GtkImage from a Cairo context. After reading through tons of out-dated information I gave up with:
```
GdkPixbuf *pixbuf = gdk_pixbuf_new (GDK_COLORSPACE_RGB, FALSE, 8, 22, 22);
GtkWidget *image = gtk_image_new_from_pixbuf (pixbuf);
GdkDrawable *drawable = image->window;
cairo_t *ctx = gdk_cairo_create (image->window);
/* do some drawing */ 
cairo_destroy (ctx);
```
Now image->window doesn't seem to be a GdkDrawable as I get the warning:
```
Gdk-CRITICAL **: IA__gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed
```

Maybe all of this is crap - at the end I need a GtkImage and I have to use an existing paint-method that's using a Cairo context. Any help is appreciated.

---

### Post by CharlesA on 2010-12-23
Closed by OP's request.

---

