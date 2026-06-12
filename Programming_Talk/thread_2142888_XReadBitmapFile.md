---
title: "XReadBitmapFile"
date: 2013-05-07
forum: Programming Talk
---

### Post by thedardanius on 2013-05-07
XReadBitmapFile, im using it to load an icon for my cursor. First of all,
are they talking about a bitmap from windows, or what kind of bitmap? It persists to fail to load the bitmaps I supply. It returns something like invalid bitmap file.
and how do I load transparency? Since I'm coding cross-platform, on windows, the icon has transparency, but on linux/x11??? Please explain.

Thanks.

---

### Post by xytron on 2013-05-07
> **thedardanius said:**
> XReadBitmapFile, im using it to load an icon for my cursor. First of all,
are they talking about a bitmap from windows, or what kind of bitmap? It persists to fail to load the bitmaps I supply. It returns something like invalid bitmap file.
and how do I load transparency? Since I'm coding cross-platform, on windows, the icon has transparency, but on linux/x11??? Please explain.

Thanks.


read this;

[http://www.linuxjunkies.org/programming/GUI/xwindow/x11/pixmaps.html](http://www.linuxjunkies.org/programming/GUI/xwindow/x11/pixmaps.html)

The easy way to just open your image (whatever format it's in)  with a program like GIMP and then save it as a pixmap or an x bitmap.  GIMP can save in both formats.

---

### Post by thedardanius on 2013-05-07
So the bitmaps i load on windows arent the same bitmaps referred in the xlib?
Then do you know a format both windows and xlib function can load as icon? Else i have to supply my release with 2 different icons for each OS...
and bitmaps do not have transparency while .ico files in windows do.
Does anyone have a solution for that?

---

