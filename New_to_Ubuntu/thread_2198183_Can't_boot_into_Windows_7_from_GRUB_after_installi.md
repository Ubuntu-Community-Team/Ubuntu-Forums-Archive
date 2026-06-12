---
title: "Can't boot into Windows 7 from GRUB after installing Ubuntu 13.10"
date: 2014-01-07
forum: New to Ubuntu
---

### Post by jason.anggada on 2014-01-07
From Boot Repair: [http://paste.ubuntu.com/6709403/](http://paste.ubuntu.com/6709403/)

I wanted to do a Dual Boot of Windows 7 and Ubuntu 13.10.
I installed Ubuntu using DVD and chose "Install Ubuntu alongside Windows7".

After installation...
GRUB displays Windows 7, but after choosing it, the screen went black for 2 seconds, and then it went back to the GRUB screen again.

So right now I couldn't boot into my Windows 7.

I tried using Boot Repair with recommended settings and it gave me these messages.

> 
Please repair the bootsector of the sda1 partition. This can be performed via tools such as TestDisk.
([https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix))


sda1 is the location of Windows 7. The Ubuntu is located in sda5 (ext4).

> The boot files of [The OS now in use - Ubuntu 13.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


And this is the log: [http://paste.ubuntu.com/6709403/](http://paste.ubuntu.com/6709403/)

Is there anything I can do to fix this? Thank you.

---

### Post by oldfred on 2014-01-07
Boot-Repair tells you that you have grub installed to the PBR or partition boot sector of the NTFS partition. Windows has boot code there, so that is why Windows will not boot.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

I think this is the linke Boot-Repair gave since it is the same author.
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Only some BIOS have issues with the boot files far from start of disk. If you can boot Ubuntu that is not an issue. Often is is grub saying partition does not exist when it really does, although other issues may give similar errors.

---

### Post by jason.anggada on 2014-01-07
Thanks for your help!
But now I'm still confused about a few things...

Contrary to the example given, it says that my Boot Sector is OK but my Backup Boot Sector is Bad.
Is it safe to do the Backup BS?

Also, I didn't make a 'system reserved' partition.
Is it going to cause any problems to the booting?

Thanks again. :)

---

### Post by jason.anggada on 2014-01-08
I'm sorry for double-posting.

Current Log: [http://paste.ubuntu.com/6713647/](http://paste.ubuntu.com/6713647/)

Now choosing the Windows 7 would lead me to a black screen with blinking cursor.

Any suggestions to fix this? Thank you. :)

---

### Post by oldfred on 2014-01-08
Did you restore the backup?

If backup was not good, you still need to run repairs from a Windows repairCD or flash drive. But it now shows a Windows PBR, so Windows repairs should work. When grub is in PBR Windows will not recongize partition and run repairs. It may need fixboot and probably needs chkdsk  Windows repairs.

My understanding is that Windows has system reserved so you can boot main install if encrypted. Boot files cannot be encrypted. Also it does have the recovery/repair files and sometimes you can use them to fix main install. But if you have a separate repair CD or flash drive, you can run repairs from that. So system reserved not required.

---

### Post by jason.anggada on 2014-01-09
I have tried to restore the backup, now both the boot sector and the backup boot sector is OK.
I have tried doing fixboot and chkdsk but it says that there are no problems with it.
But still I'm having the same problem of Windows 7 not loading and giving me a black screen after choosing it from GRUB.
Then, I'm trying to do a system recovery, but it says that my DVD is not the same version as the Windows 7 inside my laptop.

I'd like to ask if there are any errors in the current boot repair log.
[http://paste.ubuntu.com/6719528/](http://paste.ubuntu.com/6719528/)

 Or there are no more problems detected by boot repair and the booting should be normal?
Thanks again, sorry the trouble. :)

---

### Post by jason.anggada on 2014-01-09
Finally it's fixed!
I tried doing this in the GRUB section: [http://unix.stackexchange.com/questions/38469/where-can-i-learn-more-about-how-to-use-the-grub-ntldr-command-module](http://unix.stackexchange.com/questions/38469/where-can-i-learn-more-about-how-to-use-the-grub-ntldr-command-module)
I added insmod ntldr and change chainloader +1 to ntldr ($root)/bootmgr, and it works wonders!
Although this might make the Windows depend on Ubuntu and I won't be able to uninstall Ubuntu, but it's OK.
Thanks for the help, oldfred! You really help me out and motivate me to fix this problem! :D

---

### Post by oldfred on 2014-01-09
Glad you found solution. 
I have seen that as an alternative before, but not sure of diffence. ntldr is the XP boot loader. bootmgr is Vista and later boot manager and as I understand grub just jumps to the Windows PBR to boot in the same way the Windows MBR jumps to the PBR.

You can always restore a Windows boot loader to the MBR to directly boot Windows. You can use your Windows repairCD/flash drive or use Boot-Repair which adds a generic Windows boot loader. But a Windows boot loader will not let you boot Ubuntu, but sometimes useful to test whether grub issue or Windows boot issue.

---

