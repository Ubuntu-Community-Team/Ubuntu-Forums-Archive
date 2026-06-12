---
title: "python + glade problems"
date: 2006-06-15
forum: Programming Talk
---

### Post by pwrlftr220 on 2006-06-15
I am running Ubuntu 6.06 and am trying to create a simple gui with glade and python.  I believe I have all the packages that I need installed, but I am running into an error that says "global name 'libglade' is not defined".  The code that I am using is below.  The gui is simply a window with a single label.  The relevant packages that I have installed are python, python-gtk2, python-glade2, glade, libglade2-0.  The error comes up on the line: "self.widgets = libglade.GladeXML ('pyglade.glade', "window1")"  Does anyone know why I am getting this error?

#!/usr/bin/env python

import gtk, gtk.glade

class GladeHandlers:
[INDENT]pass[/INDENT]

class WidgetsWrapper:
[INDENT]def __init__(self):[/INDENT]
[INDENT][INDENT]self.widgets = libglade.GladeXML ('pyglade.glade', "window1")[/INDENT][/INDENT]
[INDENT][INDENT]self.widgets.signal_autoconnect(GladeHandlers.__dict__)[/INDENT][/INDENT]

[INDENT]def __getitem__(self, key):[/INDENT]
[INDENT][INDENT]return self.widgets.get_widget(key)[/INDENT][/INDENT]

widgets = WidgetsWrapper()

gtk.mainloop ()

---

### Post by psychicdragon on 2006-06-16
The problem is with this line:
```
self.widgets = libglade.GladeXML ('pyglade.glade', "window1")
```
It should look like this:
```
self.widgets = gtk.glade.XML ('pyglade.glade', "window1")
```
Also, replace gtk.mainloop() with **gtk.main()**.

Here's the [PyGTK reference manual]("http://pygtk.org/pygtk2reference/index.html"), I'm sure you'll find it quite useful.

---

