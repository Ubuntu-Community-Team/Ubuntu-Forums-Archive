---
title: "No ubuntu option in windows bootloader"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by zain6267 on 2012-08-12
Hi,
     This is my first time installing ubuntu, and I am trying to install it on an external hard drive. After I installed ubuntu onto my external hard drive using the live cd I rebooted the computer, and while the menu showed up the only option listed was 'windows 7'. I have tried  ```
sudo grub-install
``` and other things like this but cannot get the option to show up, even though linux has reported to have reinstalled GRUB. Is there any way to get the ubuntu option to show up or the grub menu to appear?

---

### Post by drs305 on 2012-08-12
zain6267

Welcome to the Ubuntu Forums.  :-)

First, you may have to change the BIOS boot order so that the computer boots the drive with Ubuntu on it first. 

If that doesn't boot to the Grub menu, boot a LiveCD, install Boot Repair, and select the "Recommended repair" button. If it still doesn't boot Ubuntu, run the boot info script from Boot Repair and post the contents. The information will let us give you specific commands to help allow Grub to control the boot.

A link to the Boot Repair page is in my signature.

---

