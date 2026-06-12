---
title: "Stuck on error message trying to install Ubuntu"
date: 2016-01-26
forum: New to Ubuntu
---

### Post by domino4 on 2016-01-26
Hi, I am trying to install Ubuntu on my PC, but every time I try to boot from USB, created with unetbootin (windows 10), I am greet by these messages:
[    0.024346] Ignoring BGRT: invalid satus 0 (expected 1)
[    2.937043] ACPI PCC probe failed.

It happens with both, Ubuntu 15.10 64-bit and Linux Mint 17.3 Cinnamon 64-bit. It just remains stuck on these error messages. What am I suppose to do now? I hope someone on this board can help me.

MSI Z97 Gaming 5
i5-4690k
GTX 980 ti
GTX 970
ASUS Xonar STX
8GB DDR3 RAM
SSD 850 Evo 120GB
SSD CT256MX100
WDC WD10EZEX

---

### Post by grahammechanical on 2016-01-26
Does it not load to a login screen?

I know from my own experience that ACPI PCC probe failed does not stop Linux from loading to a login screen. So, I would discount that. And from the little research I have done on the web about the Ignoring BGRT message is that it is just an advisory message.

If the loading is not progressing to a login screen then it might be nothing to do with those two messages. You have two graphic adapters. Are they both enabled? Or can you disable one graphic adapter and see if the live session then loads.

Regards.



Regards.

---

### Post by domino4 on 2016-01-31
> **grahammechanical said:**
> Does it not load to a login screen?

I know from my own experience that ACPI PCC probe failed does not stop Linux from loading to a login screen. So, I would discount that. And from the little research I have done on the web about the Ignoring BGRT message is that it is just an advisory message.

If the loading is not progressing to a login screen then it might be nothing to do with those two messages. You have two graphic adapters. Are they both enabled? Or can you disable one graphic adapter and see if the live session then loads.

Regards.



Regards.


Thank you very much, removing the second gpu did the trick.

---

