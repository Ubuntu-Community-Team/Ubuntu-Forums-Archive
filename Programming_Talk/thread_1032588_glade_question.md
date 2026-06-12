---
title: "glade question"
date: 2009-01-06
forum: Programming Talk
---

### Post by jworr on 2009-01-06
Is there anyway to create a layout in glade that is not apart of a top-level window or dialog?  I want to create a sub-layout of sorts to reuse in my application, but it forces me to use a top-level widget as the base of my project.  Any ideas?

---

### Post by dtmilano on 2009-01-07
See [gladexml]("http://www.pygtk.org/docs/pygtk/class-gladexml.html") doc.
You can specify the root element to start building from.

---

