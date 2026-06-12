---
title: "AMD Radeon hd 7600m series / Intel 4000 Graphics Problem"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by stratman15 on 2013-04-08
Hi, yesterday I finally managed to get Ubuntu 12.10 dual-booted with Windows 8 on my Sony Vaio E Series Premium laptop and I've noticed that the fan is running constantly and that I'm only getting an hour and a half of battery life compared to the 5 hour battery life I usually get on windows. I thought it might be a problem with the hybrid graphics and was wondering how I could fix this? I'm very inexperienced with Linux in general and the terminal so I'd appreciate any noob-friendly responses. Thanks.

---

### Post by Mark Phelps on 2013-04-08
Hybrid graphics  does NOT work well in Linux -- see the info in the link:

[https://wiki.archlinux.org/index.php/Hybrid_graphics]("https://wiki.archlinux.org/index.php/Hybrid_graphics")

---

### Post by stratman15 on 2013-04-08
Thanks for the response. If I disable the Radeon graphics card using the manual method in the link you provided will that only disable it in Ubuntu or will it also disable it in windows?

---

### Post by Mark Phelps on 2013-04-09
> **stratman15 said:**
> Thanks for the response. If I disable the Radeon graphics card using the manual method in the link you provided will that only disable it in Ubuntu or will it also disable it in windows?

Drivers in Linux and in Windows have no effect on each other at all.  Disabling a device in Ubuntu will have no effect on its performance in Windows.

---

