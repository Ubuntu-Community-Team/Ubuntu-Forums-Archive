---
title: "Installation help"
date: 2016-07-25
forum: New to Ubuntu
---

### Post by jachin99 on 2016-07-25
I'm trying out Linux because I'm an it guy looking to learn as much as possible.  I still need to use windows so I would like a dual boot configuration.  I created a kubuntu live USB by downloading the iso directly from the official Ubuntu site and I created install media using rufus.  I can get my machine to boot up from USB each time and upon starting my pc I am proper to choose which os I would like.  I also created a separate partition on my ssd and moved the same rufus install media onto it but I cannot access that partition on startup.  This partition also has my windows os on it.  How would I boot up the machine and Inot all Ubuntu on my permanent ssd.

Additionally, when I boot inot Ubuntu on mY removable media I cannot get to an option to to next my only keyboard, a Bluetooth one, to linux.  How do I fix these issues.  Thanks

---

### Post by yancek on 2016-07-25
Your post is not clear.  Did you just put the Kubuntu Live/Install system on a flash drive with rufus and have booted that, OR have you done that and also installed to your SSD or hard drive.  Also, mirosoft has been writing operating systems for 35 years and it would be useful to know which you are using as some very major changes have been made in recent versions.

Why would you move the Kubuntu install media to your SSD if you already have it on a usb?

---

### Post by mastablasta on 2016-07-26
> **jachin99 said:**
> I'm trying out Linux because I'm an it guy looking to learn as much as possible.  I still need to use windows so I would like a dual boot configuration.  I created a kubuntu live USB by downloading the iso directly from the official Ubuntu site and I created install media using rufus.  I can get my machine to boot up from USB each time and upon starting my pc I am proper to choose which os I would like.  I also created a separate partition on my ssd and moved the same rufus install media onto it but I cannot access that partition on startup.  This partition also has my windows os on it.  How would I boot up the machine and Inot all Ubuntu on my permanent ssd.

you left out many important details. : [SIZE=2]https://ubuntuforums.org/showthread.php?t=1422475
[/SIZE]
Does the motherboard haveUEFI or BIOS ?


i don't know about rufus, but normally i would use linuxliveusb or yumi (there are more) to create a USB image and boot from it. these are mean for USb flash drives. if you want a dualboot install then you need to boot the PC using USB or DVD and install on a portion of unformatted disk space which you create in advance using windows disk manager (for example). it is advised to defrag before partition moving and also to backup all files (e.g. image the disk)

if all you want to do is toy a bit with linux system then virtualbox ([http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)) or similar virtualisation is a good option
> 
Additionally, when I boot inot Ubuntu on mY removable media I cannot get to an option to to next my only keyboard, a Bluetooth one, to linux.  How do I fix these issues.  Thanks
completelly separate issue and should be in a different thread. you need drivers for that. in linux drivers are in kernel (opensource). if they are not there it means manufacturer provides them (or not). agin any kind of troubelshooting starts with some information - such as exactly which keyboard you are using. if no one created river and the manufacturer didnt' provide them then it will not work. however everyone can write their own drivers in linux. :P

---

### Post by jachin99 on 2016-07-26
Sorry for the confusion, I have kubuntu 16.0.4 and during the installation, I installed all the third party software.  My pc uses uefi and I have the Linux media creation on both a thumb drive and a separate HD partition.  I am looking to run this on the internal ssd because it has more room.  I hope this helps answer your questions.  Mgoal at this point is to run the installation media on the internal HD without losing windows, just for clarity

---

### Post by mastablasta on 2016-07-27
in other words you want to run a live session, an uninstalled os on internal HD? and dualbotoing iwndows form same HD? 

you might pull this off in MBR mode (the old BIOS mode) but i am not sure it is possible in UEFI. i haven't had any UEFI boards yet, so i am still to confront with this. but i believe UEFI requires a propper instalation, where GRUB (the boot loader ubuntu uses) will handle the OS boot. an option would be to manually install GRUB and the load the live session from it.

i am not sure why you would do that though as you could simply do a full disk install next to windows. you shouldn't loose windows as long as you partitioned the disk in the right way (a backup is helpful in case things do go wrong).


[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
[/URL]

---

### Post by jachin99 on 2016-07-27
I dont want a live cd and an os install.  I only want to dualboot windows and linux from the same internal ssd.

---

### Post by jachin99 on 2016-07-27
When i go into uefi i only see options to boot from physical disks rather than disk partitions, and the first startup option is UEFI: Ubuntu.

---

### Post by leunam12 on 2016-07-27
Maybe this guide can help you. Also many times after install you have to run boot-repair 

[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
[/URL][https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

