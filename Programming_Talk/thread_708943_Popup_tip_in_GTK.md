---
title: "Popup tip in GTK?"
date: 2008-02-26
forum: Programming Talk
---

### Post by solarwind on 2008-02-26
In Ubuntu, when the system wants to tell you a tip such as "restart your computer", a little icon pops up in the panel with a **popup tip**. I'm writing my own panel application and would like to use the same **popup tip** feature. How do I use those in my own program?

---

### Post by imdano on 2008-02-26
Those use [libnotify](http://www.galago-project.org/news/index.php), which is separate from gtk.

---

### Post by solarwind on 2008-02-26
> **imdano said:**
> Those use [libnotify](http://www.galago-project.org/news/index.php), which is separate from gtk.

Thanks!

---

### Post by ryanhaigh on 2008-02-26
if you were writing something in bash install the libnotify-bin package and use the notify-send command

---

### Post by solarwind on 2008-02-27
> **ryanhaigh said:**
> if you were writing something in bash install the libnotify-bin package and use the notify-send command

Thanks! I'm making a python application and there doesn't seem to be any documentation for the python binding. Do you think you could point me in the right direction?

---

### Post by imdano on 2008-02-27
check /usr/share/doc/python-notify/examples for, well, examples.  There is no API that I know of, but the examples should be enough.

---

### Post by ryanhaigh on 2008-02-27
After install python-notify check here

/usr/share/doc/python-notify/examples/applet-critical.png
/usr/share/doc/python-notify/examples/test-basic.py
/usr/share/doc/python-notify/examples/test-default-action.py
/usr/share/doc/python-notify/examples/test-image.py
/usr/share/doc/python-notify/examples/test-markup.py
/usr/share/doc/python-notify/examples/test-multi-actions.py
/usr/share/doc/python-notify/examples/test-replace-widget.py
/usr/share/doc/python-notify/examples/test-replace.py
/usr/share/doc/python-notify/examples/test-server-info.py
/usr/share/doc/python-notify/examples/test-urgency.py
/usr/share/doc/python-notify/examples/test-xy-stress.py
/usr/share/doc/python-notify/examples/test-xy.py

---

### Post by solarwind on 2008-02-27
You guys are awesome! Thanks so much! This is exactly what I needed!

---

