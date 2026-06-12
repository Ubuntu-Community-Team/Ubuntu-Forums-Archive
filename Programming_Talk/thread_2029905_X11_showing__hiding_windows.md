---
title: "X11 showing / hiding windows"
date: 2012-07-20
forum: Programming Talk
---

### Post by Yours3lf22 on 2012-07-20
Hi,

I'm trying to show / hide X11 windows. I can already grab each window's id (Window object), but when I do XUnmapWindow() nothing happens. 
I also took a look at how it is done in Gdk, and they do the same thing, except they call XWithdrawWindow() on top-level windows. Now doing that didn't really help. What am I doing wrong?

---

