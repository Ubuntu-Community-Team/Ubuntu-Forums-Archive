---
title: "Find out non-ascii gchar* length"
date: 2009-09-21
forum: Programming Talk
---

### Post by froggyswamp on 2009-09-21
Folks,
how do I get (or print) the length of "mes"?
```
gchar *mes = "&#26032;&#21326;&#32593;&#21271;&#20140;&#65305;&#26376;";
```
It's not ASCII, so I'm wondering what do I do in this case?
I'm learning C, googled, found nothing.

---

### Post by Linteg on 2009-09-21
You could use g_utf8_strlen if the string is UTF-8 encoded. GLib has a bunch of unicode related functions which may be useful to you, take a look at [http://library.gnome.org/devel/glib/stable/glib-Unicode-Manipulation.html](http://library.gnome.org/devel/glib/stable/glib-Unicode-Manipulation.html)

---

### Post by froggyswamp on 2009-09-21
Thanks a lot,
> glong length = g_utf8_strlen(mes, -1);
works fine now, I was looking in the wrong place, at
[http://library.gnome.org/devel/glib/stable/glib-String-Utility-Functions.html](http://library.gnome.org/devel/glib/stable/glib-String-Utility-Functions.html)

---

