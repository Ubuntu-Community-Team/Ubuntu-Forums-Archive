---
title: "SDL resize event issue (c++)"
date: 2011-11-14
forum: Programming Talk
---

### Post by roadkillguy on 2011-11-14
I'm trying to make my game respond to the screen being resized.  This works, until I double click the taskbar (maximize the window) and then unmaximize it.  A VIDEORESIZE event is made for the first resize, but not on the return.  Interestingly enough, if I change the window size ever so slightly and then maximize and unmaximize, it works just fine.

Is this a bug with my window manager or SDL?  I'm using Xubuntu, and thus xfce.

Thanks in advance.

---

