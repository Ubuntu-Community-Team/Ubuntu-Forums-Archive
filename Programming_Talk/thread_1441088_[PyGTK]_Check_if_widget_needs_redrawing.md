---
title: "[PyGTK] Check if widget needs redrawing"
date: 2010-03-28
forum: Programming Talk
---

### Post by smani on 2010-03-28
Hello,
I have a small problem: I have some scrolled window + viewport + image surface. I have a function that zooms in, keeping the target area under the mouse pointer, hence I do resize, then adjust scrollbars, basic code:

```

# a set_size_request triggers expose

def expose(self,widget,event):
  self.draw()

def draw(self):
  [Create buffer ...]
  if self.zoomTarget!=None:
    [...]
    self.scrolled_window.get_hscrollbar().set_value(self.scrollX)
    self.scrolled_window.get_vscrollbar().set_value(self.scrollY)
  [Draw buffer to the image]

```

This generally redraws once at the expose, and then at least once again after setting the scrollbars. I'd like to prevent the first redraw from happening, but I cannot write return after setting the scrollbar values since in some special cases the scrollbar aren't moved and hence no expose event would be fired afterwards (and I'm left with an undrawn surface).
So question: is there any way to determine if a redraw is queued in the gtk loop, so that I could write
```

# a set_size_request triggers expose

def expose(self,widget,event):
  self.draw()

def draw(self):
  [Create buffer ...]
  if self.zoomTarget!=None:
    [...]
    self.scrolled_window.get_hscrollbar().set_value(self.scrollX)
    self.scrolled_window.get_vscrollbar().set_value(self.scrollY)
    if <redraw queued>:
      return
  [Draw buffer to the image]

```
or is there any other common design pattern to handle this kind of problems?

Thanks!
Cheers
smani

---

### Post by SledgeHammer_999 on 2010-03-28
Maybe I didn't fully understand what you're asking, but why don't you call the "redraw" function yourself after setting the scrollbar's value?

---

### Post by smani on 2010-03-28
The problem ist not the redraw not getting called, but it getting called more often than necessary. I'd like to prevent the extra readraw from taking place. And btw I couldn't call the redraw immediately after asking the scrollbars to change since that operation will remain in the gtk queue for a small time, hence the draw function would be called before the scrollbars have actually changed.

---

