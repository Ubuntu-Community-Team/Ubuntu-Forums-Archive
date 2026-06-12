---
title: "pygtksourceview in win32"
date: 2009-10-09
forum: Programming Talk
---

### Post by giuspen on 2009-10-09
Hi,
did anybody have successfully installed the windows installer for pygtksourceview?
I run python 2.5.4 and have already successfully installed and used GTK and pyGTK.

I tried the one available in:
[http://ftp.gnome.org/pub/gnome/binaries/win32/pygtksourceview/2.2/](http://ftp.gnome.org/pub/gnome/binaries/win32/pygtksourceview/2.2/)
after having installed gtksourceview:
http://ftp.gnome.org/pub/gnome/binaries/win32/gtksourceview/2.2/"
but when i do "import gtksourceview" I get the error "ImportError: No module named gtksourceview".

Thanks in advance,
Giuseppe.

---

### Post by giuspen on 2009-10-26
If anybody interested, pygtksourceview is obsolete and pygtksourceview2 must be used instead.
The documentation can be found [here]("http://www.gnome.org/~gianmt/pygtksourceview2/index.html").
This way the correct import statement will be
[PHP]import gtksourceview2[/PHP]
and this works fine.

---

