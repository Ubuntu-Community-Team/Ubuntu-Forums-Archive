---
title: "output directly to frame buffer in python? (easily?)"
date: 2007-06-27
forum: Programming Talk
---

### Post by oldmanstan on 2007-06-27
ok, back in the day in BASIC you could, for instance, draw a line directly on the screen using coordinates (as i recall it was dependent on screen resolution but i can't really remember)... i want to do the same thing in python, or at least approximately the same thing, creating a window for the line would be alright, it doesn't have to be directly lighting up pixels)

i found something called pyffy ([http://dave.whatever.nu/python/fb/](http://dave.whatever.nu/python/fb/)) but it seems to be defunct, the web site it links you to times out.

here's the post (from 2001) describing what the module does, this is basically what i want... [http://mail.python.org/pipermail/python-announce-list/2001-August/000979.html](http://mail.python.org/pipermail/python-announce-list/2001-August/000979.html)

any ideas? thanks!

---

### Post by Paul Miller on 2007-06-28
What you want is pygame.  As the name implies, it has many other useful functions besides drawing.

---

### Post by oldmanstan on 2007-06-28
> **Paul Miller said:**
> What you want is pygame.  As the name implies, it has many other useful functions besides drawing.

ahh, there we go, thank you greatly

---

