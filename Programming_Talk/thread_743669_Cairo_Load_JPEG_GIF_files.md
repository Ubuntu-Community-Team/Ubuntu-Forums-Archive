---
title: "Cairo Load JPEG GIF files"
date: 2008-04-02
forum: Programming Talk
---

### Post by dosh on 2008-04-02
I notice there is the command cairo_image_surface_create_from_png is there an equivalent for loading JPEG or GIF files. Or is there another way like loading it via GDK and bringing it into cairo (any help much appreciated on this)

Thanks

---

### Post by kknd on 2008-04-02
> **dosh said:**
> I notice there is the command cairo_image_surface_create_from_png is there an equivalent for loading JPEG or GIF files. Or is there another way like loading it via GDK and bringing it into cairo (any help much appreciated on this)

Thanks

You can load a pixbuf in gdk and use it within cairo, but it is slow.

Its better to use the cairo version, like


[PHP]
image = Surface.createFromPng("tux.png");
cr:setSourceSurface(image,  0, 0)
[/PHP]

---

