---
title: "installation process"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by davidc60 on 2011-12-01
Hi,
I have a completely spare and empty drive on my HDD (currently formatted as NTFS). I wonder whether it is possible to install several Linux-related operating systems onto that one drive but place the MBR's for them (Grub2?) onto a USB and adjust the BIOS to boot from the USB so that it would then be possible to select one of a number of OS's from the menu at boot-up? If it is, can Linux distros cope with NTFS or would the empy drive on my HDD have to be formatted as Ext4?
Thanks, 
davidc

---

### Post by carverj on 2011-12-01
Does it have to be loaded from USB or will CD do?
I use a Super Grub CD and think it is great: - [www.supergrub.org](www.supergrub.org)
Linux can work with NTFS

---

### Post by mastablasta on 2011-12-01
> **davidc60 said:**
> Hi,
I have a completely spare and empty drive on my HDD (currently formatted as NTFS). I wonder whether it is possible to install several Linux-related operating systems onto that one drive but place the MBR's for them (Grub2?) onto a USB and adjust the BIOS to boot from the USB so that it would then be possible to select one of a number of OS's from the menu at boot-up? If it is, can Linux distros cope with NTFS or would the empy drive on my HDD have to be formatted as Ext4?
Thanks, 
davidc
 
 
it is possible, but the quesaiton is why do you want to do that? Is it an experiment?

---

### Post by davidc60 on 2011-12-03
Hi, 
Thanks to carverj and Mastablasta for your replies.
Yes, it does have to be an USB - I only have a netbook with no CD drive.
Yes, it is just an experiment to see what may work and what doesn't. At the moment I have a completely empty 'D' drive (over 100gb) and I simply wondered if I could fill it with several Linux distros and place the MBR on to an USB (ie. in order to keep the booting process away from Windows (on 'C')).
(Incidentally, I have since read elsewhere that Unix cannot be installed on a NTFS formatted drive).
Thanks,
davidc

---

### Post by carverj on 2011-12-05
Grub is great as it allows you to boot linux and non-linux partitions (such as Windows). So if you have a machine with a Windows partition at the start of the hard drive, and then some spare space after that you can install any flavour of linux to this free space. During the Ubuntu linux install, you will get the option to install Grub to the MBR and this will allow you to dual boot to either Windows or linux.
If this will not surfice and a USB must be involved, I have not tried that way I am sorry so can't be much help there. I had a hunt online but could not find any help for doing that way.
Good luck

> (Incidentally, I have since read elsewhere that Unix cannot be installed on a NTFS formatted drive).


When you install a linux/unix operating system to the hard drive, it will ask you to format the spare free partition to the filesystem of your choosing. I go with ext3/4 and there are other options as well.
When I say linux can work with NTFS, I mean that when you boot into your new linux partition for the first time, it should have already mounted your Windows partition and you can access and work with the data on that.

---

