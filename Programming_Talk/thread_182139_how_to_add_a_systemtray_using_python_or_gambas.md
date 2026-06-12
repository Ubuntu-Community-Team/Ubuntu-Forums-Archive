---
title: "how to add a systemtray using python or gambas?"
date: 2006-05-25
forum: Programming Talk
---

### Post by hydrogen on 2006-05-25
how to add a systemtray using python or gambas? I want to write a program that will launch a system tray when it start. Can anyone tell me how?
Thank you very much!

---

### Post by unbuntu on 2006-05-25
in GNOME you may want to look at pygtk.  Haven't tried it myself, so can't help you further...

---

### Post by psychicdragon on 2006-05-26
Here's a simple example using PyGTK. You'll need to have python-gtk2 and python-gnome2-extras installed.

```
#! /usr/bin/python

import gtk
import egg.trayicon     # egg == python-gnome2-extras

def callback(widget, ev):
        print "Button %i pressed!" % ev.button


tray = egg.trayicon.TrayIcon("TrayIcon")
box = gtk.EventBox()
label = gtk.Label("Click Me!")
box.add(label)
tray.add(box)
tray.show_all()

box.connect("button-press-event", callback)

gtk.main()
```

---

### Post by hydrogen on 2006-05-26
Hi, Thank you!
  It  really worked! 
  if I want to use some network applet ( such as network interface ) in python, how to realize?

---

