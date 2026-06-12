---
title: "LibPng with shifted writing"
date: 2011-12-21
forum: Programming Talk
---

### Post by Rahuba.youri on 2011-12-21
Hello all! I need help in my work with libpng.

I try to write image (palette, 1 bit per pixel).
I have a array of bytes. Each byte contains 8 pixel. 
If i have image with 12 pixel width, each row consist of 1,5 bytes

I am using png_write_row. Can i say that libpng that following row need write not from begin "png_bytep", but with shift on 4 bit?

---

### Post by oldprogrammer on 2012-01-04
The best advice I can give you regarding libpng is: don't use it. The libpng API is a steaming pile of turds. There is an alternative, called DevIL (Developer's image library). It's in the standard repositories. There's documentation [here]("http://openil.sourceforge.net/docs/index.php") and a discussion on Nick Knowlson's blog [here]("https://profiles.google.com/111820015518413982003/buzz/SLbbb5ipvmW").

---

