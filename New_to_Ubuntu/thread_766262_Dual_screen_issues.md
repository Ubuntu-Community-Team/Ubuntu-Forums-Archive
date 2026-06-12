---
title: "Dual screen issues"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by 3dgimp on 2008-04-25
Ok. So I've installed ubuntu 8.04 via wubi. I've enabled desktop effects and therefore the nvidia new driver. When ubuntu first booted, it cloned the same display on both screens. In the screen/resolution menu, both screens were visible and named correctly. After installing some updates, it now only works on one screen. In the screen/resolution menu it can only find one monitor called "unknown". 

What can I do to enable both monitors AND not have them clone, but instead extend the desktop?

Ta

---

### Post by Ub1476 on 2008-04-25
Install the nvidia control center package (nvidia-settings). Alternative, you can open Screens & Graphics and see if that recognize your monitors:

gksu displayconfig-gtk

---

