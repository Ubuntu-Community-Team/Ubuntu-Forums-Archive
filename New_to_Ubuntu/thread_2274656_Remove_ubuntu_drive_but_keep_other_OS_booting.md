---
title: "Remove ubuntu drive but keep other OS booting"
date: 2015-04-21
forum: New to Ubuntu
---

### Post by Anonymous_Human on 2015-04-21
I have a system with two separate physical hard drives where linux is on one and windows on the other. At boot time I get a menu to choose my OS. What I want to do is take the linux drive out so I can put it in another machine. When I take it out, my system won't even boot windows from the other drive because I think the boot loader menu is on the linux drive (which I took out). Any way to fix this so I can safely take out my linux drive and still have the system booting into windows from the other drive? More specifically, any way to do this without having to re-install either OS?

---

### Post by yancek on 2015-04-21
Your description indicates that it is likely that you are using the Linux Grub bootloader to boot both Linux and windows and that you have some boot code in the master boot record of the first (windows) drive and the rest of the boot files on the second (Linux) drive.  You need a windows installation CD and select the repair option when you boot it to repair the mbr.  That should work unless you don't have the windows media or if you have UEFI.  Which version of windows do you have?

---

### Post by oldfred on 2015-04-21
In addition, you want to install grub to the sdb drive, so that drive can boot.
Again whether UEFI or BIOS is a major issue.

If BIOS you just install grub to the MBR to sdb, but may also need to update the drive it will reinstall on major updates as that may be wrong drive.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 


 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

If you just want grub in sdb, it can be just this:
      sudo grub-install /dev/sdb

If a newer UEFI system post back.

---

