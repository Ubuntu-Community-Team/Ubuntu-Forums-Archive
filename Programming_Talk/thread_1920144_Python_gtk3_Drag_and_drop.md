---
title: "Python gtk3 Drag and drop"
date: 2012-02-04
forum: Programming Talk
---

### Post by MG&amp;TL on 2012-02-04
OK, here's the  code I'm trying to run:

[PHP]#!/usr/bin/python

from gi.repository import Gtk

class UI():
	def __init__(self):
		
		w = Gtk.Window()
		w.set_default_size(600, 400)
		lab = Gtk.Label("drop here!")
		lab.connect("drag-data-received", self.on_drag_data_received)
		w.add(lab)
		w.connect("destroy", Gtk.main_quit)
		w.show_all()
		Gtk.main()

	def on_drag_data_received(widget, drag_context, x, y, data, info, time):
		print("Hello World!")

test = UI()
[/PHP]
However, the window produced is not sensitive to dnd, nor does it print anything if I drop anything on it. What am I doing wrong?

---

### Post by StephenF on 2012-02-04
Adapted from one of my programs:
```

droptargets = [
    ('text/plain', 0, 0),
    ('TEXT', 0, 1),
    ('STRING', 0, 2),
    ('text/uri-list', 0, 3)
    ]

dropwidget.enable_model_drag_dest(droptargets, gtk.gdk.ACTION_DEFAULT)

```

---

### Post by MG&amp;TL on 2012-02-04
Thanks, but can you explain a little more on that? I'm a dnd newb. :(

I'm just trying to get the filename of files/folders dropped onto a label. I'm sure it that it can't be that hard...:lol:

---

