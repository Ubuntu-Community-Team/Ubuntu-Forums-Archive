---
title: "GTK: Getting keyboard focus for a text entry field embedded in a GtkWindow dock"
date: 2009-05-12
forum: Programming Talk
---

### Post by C-- on 2009-05-12
So I have a GtkWindow in C++ (I am using the gtkmm bindings) that has been set to the Dock type hint, so that I can paint it in reserved window space via X11 struts. However, when the window type hint is set to a dock, there doesn't seem to be a way for text entry fields in that window to get keyboard focus when the user clicks on it. It has to be a dock so it can sit in reserved space, and it has to have embedded text entry fields. 

I know that in Java Swing one can paint a JWindow in reserved space, and then assign it to 1x1 pixel parent Frame so it can receive keyboard events/focus, but I have no ideas for a workaround in Gtk+. Any ideas?

---

### Post by NintenDave on 2009-05-12
Perhaps you need to embed the entry in an EventBox.
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1EventBox.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1EventBox.html)

---

### Post by C-- on 2009-05-12
Thanks, but the event box won't accept focus either.

---

