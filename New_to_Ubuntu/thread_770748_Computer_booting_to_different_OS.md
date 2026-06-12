---
title: "Computer booting to different OS:"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Jambhavan on 2008-04-27
What is wrong with my computer?

I had Windows XP and Mandriva Linux in my computer with a grub loader to boot the OS. Both were working properly but then I had to reinstall my XP (for some reason), and since it's a factory supplied (reinstall only DVD), it cleared all the partitions and installed XP. Then I wanted to install Ubuntu and so I set up the dual boot with Ubuntu and XP with Grub to boot. Recently I used one registry cleaner, and cleared whatever it suggested. When I boot my system after that registry clean, it brought up my Mandriva Grub loader screen (blue screen unlike Ubuntu black and white, with Mandriva OS being identified in the top), and two other XP editions, and 2 more linux editions. I did not boot into other linux (probably a version of Mandriva or Ubuntu), but tried Mandriva OS and Windows XP, both are working fine. I am surprised to see that Mandriva is booting (because I expected it to be completely erased or so) after this long time.

One more surprise is two different things happen depending on whether I turn off my computer and start, and when I restart.

If restarted, this new grub loader (Ubuntu with a plain black and white) comes up, in that there is no Mandriva linux but a list of several linux versions -- all updates of Ubuntu (probably Mandriva linux is in the next page or so). This is what I wanted.

IF turned off and then started, the old grub loader (with Mandriva screen) comes up.

And when I tried to locate my grub.conf in the /etc (in Ubuntu), I did not find any.

What had happened to my computer? It is working fine and I have no problems, since I found out whether I should restart or turn off. But a permanent remedy is better.

Thanks for the suggestions.

Jam

---

### Post by tamoneya on 2008-04-27
in ubuntu it is /boot/grub/menu.lst

---

### Post by elpichi on 2008-04-27
Just a quick question, when you installed Mandriva, did you make a separate partition just for /boot? maybe your computer is looking into two bootable places(no idea if its even possible to have 2 bootable partitions, but if ubuntu installs it into /boot under the real partition, then there could be some conflict o.o)?

---

### Post by Jambhavan on 2008-04-27
Hi Tamoneya

Thanks, I found it as you said.

Hi Elpichi

I think you are right that I have installed in /boot partition only. I also supplied one wrong information about restart.

If I were in Windows XP, and then choose Restart, it will get me to Grub loader of Ubuntu (plain menu). But if Turned off and started, it brings up the Grub loader associated with Mandriva (with a blue screen with Mandriva on top of the menu).

If I were in Ubuntu, and then choosing Restart or Turn off/Start gives the same result as above.

If I were in Mandriva, and then restarting or turn off/start, all gets me to the same Grub loader (Mandriva).

No clues on how to get rid of Mandriva Linux or boot loader associated with it.

For a fraction of a second, I see that Grub loader starts up (like a plain black and white - only two lines comes in the top) and then quickly get to the Mandriva Grub loader menu.

Thanks for the help.

Jam

---

### Post by elpichi on 2008-04-27
what you can do is to either replace the grub in the partition made for /boot with the one you have in the root partition

or delete the partition completely leaving root partition handle the booting

I would recommend the first option, less risky in the matter that you can always backup the old version of grub and you won't be playing with your hard drive.. when it comes to partitioning.

---

### Post by Jambhavan on 2008-04-27
Elpichi

Thanks for the quick reply.

Thank you for the suggestion. As I am new to using Linux, I will go through all the precautions like backing up, etc. and then do it as you said.

Regards,

Jam

---

### Post by Jambhavan on 2008-04-27
This is my (Mandriva) Grub loader menu file contents. Location: /boot/grub/menu.lst

starts here
********************************************
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,1)/boot/gfxmenu
default 0

title linux
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb2 resume=/dev/sdb5 splash=silent vga=788
initrd (hd0,1)/boot/initrd.img

title linux-nonfb
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sdb2 resume=/dev/sdb5
initrd (hd0,1)/boot/initrd.img

title failsafe
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sdb2 failsafe
initrd (hd0,1)/boot/initrd.img

title windows
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title windows1
root (hd0,2)
makeactive
chainloader +1

title windows2
root (hd0,3)
makeactive
chainloader +1

title 2.6.17-13
kernel (hd0,1)/boot/vmlinuz-2.6.17-13mdv BOOT_IMAGE=2.6.17-13 root=/dev/sdb2 resume=/dev/sdb5 splash=silent vga=788
initrd (hd0,1)/boot/initrd-2.6.17-13mdv.img

title 2.6.17-14
kernel (hd0,1)/boot/vmlinuz-2.6.17-14mdv BOOT_IMAGE=2.6.17-14 root=/dev/sdb2 resume=/dev/sdb5 splash=silent vga=788
initrd (hd0,1)/boot/initrd-2.6.17-14mdv.img

********************************************************
ends here

The below is my menu file from /boot/grub/menu.lst of Ubuntu system

starts here
********************************************************


title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

*********************************************************

ends here.

Just thought if you could figure out what's happening with my system.

Thanks again.

Jam

---

### Post by elpichi on 2008-04-27
umm just to check. can you post the output of 
```
sudo fdisk -l
```
This prints all hard drives and its partitions with descriptions including if they are bootable or not.
if there are 2 bootable partitions then we could uncheck one and solve this problem.

and for the grub setting 
```

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,1)/boot/gfxmenu
default 0

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 8.04, kernel 2.6.20-16-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=c1968ce8-ade5-42b6-9391-0e8393238aaa ro single
initrd /boot/initrd.img-2.6.20-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

#not sure if this is the kernel you are currently using
#but my guess is that you always pick the first option to boot for Mandriva
###########ManDriva##############
title ManDriva
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb2 resume=/dev/sdb5 splash=silent vga=788
initrd (hd0,1)/boot/initrd.img
########################



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP Media Center Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

```
This will give you all 3 operating systems as options

---

### Post by Jambhavan on 2008-04-27
Elpichi

Thanks for the reply. I was away for shopping. I came back and backed up my files and folders. I found out my problem which is silly.

It is really silly that I ignored to see my attached mini storage disk, which is also bootable, and checked that a linux version (Mandriva) is still in there. In the morning, I tried to copy the menu file (Mandriva linux grub loader) and named it differently and placed a copy each in my home folder and /boot/grub/ folders, and wanted to see if they are visible in Ubuntu linux file system.

I found them both in my attached hard disk, and problem solved.

Thanks for helping me.

Jam

PS: Here is the output from the command fdisk -l

**************************************************

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1403        7304    47407815    7  HPFS/NTFS
/dev/sda2            7305       11900    36917370    f  W95 Ext'd (LBA)
/dev/sda3               1        1402    11261533+  83  Linux
/dev/sda5            7305        7565     2096451   82  Linux swap / Solaris
/dev/sda6            7566        9350    14337981    b  W95 FAT32
/dev/sda7            9351       11900    20482843+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80d1a799

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        4725    37945530    f  W95 Ext'd (LBA)
/dev/sdb2            4726        6128    11269597+  83  Linux
/dev/sdb3            6129        9144    24226020    7  HPFS/NTFS
/dev/sdb4            9145       12161    24234052+   7  HPFS/NTFS
/dev/sdb5               2         263     2104483+  82  Linux swap / Solaris
/dev/sdb6             264        4725    35840983+   b  W95 FAT32

*************************************************************

---

### Post by elpichi on 2008-04-27
:lolflag: glad you found it out =] 
it was a pleasure trying to help. ;)

---

