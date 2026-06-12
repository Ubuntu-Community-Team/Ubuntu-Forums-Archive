---
title: "How to update text for python-eggtrayicon"
date: 2011-03-05
forum: Programming Talk
---

### Post by oakgrove on 2011-03-05
I'm using tint2 for a panel and want to show the cpu temp as a system tray icon since there aren't any plugins for tint2 that do that and I'd just like to know how to do this anyway whether there was one or not.  The script I have so far is:
```


#! /usr/bin/python
import pygtk,os
pygtk.require("2.0")
import gtk
import egg.trayicon
t = egg.trayicon.TrayIcon("CPUTemp")
cpu_temp=os.popen('sensors | grep "temp1:" | cut -d+ -f2 | cut -c1-2').read()
t.add(gtk.Label(cpu_temp))
t.show_all()
gtk.main()

```

Basically, it works the first time around but I'd also like it to update every 5 seconds or so.  Any help greatly appreciated.

---

### Post by oakgrove on 2011-03-05
I have just about had it.  Everytime I try to do anything cool in desktop Linux, I end up beating my head against the no documentation wall.  I have scoured the internet all day and can't find a single lick of real documentation for this module.  This is utterly ridiculous.  Note to any nascent programmers reading this: never get bogged down with undocumented libraries or programming languages.  You will experience frustration and unhappiness.  /rant

---

