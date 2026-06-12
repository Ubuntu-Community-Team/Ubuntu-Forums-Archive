---
title: "Gtk::GL::DrawingArea and key input"
date: 2007-01-19
forum: Programming Talk
---

### Post by evster on 2007-01-19
Hello,

I have a Gtk::Window which contains a Gtk::GL::DrawingArea.  I am able to get mouse clicks and mouse motion event in the Gtk::GL::DrawingArea, but for some reason I cannot get keyboard events.  I have added the Gdk::KEY_PRESS_MASK and implemented the on_key_press_event(GdkEventKey* event) function.  If I do the same thing in the Gtk::Window class it works fine, but this is not where I want the keyboard input to be handled.

Any ideas why I cannot get keyboard input in my opengl drawing area?

Thanks!
evster

---

