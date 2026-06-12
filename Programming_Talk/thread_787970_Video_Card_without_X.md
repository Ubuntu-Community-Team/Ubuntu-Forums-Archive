---
title: "Video Card without X"
date: 2008-05-09
forum: Programming Talk
---

### Post by The_PhAnT0m on 2008-05-09
I am just curious, how does X interact with the hardware? The only way I know how to interact with the video card is through X. I looked at X.org's website but it didn't seem to have the answer, and I don't have the time to search through the source code.:( Anybody happen to know or at least be able to redirect me somewhere?

Thanks

---

### Post by clasificado on 2008-05-09
Not a howto but a guide (in Spanglish :D): The X doesn't talk directly with the video card, but with a kernel module instead.

the module name is defined in the xorg.conf

Section "Device"
Identifier "XFX 7300GT 256MB DDR2"
Driver "nvidia"

clasificado

---

### Post by The_PhAnT0m on 2008-05-09
Alright, so tell me if I understand this correctly. I use an Nvidia video card and consequently the proprietary driver. As I understand it, X loads the Nvidia driver (into the kernel) and uses it as a sort of proxy to interact with the hardware. Which I would also assume means that nvidia, flgrx, nv, etc. all expose a vaguely similar interface to X. Am I on the right track? I am not terribly familiar with X, as is probably apparent.

---

### Post by tseliot on 2008-05-09
Have a look at the [documentation]("http://wiki.x.org/wiki/Development?action=show&redirect=DevelopersPages").

---

