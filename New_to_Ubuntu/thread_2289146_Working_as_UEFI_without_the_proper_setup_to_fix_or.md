---
title: "Working as UEFI without the proper setup: to fix or not to fix?"
date: 2015-08-01
forum: New to Ubuntu
---

### Post by jjmgray on 2015-08-01
**S**ome background:
So a while back I tried to dual-boot Windows 7 and Ubuntu on separate disks.
I screwed the initial installation and only managed to get back into Windows successfully by unplugging the disk with Ubuntu on it and then using a restore point.
Getting it back up and running was never a priority so it's been sitting there for a while.
Finally decided to try and give it another shot today.

I plug the HDD with Ubuntu on it back in, lo and behold the system boots with GRUB displaying both Linux and Windows. 

Being cautiously optimistic I logged in and started poking around, and so I'm still a little concerned due to not meeting a certain part of this article: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI).

Terminal commands from said article assert that I am running "EFI boot on HDD" and I am "Installed in UEFI mode." Presumably this means the firmware is properly set up, though I haven't gone into the BIOS yet to check that.

**T**he issue:
My main concern though is that I don't seem to have an efi partition (ESP), so I'm worried that it's going to break again (if it's not already and I just haven't noticed).
[According to GParted I just have a regular /boot, and it's in ext4, not FAT32.]("http://i.imgur.com/VUcKXbM.png")
Also, fdisk -l tells me that the second partition isn't starting at the physical boundary size. Another thing I'm not sure I want to try fixing.

So . . . yeah. Not sure where to go from here. 
I mean it seems to be working, so should I just leave it all alone and call it good?
Any advice is appreciated.

---

### Post by oldfred on 2015-08-01
If you want to know details of install:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Most Windows 7 installs were BIOS with MBR(msdos) partitioning, even some newer hardware that was UEFI capable.
Windows only boots in UEFI mode from gpt partitioned drives.
And you can only dual boot from grub menu if both installs are in same boot mode.

---

