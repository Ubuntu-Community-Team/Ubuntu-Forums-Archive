---
title: "Converting Pixbuf to Cairo. Help!"
date: 2009-08-29
forum: Programming Talk
---

### Post by racingsnailrider on 2009-08-29
Can anyone explain to me why this does not work and the way it should be done?

cairo_t*cr;
cr=gdk_cairo_create(widget->window);
GdkPixbuf*pix=gtk_image_get_pixbuf((GtkImage*)image);
gdk_cairo_set_source_pixbuf(cr,pix,0,0);
cairo_rectangle (cr,0,0,800,800);
cairo_fill(cr);

Many Thnx

---

### Post by napsy on 2009-08-29
What is image?

---

