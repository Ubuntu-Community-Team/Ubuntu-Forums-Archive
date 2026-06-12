---
title: "Remove Xubuntu on a Windows XP PC"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by Manshi on 2012-08-23
Hello,

I tried:
a) running disk management on Windows XP. There, I deleted all the partitions that Windows stated was unknown and did not belong to it. However, then I got some black screen saying "grub, no partition" when I tried rebooting my PC.

b) running the installation CD for Xubuntu, but it clearly does not have an "Uninstall" option. 

Then, I reinstalled Xubuntu and I no longer had that "grub, no partition" problem. I can still run my Windows XP. However, I would like to completely remove Xubuntu. How may I do so?

---

### Post by Lisiano on 2012-08-23
You will need to boot from your Windows XP install disk and start the Recovery Console, from there you will need to enter this
```
fixmbr
```
After that, you can safely delete Ubuntu from inside Windows.

---

### Post by terry_gardener on 2012-08-23
[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/]("http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/")

---

