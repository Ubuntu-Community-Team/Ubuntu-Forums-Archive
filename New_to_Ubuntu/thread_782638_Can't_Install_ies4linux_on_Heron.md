---
title: "Can't Install ies4linux on Heron"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by FredJones on 2008-05-05
I had ies4linux on my Gutsy install but I just did a fresh install of Heron and I get:

ui/pygtk/python-gtk.sh: line 6: 30446 Segmentation fault      python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

I've had other errors along the way, but at present, this is what happens when I run the installer.

any ideas?

I did not update my /etc/apt/sources.list because wine and cabextract installed fine without that.

EDIT: SOLVED: I rebooted and now the installer works. Don't know why...

---

