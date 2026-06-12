---
title: "is drag and drop supported in a gtk.StatusIcon()?"
date: 2010-05-05
forum: Programming Talk
---

### Post by louis--taylor on 2010-05-05
Hello!
I have been experimenting with drag and drop for a small program I am writing.
Is it possible to use drag and drop on a gtk.StatusIcon()?

---

### Post by jeffathehutt on 2010-05-05
As far as I know, it will not work.  Drag and drop requires a widget from what I can tell, and gtk.StatusIcon is a gobject, not a widget. :-k

---

### Post by louis--taylor on 2010-05-06
Thanks!

---

