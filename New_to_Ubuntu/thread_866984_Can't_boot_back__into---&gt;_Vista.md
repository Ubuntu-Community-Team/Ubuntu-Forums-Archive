---
title: "Can't boot back  into---&gt; Vista"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Georgiou on 2008-07-22
***************PLEASE HELP****************************

Problem:
 Can't boot into windows vista even though its still their?

Vista is on raid zero.ie (2x 320Gb drives)
Ubuntu is on non raid,ie (1x 320Gb drive)

 how do i create a boot menu? 

At the moment ubuntu is functional only.

i really need help and would appropriate if someone could point in the right direction

---

### Post by compnut41 on 2008-07-22
When you installed Ubuntu it should have installed Grubs, which should start up when you turn on your system, and vista should appear on the bottom of the Grubs list. If it doesn't show up there make sure the drive that it is loaded on is set to master. If that fails look under gparted and right click on the windows partition and select manage flags. and see if it is set to boot. 

Good luck

---

### Post by fishman78 on 2008-07-22
> **Georgiou said:**
> ***************PLEASE HELP****************************

Problem:
 Can't boot into windows vista even though its still their?

Vista is on raid zero.ie (2x 320Gb drives)
Ubuntu is on non raid,ie (1x 320Gb drive)

 how do i create a boot menu? 

At the moment ubuntu is functional only.

i really need help and would appropriate if someone could point in the right direction

Howdy!

   I don't know if this is the best way, but I use something called Easy-BCD.  It's a free boot loader/Manager.  Works great for my dual boot.  You need to install it from windows.  The way i did it was:

Installed Ubuntu after windows
Booted from Vista CD - Goto repair computer command prompt
type in bootrec.exe/fixmbr
This will take you straight into windows.  
Download and install Easy-BCD
Configure dual boot as per Easy-BCD instructions (it's really easy)

This worked great for me and I think it looks better than Grub.  Maybe someone else has another way??

Hope this helps

Fishman78

---

### Post by philinux on 2008-07-22
> **Georgiou said:**
> ***************PLEASE HELP****************************

Problem:
 Can't boot into windows vista even though its still their?

Vista is on raid zero.ie (2x 320Gb drives)
Ubuntu is on non raid,ie (1x 320Gb drive)

 how do i create a boot menu? 

At the moment ubuntu is functional only.

i really need help and would appropriate if someone could point in the right direction

Run this in a terminal and post the output.

cat /boot/grub/menu.lst

also the output of

sudo fdisk -l

---

### Post by Georgiou on 2008-07-22
thanks anyways compnut41

tried your 3 suggested methods 
1.check boot loader (Grubs)-> vista OS not listed
2. check Bios,raid 0 given perference-> boot loader remain unchanged
3. Not Sure what exactly your refering too my "gparted"???

i might try fishmans methods.

but thanks

---

### Post by Georgiou on 2008-07-22
> **philinux said:**
> Run this in a terminal and post the output.

cat /boot/grub/menu.lst

also the output of

sudo fdisk -l

here is the out put: for cat /boot/grub/menu.lst
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f649364a-2982-4d5c-a1bb-c113ff8ed521 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f649364a-2982-4d5c-a1bb-c113ff8ed521 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

sudo fdisk

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9e215c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77826   625132544    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xafdfa10f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38161   306528201   83  Linux
/dev/sdb2           38162       38913     6040440    5  Extended
/dev/sdb5           38162       38913     6040408+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23410514

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38914   312568832    6  FAT16
stephen@linex:~$

---

### Post by Georgiou on 2008-07-22
> **fishman78 said:**
> Howdy!

   I don't know if this is the best way, but I use something called Easy-BCD.  It's a free boot loader/Manager.  Works great for my dual boot.  You need to install it from windows.  The way i did it was:

Installed Ubuntu after windows
Booted from Vista CD - Goto repair computer command prompt
type in bootrec.exe/fixmbr
This will take you straight into windows.  
Download and install Easy-BCD
Configure dual boot as per Easy-BCD instructions (it's really easy)

This worked great for me and I think it looks better than Grub.  Maybe someone else has another way??

Hope this helps

Fishman78

THANK YOU FISHMAN!! Your way worked the best, your a geniuses 

For those of you encountering boot problems, i suggest this method 

^^(see above) :)

---

### Post by fishman78 on 2008-07-22
> **Georgiou said:**
> THANK YOU FISHMAN!! Your way worked the best, your a geniuses 

For those of you encountering boot problems, i suggest this method 

^^(see above) :)

No Problem, glad to see you got it fixed up!

Fishman78

---

