---
title: "Booting from Live disc &quot;Failed to get gpio IRQ&quot;"
date: 2017-08-24
forum: New to Ubuntu
---

### Post by parallacks on 2017-08-24
I'm trying to set up a dual boot on an HP Laptop with a 1tb hard drive and an AMD FX 9800P APU. I successfully created the live disc and I boot into the menu where it asks you if you want to try Ubuntu without installing, install Ubuntu, etc. whenever i select either of the first two options there is a error message that pops up "[         5.422243] amd_gpio AMD0030:00: Failed to get gpio IRQ"
I've done a little bit of searching and haven't come up with a clear answer. If anyone has run into this before or could offer some advice that would be much appreciated

---

### Post by tom.peng on 2017-09-10
I ran into same failure with hp envy x360 AMD CPU. Tried CentOS minimal failed again with booting into black screen

We may need new AMD BIOS if Linux release no changes in recent time

---

### Post by BenginM on 2017-09-12
Hiya , #See

[https://bugs.launchpad.net/bugs/1683184](https://bugs.launchpad.net/bugs/1683184)

---

