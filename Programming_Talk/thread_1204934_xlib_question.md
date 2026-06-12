---
title: "xlib question"
date: 2009-07-05
forum: Programming Talk
---

### Post by wwuster on 2009-07-05
I am working on some graphics programming and can create a window and draw things. I get the full window size ok, but can't find how to get the "client area" size. Ie, in windows there is GetClientRect() which returns a RECT that contains the dimensions of the drawable area. How can I get that information from xlib? I'm using C++.

thanks,
William

---

### Post by pokerbirch on 2009-07-05
A quick Google suggests [XGetGeometry()]("http://www.tronche.com/gui/x/xlib/window-information/XGetGeometry.html")

> The XGetGeometry() function returns the root window and the current geometry of the drawable. The geometry of the drawable includes the x and y coordinates, width and height, border width, and depth.

---

### Post by wwuster on 2009-07-06
> **pokerbirch said:**
> A quick Google suggests [XGetGeometry()]("http://www.tronche.com/gui/x/xlib/window-information/XGetGeometry.html")

Thanks,

William

---

