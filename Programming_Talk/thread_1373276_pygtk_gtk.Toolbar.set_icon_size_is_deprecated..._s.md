---
title: "pygtk gtk.Toolbar.set_icon_size is deprecated... so what to use?"
date: 2010-01-05
forum: Programming Talk
---

### Post by giuspen on 2010-01-05
Hi,
I was using the function:

gtk.Toolbar.set_icon_size()

to let the user change the toolbar icons size but I see that is deprecated.

The deprecation does not tell what I'm supposed to use in place of it, anybody can help me?

Thanks in advance.

---

### Post by Brandon Williams on 2010-01-06
Just keep on using it. According to [the release announcement](http://mail.gnome.org/archives/gnome-announce-list/2009-December/msg00068.html) for PyGtk 2.17, that method is being undeprecated.

---

### Post by giuspen on 2010-01-07
> **Brandon Williams said:**
> Just keep on using it. According to [the release announcement](http://mail.gnome.org/archives/gnome-announce-list/2009-December/msg00068.html) for PyGtk 2.17, that method is being undeprecated.

Thank you.
I found also that an alternative is:
[PHP]toolbar.set_property("icon-size", desired_icon_size)[/PHP]

---

