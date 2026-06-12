---
title: "Ubuntu boot menu"
date: 2014-10-09
forum: New to Ubuntu
---

### Post by kccv42 on 2014-10-09
How do i boot to Ubuntu automatically without having to choose it in the options which includes ubuntu recovery mode and other ones. In the boot edit menu, you have to put some coding in which i dont know. Please help. Thanks.

---

### Post by Vladlenin5000 on 2014-10-09
Hi, welcome.

In a dual-boot scenario you want GRUB to be shown in order to be able to select the OS to run.
When Ubuntu is the only OS then GRUB usually isn't shown. Anyway, even if it is shown, usually the default is always Ubuntu and it boots immediately after the GRUB's countdown is finished. How exactly do you "have to choose"??

---

### Post by Paulgirardin on 2014-10-09
You can install Grub Customiser and set it the way you prefer.
[ [http://ubuntuhandbook.org/index.php/2014/04/install-grub-customizer-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/04/install-grub-customizer-ubuntu-1404/) ]("http:// http://ubuntuhandbook.org/index.php/2014/04/install-grub-customizer-ubuntu-1404/")

---

### Post by grahammechanical on 2014-10-09
Grub Customizer will let you reduce the time-out down from 10 seconds but do not it set to zero. There may come a time when you need to access the boot menu to run recovery mode and with the time-out set to zero it becomes very difficult to access the boot menu.

Regards.

---

### Post by kccv42 on 2014-10-10
It has me choose either ubuntu or ubuntu recovery mode. After a certain amount of seconds it automatically chooses Ubuntu. Hope that helps.

---

### Post by Vladlenin5000 on 2014-10-10
The posts above already provide a workaround.

---

