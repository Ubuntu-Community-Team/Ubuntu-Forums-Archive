---
title: "Setting a tray icon in gnome."
date: 2011-01-19
forum: Programming Talk
---

### Post by Dara Javaherian on 2011-01-19
Hello,

I would like to be able to set a tray icon (much like checkgmail or deluge does) in a bash script. Would anyone know how to do this?

Thank you,
Dara

---

### Post by Dara Javaherian on 2011-01-20
Anyone?

---

### Post by Dara Javaherian on 2011-01-20
OK I might as well answer my own question then. I couldn't do it in bash but I could do in in python:

```
import pygtk
import gtk
import sys
import time
myStatusIcon = gtk.StatusIcon()

while True:
  f = open('caps', 'r')
  time.sleep(0.1)
  if f.read()[0] == "0":
    myStatusIcon.set_from_file("caps.png")
  else:
    myStatusIcon.set_from_file("low.png")
  gtk.gdk.threads_init()
  gtk.main_iteration();


```

---

