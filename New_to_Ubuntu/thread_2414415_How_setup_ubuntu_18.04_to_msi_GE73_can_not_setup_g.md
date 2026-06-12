---
title: "How setup ubuntu 18.04 to msi GE73? can not setup grub."
date: 2019-03-10
forum: New to Ubuntu
---

### Post by aaa71 on 2019-03-10
Hi
my msi:
1 ssd (128gb) whith win10 (gpt)
2 hdd partitions EFI and partition for disk D,  (gpt)
UEFI boot. Secure boot -off, fast boot(in windows)-off.

I add partition to ssd (26gb) and use it as "/" during installation + EFI(on hdd) as Efi.
 
Grub install device SSD (i try hdd too). but "can not setup grab to target"

Can you help?

---

### Post by oldfred on 2019-03-10
Grub wants to install to ESP on first drive. If SSD seen as sda, then you will need an ESP - efi system partition on SSD as FAT32.

I have multiple test installs on sdb & various flash drives. Every time it overwrites my main working install's /EFI/ubuntu entry on sda. I just learned to backup entire ESP on sda, but now just edit /EFI/ubuntu/grub.cfg to point to main working install. I just installed 19.04 to see if updates to grub would allow me to select ESP on sdb. It does not, even though during install it says it is installing to the drive I have as sdb.

---

### Post by oldrocker99 on 2019-03-11
My consistent experience has been that if the installation is in UEFI mode, grub will **not** install, leaving an unbootable system. Using Legacy mode, all is well. Try that.

---

### Post by oldfred on 2019-03-11
Many users have installed in UEFI boot mode both with UEFI Secure boot on or off.
But a few vendors have UEFI implementations that do not really follow UEFI standards that should let Ubuntu install without issue. And then the CSM/legacy/BIOS boot usually does work.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

