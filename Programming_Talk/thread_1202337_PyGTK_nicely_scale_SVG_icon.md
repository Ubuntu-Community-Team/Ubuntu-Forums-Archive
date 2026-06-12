---
title: "PyGTK nicely scale SVG icon"
date: 2009-07-02
forum: Programming Talk
---

### Post by Nevon on 2009-07-02
I'm currently working on an aboutdialog where I want to use an SVG icon as the logo. The original resolution of the SVG is 22x22, but I want to scale it up to 48x48. Normally that shouldn't be a problem, as SVGs scale quite nicely (at least when you're scaling up), but for some reason my logo looks like crap. 

This is what I'm currently doing:
```
logo = gtk.gdk.pixbuf_new_from_file("Full_Cup.svg")
logo = logo.scale_simple(48, 48, gtk.gdk.INTERP_HYPER)
about.set_logo(logo)
```

Is there another way to do this that doesn't completely ruin the quality of the image?

---

### Post by monraaf on 2009-07-02
Have you tried gtk.gdk.pixbuf_new_from_file_at_size() ?

---

### Post by Nevon on 2009-07-02
> **monraaf said:**
> Have you tried gtk.gdk.pixbuf_new_from_file_at_size() ?

Oh, thank you! I can't believe I missed that. It looks great now, anyway. Thank you for your help.

---

