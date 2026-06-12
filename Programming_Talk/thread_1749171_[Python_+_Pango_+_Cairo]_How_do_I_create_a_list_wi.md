---
title: "[Python + Pango + Cairo] How do I create a list with right-aligned numbers?"
date: 2011-05-04
forum: Programming Talk
---

### Post by simeon87 on 2011-05-04
I have a pango.Layout and I'd like to display a numbered list with right-aligned numbers, such as:

```

  1 Content here
  2 Content here
  3 Content here
  4 Content here
  5 Content here
 10 Content here
 11 Content here
 12 Content here
 13 Content here
 14 Content here
101 Content here
102 Content here
103 Content here
104 Content here
105 Content here

```

Is there a straightforward way of doing this? I'm not inside a TreeView so I can't use multiple columns of that to create this effect. In Pango it's possible to add markup using <span> but I don't see something that can create a column effect.

One way would be to compute and draw each number and each content string manually but I was hoping there would be a better way to do this.

---

### Post by StephenF on 2011-05-04
I hope the following code is useful. Pay particular attention to the on_realize method.

The text width information is what I believe you will need in order to do a rendering with right justification. Yeah I agree with your worst fears. Manual rendering it is...
```

class DefaultEntry(gtk.Entry):
   def __init__(self, default_text, sensitive_override=False):
      gtk.Entry.__init__(self)
      self.connect("focus-in-event", self.on_focus_in)
      self.connect("focus-out-event", self.on_focus_out)
      self.props.primary_icon_activatable = True
      self.connect("icon-press", self.on_icon_press)
      self.connect("realize", self.on_realize)
      self.default_text = default_text
      self.sensitive_override = sensitive_override

   def on_realize(self, entry):
      layout = self.get_layout().copy()
      layout.set_markup("<span foreground='dark gray'>%s</span>" % self.default_text)
      extents = layout.get_pixel_extents()[1]
      drawable = gtk.gdk.Pixmap(self.get_parent_window(), extents[2], extents[3])
      gc = gtk.gdk.GC(drawable)
      gc2 = entry.props.style.base_gc[0]
      drawable.draw_rectangle(gc2, True, *extents)
      drawable.draw_layout(gc, 0, 0, layout)
      pixbuf = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB, True, 8, extents[2], extents[3])
      pixbuf.get_from_drawable(drawable, drawable.get_colormap(), 0, 0, *extents)
      self.empty_pixbuf = pixbuf
      if not gtk.Entry.get_text(self):
         self.props.primary_icon_pixbuf = pixbuf

   def on_icon_press(self, entry, icon_pos, event):
      self.grab_focus()
      
   def on_focus_in(self, entry, event):
      self.props.primary_icon_pixbuf = None
      
   def on_focus_out(self, entry, event):
      text = gtk.Entry.get_text(self).strip()
      if not text:
         self.props.primary_icon_pixbuf = self.empty_pixbuf
      
   def get_text(self):
      if (self.flags() & gtk.SENSITIVE) or self.sensitive_override:
         return gtk.Entry.get_text(self).strip() or self.default_text
      else:
         return ""
      
   def set_text(self, newtext):
      newtext = newtext.strip()
      gtk.Entry.set_text(self, newtext)
      if newtext:
         self.props.primary_icon_pixbuf = None
      else:
         try:
            self.props.primary_icon_pixbuf = self.empty_pixbuf
         except AttributeError:
            pass

```

---

### Post by simeon87 on 2011-05-04
> **StephenF said:**
> I hope the following code is useful. Pay particular attention to the on_realize method.

The text width information is what I believe you will need in order to do a rendering with right justification. Yeah I agree with your worst fears. Manual rendering it is...
```

class DefaultEntry(gtk.Entry):
   def __init__(self, default_text, sensitive_override=False):
      gtk.Entry.__init__(self)
      self.connect("focus-in-event", self.on_focus_in)
      self.connect("focus-out-event", self.on_focus_out)
      self.props.primary_icon_activatable = True
      self.connect("icon-press", self.on_icon_press)
      self.connect("realize", self.on_realize)
      self.default_text = default_text
      self.sensitive_override = sensitive_override

   def on_realize(self, entry):
      layout = self.get_layout().copy()
      layout.set_markup("<span foreground='dark gray'>%s</span>" % self.default_text)
      extents = layout.get_pixel_extents()[1]
      drawable = gtk.gdk.Pixmap(self.get_parent_window(), extents[2], extents[3])
      gc = gtk.gdk.GC(drawable)
      gc2 = entry.props.style.base_gc[0]
      drawable.draw_rectangle(gc2, True, *extents)
      drawable.draw_layout(gc, 0, 0, layout)
      pixbuf = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB, True, 8, extents[2], extents[3])
      pixbuf.get_from_drawable(drawable, drawable.get_colormap(), 0, 0, *extents)
      self.empty_pixbuf = pixbuf
      if not gtk.Entry.get_text(self):
         self.props.primary_icon_pixbuf = pixbuf

   def on_icon_press(self, entry, icon_pos, event):
      self.grab_focus()
      
   def on_focus_in(self, entry, event):
      self.props.primary_icon_pixbuf = None
      
   def on_focus_out(self, entry, event):
      text = gtk.Entry.get_text(self).strip()
      if not text:
         self.props.primary_icon_pixbuf = self.empty_pixbuf
      
   def get_text(self):
      if (self.flags() & gtk.SENSITIVE) or self.sensitive_override:
         return gtk.Entry.get_text(self).strip() or self.default_text
      else:
         return ""
      
   def set_text(self, newtext):
      newtext = newtext.strip()
      gtk.Entry.set_text(self, newtext)
      if newtext:
         self.props.primary_icon_pixbuf = None
      else:
         try:
            self.props.primary_icon_pixbuf = self.empty_pixbuf
         except AttributeError:
            pass

```

Thanks for your answer, it seems manual rendering is indeed the way to go.

I've come up with a way of doing it that requires less code. The width of the text is indeed important. I've been playing with creating a table of layouts which allows you to do:

```
def render(self, context, x, y, text):
   pcr = pangocairo.CairoContext(context)
   layout = pcr.create_layout()
   layout.set_markup(text)
   context.move_to(x, y)
   pcr.show_layout(layout)
   w, h = layout.get_pixel_size()
   return h
```

where x and y are computed elsewhere to decide where it should be rendered. Note that I'm returning the height of the text so that I know where the next line should be placed.

---

