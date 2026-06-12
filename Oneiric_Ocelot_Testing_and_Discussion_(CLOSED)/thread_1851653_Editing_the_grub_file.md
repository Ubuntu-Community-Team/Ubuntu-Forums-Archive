---
title: "Editing the grub file?"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bikewrecker on 2011-09-28
Hey guys, so I have a windows 7 partition a ubuntu 10.10 partition and like a million of its older versions and a ubuntu 11.10 partition. I was wondering if I could get into the grub script file like I could with ubuntu 10.10 and delete all the older versions of ubuntu and re-arrange the order. I'm thinkin that ubuntu 11.10 doesnt have a grub script file or something, so is there another way I can do this?

---

### Post by dino99 on 2011-09-28
removing kernel
uninstall them with synaptic: bot 2 headers & image for each kernel you want to remove. Its a good idea to let 2 kernels installed in case of failer with one.

grub order menu:

with synaptic , install startupmanager, then set the order via menu

---

