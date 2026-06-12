---
title: "Unable to select ubuntu as OS"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Chapeen on 2008-08-14
I did an update of my windows vista from Home version to Ultimate versio, when I did so, I don't have the choice to choose the OS I want to use, it automatically goes to windows vista, but I know Ubuntu still installed.

---

### Post by Riffer on 2008-08-14
The Vista update rewrote your MBR (master boot record).  If you get a program called SuperGrub you should be able to fix it.

[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

On ther right hand side is where you download it from.

---

### Post by erfahren on 2008-08-14
> **Chapeen said:**
> I did an update of my windows vista from Home version to Ultimate versio, when I did so, I don't have the choice to choose the OS I want to use, it automatically goes to windows vista, but I know Ubuntu still installed.
you just need to restore GRUB - you can use the Ubuntu LiveCD to do it
see the first section here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Riffer on 2008-08-14
> **erfahren said:**
> you just need to restore GRUB - you can use the Ubuntu LiveCD to do it
see the first section here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Cool learn something every day.

---

### Post by BGFG on 2008-08-15
You can also add GRUB to the Vista bootloader using EasyBCD

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

