---
title: "Load JPG into cairo"
date: 2010-10-24
forum: Programming Talk
---

### Post by stefano.facchini on 2010-10-24
How can I load a JPG image and use in cairo? cairo can load directly only the PNG format, but there must be (in gtk or elsewhere) some built-in library for handling other formats, for example something used by nautilus to show the thumbnails. Any suggestion?

thank you all!

---

### Post by gmargo on 2010-10-24
You can always convert your .jpg image into .png format using **convert** from the **imagemagick** package or **jpegtopnm**/**pnmtopng** from the **netpbm** package.  Surely there are other ways but I can't see a way to force cairo to accept a .jpg.

---

### Post by Linker101 on 2012-02-08
This really bugged me. I think the best way is to load the image file into a GdkPixbuf, then usegdk_cairo_set_source_pixbuf to load the image into your cairo context. So, (if you're trying to draw the image on a gtk window) the code might look something like this:

```

GdkPixbuf *image;
cairo_t *cr;

cr = gdk_cairo_create (window);
image = gdk_pixbuf_new_from_file("elephant.jpg");
gdk_cairo_set_source_pixbuf(cr, image, 0, 0);
cairo_paint (cr);

```Correct me if I'm wrong.

---

