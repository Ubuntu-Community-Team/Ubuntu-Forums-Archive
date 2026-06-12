---
title: "Cut/Copy buffer access."
date: 2007-12-21
forum: Programming Talk
---

### Post by solarwind on 2007-12-21
Hi all, how do I access the cut/copy buffers through c++? I have been searching a lot for this and I couldn't find an answer.

---

### Post by Klipt on 2007-12-21
Googling for *linux clipboard*, it seems that it depends on the desktop. E.g. for gnome you can use gtk clipboard functions:

[http://library.gnome.org/devel/gtk/unstable/gtk-Clipboards.html](http://library.gnome.org/devel/gtk/unstable/gtk-Clipboards.html)

---

### Post by solarwind on 2007-12-21
> **Klipt said:**
> Googling for *linux clipboard*, it seems that it depends on the desktop. E.g. for gnome you can use gtk clipboard functions:

[http://library.gnome.org/devel/gtk/unstable/gtk-Clipboards.html](http://library.gnome.org/devel/gtk/unstable/gtk-Clipboards.html)

Thanks, that's exactly what I needed!

---

