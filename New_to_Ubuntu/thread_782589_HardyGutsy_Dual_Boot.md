---
title: "Hardy/Gutsy Dual Boot"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by thewhiteraven on 2008-05-05
I'm an absolute absolute beginner so forgive me if I don't make sense... But here's the problem...

My laptop had Gutsy Gibbon on it and then I downloaded Hardy and installed it... Now my laptop has both versions and I don't know how to uninstall gutsy because both seem to be installed in the same root partition... Help!

---

### Post by Paqman on 2008-05-05
> **thewhiteraven said:**
> both seem to be installed in the same root partition... Help!

Nah, they'll have their own root partitions.

Bascially, to remove Gutsy you'll want to edit it out from /boot/grub/menu.lst and then wipe the partition that it's on.

---

