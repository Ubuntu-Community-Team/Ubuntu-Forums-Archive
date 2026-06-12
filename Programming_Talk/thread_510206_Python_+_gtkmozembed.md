---
title: "Python + gtkmozembed"
date: 2007-07-26
forum: Programming Talk
---

### Post by apoth on 2007-07-26
I'm trying to use gtkmozembed, admittedly in gutsy, and it seems to seg fault - does anyone know if it's the fault of my programming? Test case:

```
#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk
import gtk.gdk
import gtk.glade
import gtkmozembed

win = gtk.Window()
browser = gtkmozembed.MozEmbed()
win.add(browser)
win.show_all()

gtk.main()
```

Thanks

---

### Post by angem1 on 2007-10-22
Hi, I have the same segmentation fault too, using the stable Gutsy release (7.10)

---

### Post by tonyriva on 2007-12-05
[https://bugs.launchpad.net/ubuntu/+source/gnome-python-extras/+bug/22487](https://bugs.launchpad.net/ubuntu/+source/gnome-python-extras/+bug/22487)

---

### Post by SeanHodges on 2007-12-05
I had the same problem in C++.

Type this in the console before you try and run the program:

```
export MOZILLA_FIVE_HOME=/usr/lib/firefox
```

Obviously you will need to set this each time you log out and in again. I worked around this by adding a shell command at the beginning of my program to set it before doing anything else. I'm sure there's a similar way of doing it in Python.

---

