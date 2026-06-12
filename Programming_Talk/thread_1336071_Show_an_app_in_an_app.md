---
title: "Show an app in an app?"
date: 2009-11-24
forum: Programming Talk
---

### Post by kripkenstein on 2009-11-24
I want to show an app inside another app. That is, my app is a 3D renderer, and I'd like to show other currently running apps inside it. For example, if Firefox is running, to show Firefox inside my app (so I can move it around in 3D and do effects etc.)

So as a first approach, I did this:
```

import gtk

root = gtk.gdk.get_default_root_window()
geom = root.get_geometry()
w, h = geom[2:4]

pb = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB, False, 8, w, h)
pb = gtk.gdk.Pixbuf.get_from_drawable(pb, root, gtk.gdk.colormap_get_system(), 0, 0, 0, 0, w, h)

```

This uses Python and GTK to save the entire screen (with a little work I guess I could pick a specific window and not the entire screen). I can then read the pixel data and render that in my 3D app.

But the problem is this is very slow - I get 15 frames per second and 100% CPU (just from the code above, running in a loop - without even running my 3D app). Is there maybe some better way to do this?

---

