---
title: "GLib missing"
date: 2006-03-27
forum: Programming Talk
---

### Post by icyisamu on 2006-03-27
I am using Ruby-Gnome2.

In my laptop, I can compile this : 

```
require 'gtk2'
Gtk.init
window = Gtk::Window.new
window.show
Gtk.main
```

However, in my desktop, I get a Glib missing error.

What packages am I missing? I tried to install the required packages again but it doesn't seem to work.

---

### Post by M4av0 on 2006-03-27
I think you need libglib and/or libglibc, maybe even -dev versions. They are on the
ubuntu CD /pool/main/g/glib(c).
Hope this helps.

---

### Post by icyisamu on 2006-03-27
Thanks. Fixed by reinstalling all the required packages.

---

