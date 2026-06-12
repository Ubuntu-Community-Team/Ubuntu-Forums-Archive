---
title: "boot repair error"
date: 2014-10-11
forum: New to Ubuntu
---

### Post by Choong_Zheng_Yang on 2014-10-11
after attempting to reinstall ubuntu, on ubuntu from a live usb, got a grub error where grub menu doesn't appear

followed steps in boot repair, error message in link below

[http://paste.ubuntu.com/8538631/](http://paste.ubuntu.com/8538631/)

assistance greatly appreciated

thank you.

---

### Post by kc1di on 2014-10-11
HI Choong_Zheng_Yang and Welcome to Ubuntu,

what type of machine are you installing on?  That may make a difference in how to fix it.

---

### Post by oldfred on 2014-10-11
Also what video card/chip your system has.

With just Ubuntu installed you may be booting but have video issues.

If not booting it may be a UEFI issue with your brand/model system. Some only boot Windows.

With only Ubuntu installed, you do not normally get grub menu, you have to use escape key at UEFI menu to get grub menu

Grub reinstalled correctly, Boot-Repair does pick up some misc errors that are not related and puts those in its summary. Error code 0 is no errors.

 Reinstall the GRUB of sda2 into the MBR of sda
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

---

