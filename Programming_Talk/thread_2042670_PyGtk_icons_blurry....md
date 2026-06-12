---
title: "PyGtk icons blurry..."
date: 2012-08-15
forum: Programming Talk
---

### Post by ragtag on 2012-08-15
I'm making a PyGtk plug-in for GIMP, and my icon shows up blurry.

I'm simply doing:

```
self.set_icon_name('gimp')
```

Which shows the correct icon. I've tried getting it directly from file too, both at 256x256 and from an svg, but they all look the same. It looks like like I'm only getting a 32x32 version, that is then being scaled up.

---

