---
title: "conditional load of modules"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by anoe on 2012-07-17
hi there, i am working with two kernels, the generic and the abogani's  realtime one for audio purposes. I'm using ubuntu 12.04 (precise pangolin), kernel 3.2.x in both cases.

the thing is, to use the wifi with the generic kernel i compiled the ralink drivers, and then added rt2860sta to /etc/modules. I also blacklisted some modules in /etc/modprobe.d/blacklist.conf. But, when working with the realtime kernel i have to manually load rt2800pci, because rt2860sta by itself doesn't work and i blacklist rt2800pci when using the generic kernel because i think this way my system works better.

so, my question is, is there a way to selectively load modules (or blacklist them) depending on the kernel i am using?

tx for your time.

---

