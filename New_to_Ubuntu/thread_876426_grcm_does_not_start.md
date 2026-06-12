---
title: "grcm does not start"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by willbnz on 2008-07-31
Hi,

I started to use grcm for remote desktop management, then tried to add a rdesktop connection.  But it failed, and then grcm does not start.

If I click the icon under Internet it does nothing.

In Terminal

grcm
Segmentation fault

In Terminal as Root

grcm
(grcm:7833): Gtk-WARNING **: cannot open display:

How do I fix this issue?

---

### Post by willbnz on 2008-08-03
Sorted,

Reinstalled grcm.

Then had the same issue, but if I typed sudo or gksudo grcm  and it loaded again.  I think it may have had the old session or something.

---

