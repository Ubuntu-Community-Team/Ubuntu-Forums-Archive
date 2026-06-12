---
title: "Can't Install 8.04, dumped to busy box"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-05-17
I just got my new laptop.  And any time I try to install ubuntu on it, it automatically dumps me into busybox v1.1.3.

There is no windows install on this laptop.  It's a completely fresh hard drive.  How do I install this?

Here are some specs on my machine just in case:
Intel Core 2 Duo Mobile T9300 2.5 ghz with 6mb l2 cache
320gb Sata150 hard drive
4 gb DDR2 PC5300 ram
Nvidia 8600gt M video card.

---

### Post by EXCiD3 on 2008-05-18
Try adding "all_generic_ide" and/or "irqpoll". Sometimes you just need to add a boot parameter to get it to run. You add these by Pressing F6 at the first menu on the Ubuntu LiveCD.

---

