---
title: "What's Wrong with My TreeView/CellRendering Reasoning?"
date: 2008-11-05
forum: Programming Talk
---

### Post by moephan on 2008-11-05
Hello,

I am hoping that someone can help me understand how to work effectively with TreeViews in pyGTK. Essentially, I would like to be able to easily populate a TreeView with custom interactions, for example, using an extended gtk.Widget in in some cells.

I would like to be able to approach this by extending GenericCellRenderer, and in the on_render handler create gtk.Widgets, attach to their events, and plop them into place on the treeview. In this way, I could easily create custom user experiences and handle events like mouse events in a sane manner.

So the code that I would like to write would be kind of like this:

```

#within my CellRendererLink class
 def on_render(self, window, widget, background_area, cell_area, expose_area, flags):
  widg = gtk.WhatEverWidget(self.text)
  widg.connect("what-ever-event",whatevercallback)
  widget.add(widg)

```

However, I don't think I can do it that way. I think that what I have to do is extend GenericCellRenderer, and then treat the whole TreeView as one big canvas. The arguments for on_render tell me where to paint using pango. So to create a hyper link I created a pango.Layout, and set it's attributes so that it was blue and underlined.

So I render a link this way:
```

 def on_render(self, window, widget, background_area, cell_area, expose_area, flags):
  layout = self.get_layout(widget)
  if (flags & gtk.CELL_RENDERER_SELECTED) == gtk.CELL_RENDERER_SELECTED:  
   if widget.get_property('has-focus'):
    state = gtk.STATE_SELECTED
   else:
    state = gtk.STATE_ACTIVE
  else:
   state = gtk.STATE_NORMAL

  x_offset, y_offset, width, height = self.on_get_size(widget, cell_area)
  width -= self.xpad*2
  height -= self.ypad*2
  widget.style.paint_layout(window, state, True, cell_area, widget, "celllink", cell_area.x + x_offset + self.xpad, cell_area.y + y_offset + self.ypad, layout)

```

Besides having to manually recreated gtk.Widgets, handling mouse events does not seem right with this approach. I have to attach to the TreeView's mouse events and infer based on the path that the mouse is over what cell is points to, and command the CellRenderer to paint based different criteria I pass in. So my TreeView code has to have intimate knowledge of the CellRenderes with in it.

Then I handle changing the mouse cursor like this:
```

  #connect to the TreeView's events
  self.connect("motion-notify-event",self.set_cur,column)

 #handle mouse cursor in the Treeview code, based on columns
 def set_cur(self, widget, event, col):
  info = self.get_path_at_pos(event.get_coords()[0],event.get_coords()[1])
  if info == None:
   self.window.set_cursor(None) 
  else:
   moused_col = info[1]
   if moused_col != col:
    self.window.set_cursor(None)   
   else:
    self.window.set_cursor(gtk.gdk.Cursor(gtk.gdk.HAND2))

```

I hope I articulated my understanding and problem effectively. So, now, what am I doing wrong? I see that built in CellRenderers such as CellRendererCombo handle their own mouse events, and appear to use gtk.Widgets.

TIA

Cheers, Rick

---

### Post by moephan on 2008-11-10
No pyGTK masters in here who can help?

---

