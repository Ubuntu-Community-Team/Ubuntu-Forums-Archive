---
title: "(pyGTK) Setting ToolButton Icon from Pixmap"
date: 2007-02-23
forum: Programming Talk
---

### Post by hatchek on 2007-02-23
Hi, I'm having some difficulty working with the ToolButton widget.

What I want to do is create a new icon for a ToolButton based off of a new color.

I used the code:
```

img = gtk.Image()
img.set_from_file("foo.png")
aToolButton.set_icon_widget(img)

```

..to load a PNG as the icon, but I want to be able to use a gtk.gdk.Drawable()  to create the icon on the fly, and then set that pixmap as the icon (basically, using the draw_rect, draw_line, draw_arc etc functions)

Any help?

---

### Post by hatchek on 2007-02-24
Ok, figured it out after whimsically trying things.. :D

To add a pixmap to a ToolButton as its icon, use the following code:

self.area is a drawing area widget added to the form.
```

self.colorA = gtk.gdk.Color(0,0,0)
self.iconA = gtk.gdk.Pixmap(self.area.window,24,24,24) #24x24 pixel, 24 bits/pixel
gc = self.iconA.new_gc(background=self.colorA, fill=gtk.gdk.SOLID,line_width=1,line_style=gtk.gdk.LINE_SOLID)
img = gtk.Image()
img.clear()
map = self.iconA.get_colormap()
color = map.alloc_color(self.colorA) #new color
gc.set_foreground(color)
iconA.draw_rectangle(gc, True, 0,0,24,24)
img.set_from_pixmap(icon,None)
img.show()
self.iconA.set_icon_widget(img)

```

---

