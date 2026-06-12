---
title: "[SOLVED] Slow menu with custom kernel"
date: 2008-05-26
forum: Packaging and Compiling Programs
---

### Post by chadjohnson on 2008-05-26
Hello, I'm running Mint Linux (Daryna). I recompiled the kernel using the config file that came with the install, only changing it to use SLAB instead of SLUB (fglrx incompatibility). The kernel boots and everything runs fine, EXCEPT for the Mint Menu.

When I search for an item, it takes around 15 seconds for it to show, with the menu becoming frozen in the meantime. It also takes around 10 seconds sometimes when pausing over categories.

When I boot into the original kernel, the menu works fine.

Any ideas why this may be happening?

---

### Post by chadjohnson on 2008-05-26
bump

---

### Post by chadjohnson on 2008-05-27
Fixed (apparently)! I had forgotten to enable the Intel HDA sound module when I compiled the kernel. I recompiled with this, and the menu is, for some reason, as fast as it was before.

---

