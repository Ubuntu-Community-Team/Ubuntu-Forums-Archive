---
title: "Create a GdkBitmap from a gdk_pixbuf"
date: 2008-04-09
forum: Programming Talk
---

### Post by dosh on 2008-04-09
should I use gdk_pixbuf_render_threshold_alpha use in a alpha channel to a pixbuf image to create a gdkBitmap (that is to make a mask for use with gdk_window_shape_combine_mask)? hopefully that makes sense.

---

### Post by Zugzwang on 2008-04-09
I'm afraid that that's not 100% clear to me, but did you try it?

---

### Post by dosh on 2008-04-09
Sorry about that I need to reword it. First of all I'm trying to create a shaped window, yet not use gtk but GDK. I want to use the mask of a given graphic file (which is in colour) and could be of any type (png, gif jpg etc.). From my understanding after reading the manuals and other examples (mostly done using GTK), I need to load the file into a pixbuf, add an alpha channel, and convert it to Gdk_bitmap (depth of 1), than use a gdk_window_shape_combine_mask (to make the mask). That is why the gdk_pixbuf_render_threshold_alpha command. Yet I seem to be getting a problem with the bitmap. I try it and seem to get black pixels randomly place not the mask of the pixbuf.

Or is my understanding incorrect or missed something?

---

