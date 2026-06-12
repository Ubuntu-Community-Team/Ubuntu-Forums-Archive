---
title: "How do you convert a pixbuf to a Bitmap mask"
date: 2008-04-07
forum: Programming Talk
---

### Post by dosh on 2008-04-07
I'm using GDK to to load an image into a pixbuf now I'm trying to convert that into a bitmap mask (1 bit depth) any help much appreciated.

---

### Post by mike_g on 2008-04-07
I only started using Gtk the other day so I dot knwo if theres a built in function to do this. However it shoudl be pretty easy to convert yourself. 

Something like:
```
guint8 *image_mask = malloc(IMAGE_WIDTH*IMAGE_HEIGHT);
guint8 *ptr = image_mask;
for(y=0; y<IMAGE_HEIGHT; y++)
for(x=0; x<IMAGE_WIDTH; x++, ptr++)
    *ptr = (image[x][y] == MASK)? 0 : 1;

```
Obviosly theres going to be a little extra work involved converting GdkColors, but its one way it could be done. Also if memory is relly tight you might want to pack eight bits into each byte, instead of just one.

---

