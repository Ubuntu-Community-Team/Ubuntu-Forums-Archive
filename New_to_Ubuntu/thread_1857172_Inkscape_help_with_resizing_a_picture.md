---
title: "Inkscape help with resizing a picture"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by Radical_Dreamer on 2011-10-09
Is there a way to make inkscape deal with bmp? because for some reason I can open these but if I try to alter it, saving doesn't work

---

### Post by Cheesehead on 2011-10-09
Inkscape is probably the wrong tool.

Inkscape is a vector-graphics tool. It can import raster-graphics, but is not really equipped to alter them.
bmp files are raster-graphics, not vector.

The easiest way to resize a raster image is using imagemagick, which is already installed on most Ubuntu systems. It uses the command line, but it you know what you want it's fast and simple.

If you want something a little easier to learn, try the nautilus-image-converter tool.

For full-strength raster, go for The Gimp.

Far an easy list of all the software in the Ubuntu repositories that may meet your needs,```
apt-cache search image resize
```Of course, you can change the search terms to anything you like.

---

### Post by Radical_Dreamer on 2011-10-09
yeah I worked with gimp to get it done.  Wasn't fun

---

