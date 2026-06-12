---
title: "[SOLVED] GRUB 21 Error Dual Boot"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by The_Shady_1 on 2008-06-05
I was dual booting Ubuntu on separate drives.SDA for WinXp,SDB for Ubuntu with an NTFS partition as backup for SDA.I booted up LiveCD for Ubuntu and deleted Ubuntu from SDB leaving only the NTFS partition.I unplugged SDB attempting to boot into WinXp from SDA and I get GRUB error 21.I am able to see my data is still intact but I am unable to boot XP.I am not leaving Ubuntu and I do plan to reinstall.How can I boot into XP ?Something just went whacko on Ubuntu so I just deleted it and want to start from a fresh install.

---

### Post by Duck2006 on 2008-06-05
Boot up with the XP cd and got to recover mode. In recover mode at the promp type.

fixmbr

reboot and you should boot in to XP. Then reinstall ubuntu or just grub. This may help on reinstalling grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by The_Shady_1 on 2008-06-05
Thank You Duck2006 !

---

