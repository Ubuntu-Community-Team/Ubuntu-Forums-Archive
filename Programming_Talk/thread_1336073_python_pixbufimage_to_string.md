---
title: "python pixbuf/image to string"
date: 2009-11-24
forum: Programming Talk
---

### Post by giuspen on 2009-11-24
hi,
I need to encode a pygtk pixbuf (or an image) into a string, I found that it is possible to save a pixbuf into a file and then encode base64, but is there a faster way to go directly from pixbuf to string or I have to go through saving a file to disk and then encode it?
Thanks in advance.

---

### Post by kripkenstein on 2009-11-24
This should work:
```

    pixel_string = pb.get_pixels()

```
assuming pb is a PyGTK pixbuf.

---

### Post by giuspen on 2009-11-24
> **kripkenstein said:**
> This should work:
```

    pixel_string = pb.get_pixels()

```
assuming pb is a PyGTK pixbuf.

but in the gtk.gdk.Pixbuf documentation I can't find how to build again the pixbuf from the pixel_string

---

### Post by kripkenstein on 2009-11-24
> **giuspen said:**
> but in the gtk.gdk.Pixbuf documentation I can't find how to build again the pixbuf from the pixel_string

For that direction, you can use [gtk.gdk.pixbuf_new_from_data]("http://www.pygtk.org/docs/pygtk/class-gdkpixbuf.html#function-gdk--pixbuf-new-from-data").

---

### Post by giuspen on 2009-11-24
> **kripkenstein said:**
> For that direction, you can use [gtk.gdk.pixbuf_new_from_data]("http://www.pygtk.org/docs/pygtk/class-gdkpixbuf.html#function-gdk--pixbuf-new-from-data").

thanks

---

