---
title: "reinstall ubuntu with larger partition"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by tristanwalker44 on 2014-04-04
i have Ubuntu installed on one of my 2 1tb hard drives.  it is dual booted with win 7 in one and the other has a non working copy of win 8 and 30gb partition for ubuntu.  i spend most of my time in Ubuntu, as i prefer that.  i want to allocate about 700gb for Ubuntu and about 300gb left so i can use it for backups and such.  what is the best way to do this, without messing up my boot sequence.  if its necessary to redue all that then best way to set up a new grub (i think thats what its called when it tells me what i want to boot into).  i am savvy on the hardware section on comps as i built mine, do ok on the software set up, but obv am no expert on either.  thanks for any advice possible.  i already tried to resize in gparted, but the un-allocated space i couldnt give to Ubuntu for some reason, i think because the swap was inbetween them?

---

### Post by bshatt1987 on 2014-04-04
To resize a partition it needs to not be mounted.  So if you were trying  to resize the partition that you had booted from it won't let you  because it would be mounted.  
The best way would probably be to do it from a live session of Ubuntu from DVD or USB and then use GParted.    
If  all you want is to make the existing partition bigger then you  shouldn't mess up your boot sequence, but if you are going to reinstall  to the newly resized partition then the newly installed Ubuntu would be  chosen to boot first.

---

### Post by tristanwalker44 on 2014-04-04
so grab a live cd with 13.10 on it and install gparted on that, or will it be installed, then use it to resize.  when dvd is in drive do i boot up comp with the dvd in and boot into that, then use gparted to resize.  also when i do so i have a hacked unworking copy of win 8 installed, can i resize my ubuntu to what i want, then wipe the rest of the drive out so it can be used for back ups only?

---

### Post by bshatt1987 on 2014-04-04
GParted should be included in the Live DVD.  And yeah, boot the computer up with the DVD in the drive (make sure your BIOS will boot it automatically or else hit whatever button you need to to select the boot device).  When the menu for the Ubuntu DVD comes up, go to the Try Ubuntu Without Installing and it will start the live session.  Then you should be able to find GParted in the Dash.  
If you don't want to keep the Windows 8 files then you can just delete that partition, resize the Ubuntu partition, then reformat what you want for backup to probably FAT32.  At least I would choose FAT32.

---

### Post by tristanwalker44 on 2014-04-04
thanks man will try tomorrow evening when i have free time and report back... i appreciate the advice.

---

### Post by bshatt1987 on 2014-04-04
You're welcome and good luck.  :3

Also, I'm sure it goes without saying, but if you've got any important files on the drive where you'll be partitioning, you should probably back them up somewhere else.  It's not a terribly risky procedure but you never know what could happen.  lol.

---

### Post by oldfred on 2014-04-04
With 2 drives best to use Something Else or manual install. You want to leave the Windows boot load on the Windows drive and have grub boot loader on the Ubuntu drive. Then if the Ubuntu drive does not work you can reset BIOS to directly boot Windows.

       Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

I do prefer a smaller root partition and larger data partition(s). But it is more work to set up data partitions. You can have a smaller / of  20 or 25GB and large /home as part of the install. But cannot directly create & mount data partitions during install.

---

### Post by Impavidus on 2014-04-05
To give more specific advice we need to know the layout of the partitions of your disk.```
sudo parted -l
```

I wouldn't use fat32 partitions, except on smaller usb drives. If you only need access from Ubuntu, use ext4. There are some other options, but ext4 is OK. If you also (or only) need access from Windows, use NTFS.

---

