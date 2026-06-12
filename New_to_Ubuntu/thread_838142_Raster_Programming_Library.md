---
title: "Raster Programming Library"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by lucasl on 2008-06-23
Hi.
This seemed like a beginner question, so I put this topic here.

It seems that I can't find a raster imaging library that allows you to **draw to an image** for any language, let alone ruby.

Right now I've just been using Cairo and treating it as a raster image (without anti-aliasing), which is bad because the pixels go round when zoomed in far, and it is really slow when zoomed because there is no easy way to only update part of the image.

Is there any better way to do this?

Thanks!

---

### Post by adewale on 2008-06-23
I can't really remember but i know there are raster libraries in ubuntu. Your synaptics package manager could help you search for it.

---

### Post by lucasl on 2008-06-24
Imlib 2 came up, its great! There is even a ruby binding!
The only thing I can't figure is how to use it with Gtk?
Any ideas?

Thanks!

---

