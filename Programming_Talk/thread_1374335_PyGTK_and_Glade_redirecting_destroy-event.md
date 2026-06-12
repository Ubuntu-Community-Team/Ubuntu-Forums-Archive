---
title: "PyGTK and Glade redirecting destroy-event"
date: 2010-01-06
forum: Programming Talk
---

### Post by Mach1723 on 2010-01-06
i have a window that comes up more than once in my application and i want the close button to not destroy the window but simply hide it (i.e window.hide()) how would i do this with PyGTK and glade?

I have read about the gtk destroy-event but dont really know how to disable it.

---

### Post by worseisworser on 2010-01-07
Check out what's being said in the *"More on Signals and Callbacks"* section here; [http://developer.gnome.org/doc/GGAD/cha-gtk.html](http://developer.gnome.org/doc/GGAD/cha-gtk.html) .. (hint: return value of your event handling callback).

---

