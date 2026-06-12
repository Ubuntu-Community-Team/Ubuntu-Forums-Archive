---
title: "Grub Basic Troubleshooting Checkpoints/Flow Chart"
date: 2009-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by meka4996 on 2009-05-25
Grub Basic Troubleshooting Step by Step procedure
 Checkpoints/Flow Chart
recover/restore/repair wiped/erased/overwritten Grub

--Checkpoint 1: Can you boot into Grub? (including seeing menu or not)
If yes, go to "Checkpoint 2"
If no, choose either Case1 or Case2

Case1. Grub installed on MasterBootRecord[MBR] has been wiped out by another Linux or M$ Wind0ws
see reference: How to restore Grub from a live Ubuntu cd [using "find-root-setup" method]
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+troubleshoot](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+troubleshoot)
Note: ALWAYS use "SUDO grub", forgetting "sudo" will cause problems...

Case2. Grub has not been properly installed 
something like ubuntu 8.10  ubiquity crashed with InstallStepError in configure_bootloader()
reference: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/260001](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/260001) 
then go to "installing grub from LiveCD" section below [using "grub-install" method]

note: grub-install refresh all files inside /boot, except menu.lst and device.map
so you need to find those two files first...
See attached menu.lst file, and here is my device.map file of Ubuntu 8.10 inside /boot/grub
(fd0)	/dev/fd0
(hd0)	/dev/sda
[or by copying them from /boot/grub of an already installed linux]
[or use grub to generate device.map file only >_< see ...
[http://www.gnu.org/software/grub/manual/html_node/Device-map.html](http://www.gnu.org/software/grub/manual/html_node/Device-map.html)
 
--Checkpoint 2: Inside Grub, can you see a Grub menu?
If yes, go to "Checkpoint 3"
If no, search online for the menu.lst file for your linux version, 
then modify its entries ... see "Checkpoint 3"
then copy it into /boot/grub

--Checkpoint 3: Can you boot into the linux from the Grub menu?
If yes, Congratulations! You are done!
If no, 
modify entries manually, by first trying a few times using
"How To Boot Linux from GRUB's CLI" [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
... and find the uuid by...
```
$ sudo blkid 
```
or
```
$ sudo grub
```   
```
$ grub> uuid
```
or install another linux first, then use "update-grub" to update the menu
see more: [http://linux-hardcore.com/index.php?topic=1712.0](http://linux-hardcore.com/index.php?topic=1712.0)

"installing grub from LiveCD"
reference: [http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/](http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/)
Choose a linux LiveCD ...
Boot the linux Live CD, open a Terminal
```
$ sudo mkdir /mnt/linux1
```
```
$ sudo mount -t ext3 /dev/sda12  /mnt/linux1
```

...if /boot partition exists at sda5, do the following line as well
```
$ sudo mount -t ext3 /dev/sda5  /mnt/linux1/boot
``` 
[your partitions may not be sda12 and sda5 ]
(later you can use umount: ```
$ sudo umount /dev/sda12
``` )
then
```
$ sudo grub-install /dev/sda --root-directory=/mnt/linux1
```
 make sure you use two dashes in front of root-directory. 
Note: /dev/sda not /dev/sda12 because of installing into MBR
 
Other references: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
Have fun =)

---

### Post by meka4996 on 2009-06-10
Related Topic: Moving from Dual Boot to Multi boot
see this in the tutorial sections,...
[http://ubuntuforums.org/showthread.php?t=1169648](http://ubuntuforums.org/showthread.php?t=1169648)

---

