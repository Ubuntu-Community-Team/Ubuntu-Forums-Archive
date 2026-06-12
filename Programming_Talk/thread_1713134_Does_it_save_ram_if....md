---
title: "Does it save ram if..."
date: 2011-03-23
forum: Programming Talk
---

### Post by kevin11951 on 2011-03-23
Does it save ram in Python if instead of doing:

[PHP]import subprocess[/PHP]

I do:

[PHP]from subprocess import call[/PHP]

(subprocess and call are just examples)

Assuming I just need to use call...

---

### Post by trent.josephsen on 2011-03-23
Gee, I don't know.  If only there were some way to determine how much memory a process uses.  You could call it profiling, or something.

---

### Post by Reiger on 2011-03-23
Think about why the imports *do* and the answer will be obvious.

---

### Post by StephenF on 2011-03-23
Both of them import the entire module. Both of them store exactly one reference from it.

---

### Post by cgroza on 2011-03-23
Whatever it happens, it is negligeble. Those are useful just to reduce namespace polution.

---

