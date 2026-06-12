---
title: "Drawing With Cario"
date: 2008-05-18
forum: Programming Talk
---

### Post by solarwind on 2008-05-18
Is it possible to draw directly onto the screen using Cairo? I want to make a desktop widget but I need to know how to draw directly onto the screen with Cairo. I want to make something similar to conky, but has a different purpose.

---

### Post by sznurek on 2008-05-19
[http://conky.svn.sourceforge.net/viewvc/conky/branches/conky1.5/src/x11.c?view=markup](http://conky.svn.sourceforge.net/viewvc/conky/branches/conky1.5/src/x11.c?view=markup)
(it is code for finding desktop window, setting transparent background etc.)
+

[http://www.cairographics.org/manual/cairo-XLib-Surfaces.html#cairo-xlib-surface-create](http://www.cairographics.org/manual/cairo-XLib-Surfaces.html#cairo-xlib-surface-create)
(you already know this, right?)

---

### Post by solarwind on 2008-05-19
> **sznurek said:**
> [http://conky.svn.sourceforge.net/viewvc/conky/branches/conky1.5/src/x11.c?view=markup](http://conky.svn.sourceforge.net/viewvc/conky/branches/conky1.5/src/x11.c?view=markup)
(it is code for finding desktop window, setting transparent background etc.)
+

[http://www.cairographics.org/manual/cairo-XLib-Surfaces.html#cairo-xlib-surface-create](http://www.cairographics.org/manual/cairo-XLib-Surfaces.html#cairo-xlib-surface-create)
(you already know this, right?)

Hmmm, are there any examples for those? I've never done this before and don't know where to start.

Edit: Found this [http://en.literateprograms.org/Hello_World_(C,_Cairo)#chunk%20def:x](http://en.literateprograms.org/Hello_World_(C,_Cairo)#chunk%20def:x)

---

