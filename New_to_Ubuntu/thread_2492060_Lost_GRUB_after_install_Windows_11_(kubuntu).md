---
title: "Lost GRUB after install Windows 11 (kubuntu)"
date: 2023-10-29
forum: New to Ubuntu
---

### Post by goldfran on 2023-10-29
Hi

I have an Intel NUC 11 Esential NUC11ATKPE and had install Kubuntu and Windows 10.

I install windows 11 and grub boot loader was lost... so I can´t run kubuntu... 

I try to create grub boot repair disk but doen´t run (create with Rufus)

I try to use Kubuntu liveUSB to repair grub but ... I don´t know

Can you help me anyone?

---

### Post by kc1di on 2023-10-29
Usually Windows will overwrite the boot sector when ever it upgrades.  You will have to reinstall grub here's how.
[https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition]("https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition") 
look at # 154.  good luck.

---

### Post by yancek on 2023-10-29
You can boot the Kubuntu install usb and download boot repair from it and run boot repair ONLY with the  Create BootInfo Summary option.  At the boot repair site from the link below, when booted into the Kubuntu install USB, select the 2nd option shown on that page.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It is likely that Kubuntu is still there and windows just set itself to first in the boot options.  Windows 10 is probably an EFI install so go into the BIOS and look for Boot, boot options and look for a Boot Order or OS Boot Manager option or something similar.  You should be able to set Kubuntu to first priority there.  If you can do this and boot Kubuntu then update Grub as suggested in the post above.

---

