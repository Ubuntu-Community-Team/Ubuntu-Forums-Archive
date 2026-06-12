---
title: "Moving from Dual Boot to Multi boot [Dedicated GRUB Partition]"
date: 2009-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by meka4996 on 2009-05-25
Moving from Dual Boot to Multi boot [Dedicated GRUB Partition]
For many linux distro os and MS Windows, one Grub main menu at MBR and many menu for each distro/linux/os
Thanks for the posts of ...
[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

... the following steps assume you have a Dual boot system already! but wanting to move to Multi boot...

1) make a small partition (my 5 distro GRUB partition only has 11MB used space)
2) Label your file system.
```
$ sudo fdisk -lu
```
```
$ e2label /dev/sde1 GRUB
```
```
$ ls /media
```
Reboot your computer, and mount the new GRUB partition. for example (hd0,7)

3) Make a directory "boot" in your new GRUB partition (in /media/GRUB)
```
$ sudo mkdir /media/GRUB/boot
```

4) Copy your /boot/grub directory(that is inside this working linux already) to the new GRUB partition,
```
$ sudo cp -r /boot/grub /media/GRUB/boot/
```

5) Edit the new GRUB partition's menu.lst file by ...
```
$ sudo gedit /media/GRUB/boot/grub/menu.lst
```

6) Delete all the old operating system boot entries, and the entire Debian Automagic Kernels List too.
Example of Multi Boot menu.lst (GRUB partition's menu.lst)

title Ubuntu 8.04 (/dev/sda6)
root (hd0,5)
chainloader +1

title ArtistX 0.6 Ubuntu 8.10 (/dev/sda7)
root (hd0,6)
chainloader +1

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
chainloader +1

Note: Don't get confused! The above menu.lst [the main GRUB menu.lst] is the first menu you will see, so you can choose which distro you want to boot, then you will see each linux distro's menu.lst, which is just the normal menu.lst listing different kernel versions under that distro.

7) Re-install Grub from your new GRUB partition to MBR.
(Notice the order FROM abc TO xyz)
```
$ sudo grub
```
```
grub> find /boot/grub/stage1
```
(hd0,1)
(hd0,5)
(hd0,6)
(hd0,7)
(hd1,1)
```
grub> root (hd0,7)
```
```
grub> setup (hd0)
```
```
grub> quit
```

Note, sometimes GRUB gets the device label wrong...
for example, when using "sudo grub" inside a workig linux os, "find" command returns (hd0,5)
but at grub command line before booting into that linux os, "find" command returns (hd1,5)
so just manually edit the main GRUB menu.lst

8) Give all your operating systems a test boot-up to make sure everything's working fine.

EXTRA STEPS
9) later, when installing a new linux distro into a partition, for example, partition LinuxY,
just make sure to install bootloader Grub or Lilo into that partition LinuxY 
in Ubuntu, at the last HD installation step, there is a small button "Advanced Options", click on it, then choose to install bootloader Grub into LinuxY
(Not to install it into MBR, which is hd0 or hd1 )

(by the way, in the earlier steps, you only need to select one / partition[root partition], and one swap partition [... so edit all other swap partitions for "NOT TO BE USED"] )
After linux HD installation, add lines like below into the main GRUB menu.lst that is inside the dedicated Grub partition

title Ubuntu 9.04 (/dev/sda9)
root (hd0,8)
chainloader +1

if that linux has to install its /boot as a separate partition, (hd0,9), then just edit the main GRUB menu.lst according to where that /boot partition is

title Fedora 11 (/dev/sda10)
root (hd0,9)
chainloader +1

10) Fun thing to do... add lines below into each linux distro's menu.lst, that will get you back to the main menu!
title		Main Menu (/dev/sda8)
root		(hd0)
chainloader +1

Enjoy =)

---

### Post by meka4996 on 2009-06-10
Related Topic: 
Grub Basic Troubleshooting Checkpoints/Flow Chart
[http://ubuntuforums.org/showthread.php?t=1169670](http://ubuntuforums.org/showthread.php?t=1169670)

menu.lst and device.map files.
download then rename them to "menu.lst", "device.map"

main GRUB menu.lst
download then rename it to "menu.lst"

---

