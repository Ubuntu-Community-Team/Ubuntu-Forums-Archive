---
title: "Python/Clutter Segmentation fault with get_pixbuf"
date: 2010-02-15
forum: Programming Talk
---

### Post by saumitra_bg on 2010-02-15
I'm pulling my hair trying to figure out why I'm getting the segmentation fault. If you look at the following, I believe, I'm doing everything correctly but whenever I use get_pixbuf(), I get a segmentation fault.

Any help will be appreciated.

Thanks much.
-S

boxx:~/Desktop/0.1$ python
Python 2.5.2 (r252:60911, Jan 20 2010, 21:48:48) 
[GCC 4.2.4 (Ubuntu 4.2.4-1ubuntu3)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import clutter
>>> import gtk
>>> from clutter import cluttercairo
>>> stage = clutter.Stage()
>>> stage.fullscreen()
>>> stage.hide_cursor()
>>> (s_w, s_h) = stage.get_size()
>>> print "%s" %s_w 
800
>>> print "%s" %s_h 
600
>>> texture = clutter.Texture()
>>> src = "themes/Gloxygen/background.png"
>>> print "%s" %src
themes/Gloxygen/background.png
>>> pix_buf = gtk.gdk.pixbuf_new_from_file(src)
>>> texture.set_pixbuf(pix_buf)
True
>>> pixbuf1 = texture.get_pixbuf()
Segmentation fault
boxx:~/Desktop/0.1$

---

### Post by cariboo on 2010-02-16
This may be a better place to get your question answered.

---

### Post by saumitra_bg on 2010-02-20
Will appreciate some help on this.

Best,
S

---

