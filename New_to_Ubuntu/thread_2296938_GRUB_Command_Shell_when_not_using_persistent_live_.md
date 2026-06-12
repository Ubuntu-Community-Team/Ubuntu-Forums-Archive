---
title: "GRUB Command Shell when not using persistent live USB on W8.1/Ubuntu dualboot"
date: 2015-09-29
forum: New to Ubuntu
---

### Post by spite2 on 2015-09-29
Good day all,


I've looked around for quite a while but, perhaps due to me still being new to Ubuntu and not knowing the terminology well, I couldn't quite find anything to help me fix my issue.


I'll start from the beginning of the issue, and move towards the actual issue, as it might help explain what went wrong.


I'm running a dual-boot setup on my laptop (Windows 8.1 and Ubuntu 14.04.3 LTS) and this worked well, the bootloader would show up in it's simplistic GUI form and allow me to choose my windows bootloader or my Ubuntu.


As I'll be going to the US for a while, I looked into a method to have a portable Ubuntu, which wouldn't require me to install anything to my girlfriends' laptop.
Sure enough, I found out about the persistent live USB and after a lot of searching found some methods that seemed viable, leading to my current predicament.


I used this specific guide - but used the 14.04.3 LTS version instead:
[http://www.fernhilllinuxproject.com/installubuntutousbdrive.html](http://www.fernhilllinuxproject.com/installubuntutousbdrive.html)


After rebooting after everything was done, I noticed immediately that I had 2 Ubuntu distributions in my GRUB. ([http://i.imgur.com/JYEeluX.jpg](http://i.imgur.com/JYEeluX.jpg))


Now I'm used to having "*Ubuntu" be the Ubuntu on my laptop's HDD partition, however in this case it appears to be the one on my persistent live USB.




The issue arises then, when I remove the usb and try to boot up my system.


It shows the GRUB Command Shell instead of the usual GUI and a subsequent "ls" - which I used due to not understanding what was going on - came back with errors. ([http://i.imgur.com/Sm2dwLx.jpg](http://i.imgur.com/Sm2dwLx.jpg))
Using the "exit" command simply loads up Windows.


My Windows 8.1, Ubuntu on laptop, and persistent live usb all work just fine and dandy. 
However, I'd like to get the bootloader GUI back when I don't have the USB plugged in, which is the reason for this post.

One thing to keep in mind though is that, I'll need the GRUB bootloader to still load when I plug my persistent live USB into a Windows 8.1 laptop which doesn't dualboot. This due to the persistent live USB not showing in the boot menu.


I've been stuck on this for a few days already, so any help would be greatly appreciated.


Thank you in advance,


Spite

---

### Post by mastablasta on 2015-09-30
well first problem is - you are thinking you created a live USB but in fact, if you followed that guide, you:
 - installed Ubuntu to USB - it's a full install - this means if oyu plug it into another PC it might work or might now work. depends really what else you've managed to add.
- installed grub to USB and that GRUB is now used to boot your pC. if you remove the USB drive you get what you have now.

solution:
create a proper live USB disk using unetbootin or linuxliveUSB in windows. boto form it and use boot repair tools to fix grub on your dualboot PC.

while you are doing the live USB disk with one of aforementioned programs, you can tick the persistence box and this will create persistant live USB.


if you want to actually have full install on USB there are a few things to look out for:
- it is better to use USB HDD rather than USB flash drive
- use good USB drive - despite using a well rated and good quality USB drive I had a failure in about 6 months. replacement seems to be working a bit better.
- take care when creating swap partition - use swappiness command to reduce the usage of /swap partition. otherwise if you work on PC with low ram you will ruin USB drive faster.
- make sure you install grub to the disk you plan to carry around. afterwards don't do any grub updates or it will pickup and load the OS on computer hard disk - might complicate things later on

---

### Post by spite2 on 2015-09-30
Thank you for the information Mastablasta, following the advice fixed the issue with my GRUB.

The live USB, however, despite having selected persistence with the unetbootin setup, is not persistent - so I'll have to look into that, which was my primary reason for using the full install guide.

In any case, thank you very much.

---

### Post by mastablasta on 2015-10-01
try LinuxliveUSB (windows only I think) instead of unetbootin. I like LinuxliveUSB as it has this option that will add a portable virtualbox on your USB key (virtualise this key). so you can pop in the USB into a windows PC with enough ram and just run the virtualise this key or something like that and it will open your Linux live session in virtualbox.: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

persistence saves (should save) your setting and any new programs you install. the issue is that it uses some kind of virtual disk/file. now FAT32 file system has a max file limit around 2 GB I believe (so the file system can be your limit). NTFS will do better. data can be save "outside" of all this Linux stuff as normal on USB drive.

you can use full install if you wish but like I said there are a few issues with it. but you can work around them. the key is that when doing the install you need to put GRUB on USB drive. if you have a desktop you could unplug internal hard disk when installing to USB. it will be ok then. but you shouldn0t install any proprietary drivers unless the PC you plan on using later on has same hardware.

---

### Post by sudodus on 2015-10-01
The maximum file size in FAT32 is 4 GB, which limits the size of the workspace for persistence if you use a file with the name casper-rw. But if you use a partition with the label casper-rw, there is no such limit, only the size of the pendrive will decide the size of the workspace for persistence.

If you use [mkusb](https://help.ubuntu.com/community/mkusb) to create a persistent live pendrive, you can select how much of the pendrive to use for persistence (and the remaining drive space will be used as a FAT32 partition that is available for exchange of data with Windows systems).

---

