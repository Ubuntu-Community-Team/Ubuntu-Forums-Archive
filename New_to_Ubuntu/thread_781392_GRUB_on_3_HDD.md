---
title: "GRUB on 3 HDD"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by bjstabio on 2008-05-04
I want to install 3 different distros of linux to 3 different hard drives.  I'm not sure how to do this and have GRUB able to boot all 3.  On my last installation with 2 hard drives, I could only boot with the assistance of SuperGRUB, otherwise I would get an Error 15.  Any advise appreciated.  Thanks.

---

### Post by bobnutfield on 2008-05-04
This is pretty easy to do, but each distro will try to install it's own grub to the MBR.  You can deny them the ability to do this during the installation and edit the menu.lst file of the distro of your choice.  For example, I have five distros on two hard drives, and all of them boot from the menu.lst from PCLinuxOS (as well as WinXP).

Just install your first distro and use it's menu.lst to boot the others.

---

