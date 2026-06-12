---
title: "Repairing NTFS disk in Ubuntu... Help!"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by shmoe010 on 2008-05-10
I have a Windows Vista installation on a 320GB SATA HDD, and suddenly said hard drive 'disappeared.' What I mean by this is that while I was in Vista, Firefox stopped responding, then the whole OS did, and the monitor went black and the PC reset itself. Upon reboot, my BIOS does not list this HDD, and consequently I cannot boot into it.

Of course, I shouldn't be using Windows at all, but unfortunately I have work-related programs that I can't get working in Wine :(. Anyway, this is the output from sudo fdisk -l:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c2885da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29576   237569188+  83  Linux
/dev/sda2           29577       30401     6626812+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb142b142

``` 

It sees my drive is attached, which means it's not a bad cable or anything. My question is whether or not I can repair this NTFS disk, and if so, what application you all would recommend. I need to preserve this data if at all possible, and if not, I have to find a way to recover it before reinstalling Winblows. I remember a college roommate fixing his "dead" HDD in linux after Partition Magic and Geek Squad both told him it was toast lol.

My Setup (because I know it helps to see what I'm working with):

Ubuntu 8.04 LTS
Opteron 165 @ 2.55 GHz
2x1GB G.Skill PC3200
1x250GB SATA HDD (Linux)
1x320GB SATA HDD (Vista)
DFI LanParty Socket 939 
PC Power&Cooling 1kW PSU
eVGA Nvidia 7800 GTX 256MB

I will be on for a while if you need me to post the output of any terminal commands or anything like that. Thank you all in advance.

---

### Post by Malta paul on 2008-05-10
Hi, I see you have two HD's on your computer, One with Windows and the other with Ubuntu.
When Ubuntu boots up it uses Grub as the boot manager and will normally give you a menu where you can select Ubuntu or Windows. I would say that grub is not recognizing your windows disk. Don't worry you have not lost your windows data. You just have to configure grub to recognize both drives.
Post back if you need more info.

---

### Post by shmoe010 on 2008-05-10
Thanks for your response.

Actually, I wasn't using the GRUB to try and get into Windows, I was in my Phoenix BIOS and I was trying to set my Windows drive as the first in the priority list so it would go straight to Vista, and that's when I saw that my BIOS does not even see the disk. At the Ubuntu GRUB, I see my Windows partition but it won't boot; it says something like drive not found.

---

### Post by hyper_ch on 2008-05-10
it doesn't recognize any partition on the second drive which is unusual....

If you can, resize the linux partition and install a windows there... most recovery tools for ntfs are based on windows... if you can't resize, buy a new harddisk... it's important to not touch the ntfs disk if possible.

---

### Post by Malta paul on 2008-05-10
Boot into Ubuntu, goto Places>Home> then click the UP arrow to go to root>Boot>grub and take a look at Menu.lst. and post back the text list.

---

