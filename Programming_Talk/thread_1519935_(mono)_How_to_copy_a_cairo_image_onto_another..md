---
title: "(mono) How to copy a cairo image onto another."
date: 2010-06-28
forum: Programming Talk
---

### Post by VH-BIL on 2010-06-28
If I create many cairo surfaces which are parts of the image, how can I copy them to a cairo surface to make the image.

(Windows C# programminer migrating to Linux)

---

### Post by tbastian on 2010-06-29
I don't do C#, but in C (GTK+) you call this function:

```

void gdk_draw_drawable (GdkDrawable *drawable,
                        GdkGC *gc,
                        GdkDrawable *src,
                        gint xsrc,
                        gint ysrc,
                        gint xdest,
                        gint ydest,
                        gint width,
                        gint height);


```

My guess is that you're looking for something similar.

---

