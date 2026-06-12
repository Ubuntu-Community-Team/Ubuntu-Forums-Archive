---
title: "Cairo help please"
date: 2006-08-07
forum: Programming Talk
---

### Post by zootreeves on 2006-08-07
Could someone give me an example of how could i draw this shape with cairo?

[img]http://www.qkos.com/Engine/shape.png[/img]

Thanks

---

### Post by toojays on 2006-08-08
Here's a little example in pycairo which should give you an idea. It's based on an example in the python-cairo source package.```
#!/usr/bin/env python

import cairo
import gtk
from math import pi

def expose_event(widget, event):
    cr = widget.window.cairo_create()
    xc = 200
    yc = 0
    radius = 200
    angle1 = pi/2
    angle2 = pi
    cr.arc (xc, yc, radius, angle1, angle2)
    cr.line_to (0, 200)
    cr.close_path ()
    cr.fill ()

win = gtk.Window()
win.connect('destroy', gtk.main_quit)

drawingarea = gtk.DrawingArea()
win.add(drawingarea)
drawingarea.connect('expose_event', expose_event)
drawingarea.set_size_request(200,200)

```

---

