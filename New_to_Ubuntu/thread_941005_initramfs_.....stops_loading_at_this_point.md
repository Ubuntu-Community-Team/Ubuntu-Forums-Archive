---
title: "initramfs .....stops loading at this point"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Michael Prescott on 2008-10-07
Hi

Have install 8.04.1 LTS desktop edition, after loading from the hardisk, directory initramfs is displayed.

Tried using the cmd line /var/log/Xorg.0.log  to find out why Ubuntu is not booting. A suggestion from a software guy at work.

Unfortunately   "not found" is displayed.

73's,


Mike

---

### Post by spiderbatdad on 2008-10-07
a couple of things to try. 1.)Clear the cmos...unplug power cable and remove battery for 15 minutes or so, or use mobo jumper. 2.)Try booting with the option all_generic_ide by pressing f6 from the startup menu or by editing the kernel by pressing e from the grub menu, then move to kernel line and press e again. Delete quiet splash from the end of the line and type in all_generic_ide. Hit enter and press b. If this works you will need to edit /boot/grub/menu.lst to make the edit permanent.

---

