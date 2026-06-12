---
title: "Ubuntu mate not booting after uninstalling Windows"
date: 2016-04-21
forum: New to Ubuntu
---

### Post by ane242 on 2016-04-21
Can anyone please help.
 
 I am a newbie to Linux/Ubuntu and brought a new build laptop with 'no operating' system so that I could install Ubuntu Mate.  When I first turned the laptop on it booted into a Windows 10 screen (although nothing there as I hadn't brought the software).  The supplier explained they had put on Windows 10 to test the laptop.
 
 I installed Ubuntu Mate 15.10 as a dual boot thinking it might be useful to keep Windows in case need to dual boot in the future (this was before I since found out about Virtual machines).  I have been using the laptop for a couple of months but recently started to get messages that disk space running out.  When I looked in Gparted it showed that a windows partition was taking up about 90GB of my 120GB hard drive with only about 10GB assigned to Ubuntu so I decided to uninstall Windows using **OS-Uninstaller **but got error message (please see attached screenshot).When I looked in Gparted all the windows partitions were still there and using the same amount of hard drive space so I assumed OS-Uninstaller had failed in the uninstall of Windows so I deleted the windows partitions in GP parted.

 The laptop is now unable to boot into Ubuntu.
 
 I have spent 3 days trying to fix the problem (including using Boot-Repair) and now understand (or think I understand) that I should not have deleted the windows EFI partition as that is where ubuntu was boot loading.  I tried changing the boot manager from EFI to BIOS but ubuntu still not booting.
 
 I had saved my working files but did not create a disk image backup so cannot restore everything to what it was before.  I do not want to reinstall ubuntu as I will lose all the software I installed (which took hours/days to install as I am new to Linux) and most importantly don't want to lose all my search engine history and bookmarks as urgently need it for my work.

 Can anyone help me to get the Ubuntu on my hard drive to boot?  Here is a link to the boot info [http://paste.ubuntu.com/15959459/](http://paste.ubuntu.com/15959459/)
 
 If it helps:
 sda is the hard drive
 sdb is the ubuntu mate 15.10 live usb
 sdc & sdd are usbs (data files – no operating systems on them)

---

### Post by oldrocker99 on 2016-04-21
If you've removed Windows, reinstall with the first (erase disk and install) option. That should rectify your problem.

---

### Post by yancek on 2016-04-21
If you have data on the computer you want to keep, you will need to reinstall Grub and update it.  You have a FAT32 partition at the beginning of the drive which was probably and EFI partition and then you have a small BIOS boot partition which is only used with GPT and MBR installs.  Unfortunately, you do not have any files in the EFI partition.  You need to decide which you want to use.  The link below has some info on using UEFI

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Some detailed info with multiple options for reinstalling Grub at the link below.

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by ane242 on 2016-04-23
> **yancek said:**
> If you have data on the computer you want to keep, you will need to reinstall Grub and update it.  You have a FAT32 partition at the beginning of the drive which was probably and EFI partition and then you have a small BIOS boot partition which is only used with GPT and MBR installs.  Unfortunately, you do not have any files in the EFI partition.  You need to decide which you want to use.  The link below has some info on using UEFI

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Some detailed info with multiple options for reinstalling Grub at the link below.

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

Thank you both for replying.

I am very very very pleased to say that thanks to yancek's advice to go to link on reinstalling GRUB 2 I used** Boot-Repair **to purge and reinstall GRUB 2 then set boot to BIOS and I am now back in the originally installed Ubuntu Mate and can see all my bookmarks, browsing history and all the software installed over the last 2 months.

If it is of interest here is the link to the repaired boot info [http://paste.ubuntu.com/15999383](http://paste.ubuntu.com/15999383)

---

