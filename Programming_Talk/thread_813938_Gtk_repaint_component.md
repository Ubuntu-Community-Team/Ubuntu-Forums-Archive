---
title: "Gtk repaint component"
date: 2008-05-31
forum: Programming Talk
---

### Post by xlinuks on 2008-05-31
Hi,
I'm using Gtkmm on Hardy, trying to figure out how to force a Gtk:: DrawingArea or Gtk:: Layout component to repaint itself.
In Java it was very easy by just calling the built-in repaint() method without any parameters for any type of GUI component.
Is there a way I can tell the component to repaint itself?
I only found the "bool MyArea:: on_expose_event(GdkEventExpose* event)"
but it only happens when the system calls this method, I don't know how to "fake" it. I tried digging into creating a GdkEventExpose but got scared, there's too many params.

---

