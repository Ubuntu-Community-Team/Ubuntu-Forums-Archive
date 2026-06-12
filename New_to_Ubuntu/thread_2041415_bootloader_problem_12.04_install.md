---
title: "bootloader problem 12.04 install"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by linuxnovice on 2012-08-12
Hi,

I was dual booting Windows 7 and Ubuntu 11.04 on a Gateway desktop pc. I wanted to install Ubuntu 12.04. I tend to do fresh installs and not upgrades. When I poped in the live CD (usb) I was given an option of erasing 11.04 and installing 12.04 (along with upgrading 11.04, erasing everything and installing 12.04 etc). 

I chose to erase 11.04 and install 12.04 and the installation proceeded without problems. But at the end, I got an grub error (I dont remember on which partition how do I find this out?) mentioning that it was a fatal error. It gave me three options to proceed, install the bootloader on sdb (usb), continue without bootloader or cancel the installation. I chose to continue without the bootloader, hoping to install it manually later. However, I don't really know how to go about doing this. I hope my Windows system is not disturbed (which should be the case since this is a bootloader issue).

Any help is appreciated!
Thanks.

---

### Post by Bashing-om on 2012-08-12
linux n ;

 Not to be too perturbed ... shud be good...
we will get grub loaded properly ....
1. lets find out what your system looks like ..  -how many drives do you have installed -and, what partition has ubie loaded as the boot partition.
 do in terminal:
```
sudo fdisk -l
```
   will require your password... will get no response of entered password echoed to screen....
now look on the output for a line with an astaric (*) in it ... and advise  what the left column designates (ie /dev/sda1)....
[INDENT]warm regards <====BDQ
[/INDENT]

---

### Post by Mortesins93 on 2012-08-12
If you cannot boot, just use a liveCD. Once in, find out on which partition you installed ubuntu with either gparted or as Bashing-om said using the command:```
sudo fdisk -l
```After that, let's say you installed ubuntu in the /dev/sda1 partition, open a terminal and type: ```
sudo mount /dev/sda1 /mnt
```This will mount the partition in the /mnt folder.
Then type:
```
sudo grub-install --root-directory=/mnt /dev/sda
```this will install grub bootloader in the device /dev/sda with all the configuration files in the /dev/sda1 partition because it is mounted in the /mnt folder.
After that, unmount the partition:
```
sudo umount /dev/sda
```For more information: 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
13. Reinstalling GRUB2 from LiveCD

---

### Post by linuxnovice on 2012-08-13
Hey guys,

Sorry for the late reply. I booted using the livecd and chose to install the OS again by using the custom option. I created / and /home fresh and everything worked out fine. Grub got installed correctly and I was able to boot into windows and ubuntu without any problems.

Thanks for your help!

---

### Post by Mortesins93 on 2012-08-13
No problem, glad to know you managed to make it work.

---

