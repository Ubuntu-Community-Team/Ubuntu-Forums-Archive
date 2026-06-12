---
title: "Can Gtk+ access bookmarks?"
date: 2011-08-12
forum: Programming Talk
---

### Post by t1497f35 on 2011-08-12
Hi,
is there any API method to get access to bookmarks in Gtk?
Maybe in gio or glib?

---

### Post by cgroza on 2011-08-12
Bookmarks? As in browser functionality? In this case, I don't think there is much that glib can do for you.
Maybe the browser you are interested in has some sort of API to help you.

---

### Post by t1497f35 on 2011-08-12
As in "file browser", like Nautilus or thunar.
There seems to be no API for it, but I already figured out that the bookmarks are stored in ~/.gtk-bookmarks, so I'm accessing the bookmarks using my own code.

---

