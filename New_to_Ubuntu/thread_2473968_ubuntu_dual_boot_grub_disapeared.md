---
title: "ubuntu dual boot grub disapeared"
date: 2022-04-19
forum: New to Ubuntu
---

### Post by thatim on 2022-04-19
hello the community, i deleted a partition on my ubuntu hard drive by mistake , i'm running both ubuntu and windows 10 each on it's hard drive.
i rebooted ubuntu today and i have no more the grub menu here is the report 
[https://paste.ubuntu.com/p/rmDjmybF3y/](https://paste.ubuntu.com/p/rmDjmybF3y/)
please help me

---

### Post by oldfred on 2022-04-19
Only use live installer in UEFI mode, you booted it in BIOS/CSM/Legacy mode.
Repairs are made in the mode you boot repair disks for both Windows & Ubuntu. You have UEFI system & installs.

It looks like you deleted your ESP - efi system partition on sda1.
And recreated it as fAT16 when it should be FAT32, even though FAT16 may work. UEFI allowed FAT16 for tiny devices.
And now ESP has no boot files.
Your Ubuntu fstab showed in comments that it was using ESP on sda1.

You can reset sda1 to FAT32, reinstall grub in UEFI mode & reinstall Windows boot files in UEFI mode.
Not sure if testdisk may find & restore partition? You could check that first if desired.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

