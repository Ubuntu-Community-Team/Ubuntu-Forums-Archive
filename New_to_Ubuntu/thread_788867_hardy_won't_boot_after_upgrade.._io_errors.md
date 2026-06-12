---
title: "hardy won't boot after upgrade.. i/o errors?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by epidemiks on 2008-05-10
Hi,
I just updated to 8.04 from 7.10.

I'm running XP on a second drive and can still boot into it from GRUB no probs.

Upgrade went smoothly, no obvious issues, but when booting into the hardy i get:

```

ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 acion 0x2 frozen
ata1.01: cmd C8/00.08.00.../fo tag 0 dma 4096 in
Buffer I/O error on device sdb, logical block 0
```

and end up at a Busybox prompt.
happens for both rt and generic kernel..
would trying the recovery mode help?
Any ideas how to fix?
Thanks!

---

### Post by mdmcginn on 2008-05-10
Does [http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195) look helpful to you?

---

### Post by epidemiks on 2008-05-23
no joy.. any other advice?

---

