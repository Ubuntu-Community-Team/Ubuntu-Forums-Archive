---
title: "Can't install Matrox 64 bit drivers MXG-M9128"
date: 2015-12-27
forum: New to Ubuntu
---

### Post by NotQuiteSU on 2015-12-27
I'm new to Ubuntu and administering Linux, I've used it mostly via CLI for several years, as a power user, not quite an admin.

I'm installing Ubuntu Server on a Optiplex 980 with a Matrox MXG-M9128 card. I found the driver page, since it doesn't seem to be installed by default.
[http://www.matrox.com/graphics/en/support/drivers/download/?id=639](http://www.matrox.com/graphics/en/support/drivers/download/?id=639)

It seems to require Xorg, but only checks up to version 1.15. I believe I currently have 1.17. Is there any way I can have more than 600x800 resolution?

---

### Post by sandyd on 2015-12-27
Hi, can you post the output of the following
```

lsmod
xrandr -q
```

---

### Post by NotQuiteSU on 2015-12-28
Looks like I accidentally installed the desktop version, not the server. Serves me right for jumping through menus. But I still wouldn't mind knowing how to solve this issue. I'll get the output tonight when I get home

---

