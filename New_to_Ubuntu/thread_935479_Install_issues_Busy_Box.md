---
title: "Install issues Busy Box"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by snipethewolf on 2008-10-01
From what I have found searching the forum busy box is loaded on install when there is an issue with the disc or hardware.


I have checked the disc, and also reburned/dled and rechecked another disc to make sure the issue is not with the disc.


What might cuase busy box to load when I try to install Hardy? It also loads when I try to boot to the live desktop or any other option I can find.


Please any help would be great!

---

### Post by spiderbatdad on 2008-10-01
maybe try to clear your cmos with the onboard jumper or, if lappy, power down and remove battery for a bit. Do you have windows installed, and was there an improper shutdown?

---

### Post by ModelM on 2008-10-01
Try adding```
all_generic_ide

```to the kernel options at boot.

---

### Post by snipethewolf on 2008-10-02
I tried the CMOS idea and just updated the BIOS of the mobo as well. How do I go about adding the code to the boot? Im still fairly new to linux when it comes to well doing anything.

If it makes a difference I have had issues with the RAM im running in the system. The HDD and CD-Rom are on Sata not IDE if that makes a difference as well.

---

### Post by ModelM on 2008-10-02
Have a look at "1. Changing Boot Parameters Temporarily" on [_this web page](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)_.

---

