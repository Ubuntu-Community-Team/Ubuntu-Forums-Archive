---
title: "Tray icon using PyGTK"
date: 2006-04-09
forum: Programming Talk
---

### Post by Fipaj on 2006-04-09
Hi!
I'm modyfing a little IRC app called Urk (I don't know Python well but this application is so simple...). One of new features listed by me is to minimize program to tray...

Can anybody write me an example for this action? I have already searched Net, but I didn't find anything useful.

Thanks!

---

### Post by nanotube on 2006-04-09
check out the pygtk page ([http://www.pygtk.org/)](http://www.pygtk.org/)), and search for word "trayicon"

you will see that a package called GnomePythonExtras provides an interface for making trayicons in gnome. that should be helpful.

---

### Post by Fipaj on 2006-04-10
Yes, thanks. But... there's no search on PyGTK.org, and using Google (trayicon site:pygtk.org) i found nothing...

---

### Post by llonesmiz on 2006-04-10
You should install the packages python-gnome2-extras, python-gnome2-extras-dev and python-gnome2-extras-doc. Then you can find an example program at /usr/share/doc/python-gnome2-extras/examples/egg/trayicon.py. I'm using dapper but it should be the same in breezy.

---

### Post by psychicdragon on 2006-04-10
Here's a quick example:
```
#! /usr/bin/python

import gtk
import egg.trayicon 	# egg == python-gnome2-extras

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

### Post by solarwind on 2008-05-10
> **psychicdragon said:**
> Here's a quick example:
```
#! /usr/bin/python

import gtk
import egg.trayicon 	# egg == python-gnome2-extras

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

Is there any documentation on egg.trayicon?

---

### Post by imdano on 2008-05-10
egg.trayicon is actually deprecated, but I've used it for backwards compatibility before (gtk.StatusIcon is somewhat new).  I couldn't find any documentation on it though, I just looked for code samples.

---

### Post by solarwind on 2008-05-10
> **imdano said:**
> egg.trayicon is actually deprecated, but I've used it for backwards compatibility before (gtk.StatusIcon is somewhat new).  I couldn't find any documentation on it though, I just looked for code samples.

Well, I need something (anything, I don't care), that will let me stick an icon and a label in the system tray with c++. Does either gtk.StatusIcon or the egg thing let me put a label or other simple widget in the system tray?

---

### Post by nanotube on 2008-05-11
> **solarwind said:**
> Well, I need something (anything, I don't care), that will let me stick an icon and a label in the system tray with c++. Does either gtk.StatusIcon or the egg thing let me put a label or other simple widget in the system tray?

yes it does. if you don't care about supporting versions of gtk prior to 2.10, use gtk.StatusIcon. it's nice.

---

