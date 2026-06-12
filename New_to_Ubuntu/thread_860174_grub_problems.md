---
title: "grub problems"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by dnns123 on 2008-07-15
I installed Windows in an HDD via USB. My original HDD was connected to the same computer during the whole installation. After that, I tried to boot up from my real HDD and found out that the windows installation wiped out GRUB from the MBR. Also, my HDD's partition tables cant be found using the partition editor from the liveCD, but all my files can still be accessed using the LiveCD (whew!).

I tried the info from 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

but I get errors even if I do it properly.

> 
grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 12: Invalid device requested


I don't understand the problem

---

### Post by Het Irv on 2008-07-15
This is an old thread, but see if it helps:

[http://ubuntuforums.org/archive/index.php/t-464695.html](http://ubuntuforums.org/archive/index.php/t-464695.html)

---

### Post by sandysandy on 2008-07-15
there is a utility called Super Grub ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/))

which u can download and burn a bootable CD.

with the Super Grub Disk u can try and do some trouble shooting.

regards

---

### Post by Het Irv on 2008-07-15
Follow Up:

> 12 : "Cannot mount selected partition"

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Dunno if that helps any

---

### Post by bumanie on 2008-07-15
boot livr cd and post the output of terminal command > sudo fdisk -l (that's a lower case L)

---

### Post by dnns123 on 2008-07-15
> 
ubuntu@ubuntu:~$ sudo fdisk -l 
omitting empty partition (5)

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6256c0b8

____Device Boot_____Start_________End_______Blocks__Id__System
/dev/sda1_______________1_______44636___358538638+___5__Extended
/dev/sda2____________5464_______44636___314657091____7__HPFS/NTFS
/dev/sda3___*_______44637_______48641____32170162+___7__HPFS/NTFS
/dev/sda5_______________1________5332____42829195+__83__Linux
/dev/sda6____________5333________5463_____1052226___82__Linux swap / Solaris
ubuntu@ubuntu:~$ 


The partition editor doesn't even see this. It just says that my whole HDD is unallocated

---

### Post by dnns123 on 2008-07-15
I tried to reinstall GRUB using this link [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

But it always says that my /boot/grub/stage1 cannot be read.

---

### Post by unutbu on 2008-07-15
(hd0,5) is /dev/sda6 -- your Linux swap according to fdisk.
(hd0,4) would be /dev/sda5 -- the Linux partition.

Try booting from the LiveCD, and typing
```

sudo grub
root (hd0,4)
setup (hd0)
```

---

### Post by bumanie on 2008-07-15
The problem is that you have somehow managed to place all your partitions within an extended partition - windows won't boot from an extended/logical partition under normal circumstances. Unfortunately, you can't get rid of an extended partition without getting rid of what is inside the extended partition.

---

### Post by unutbu on 2008-07-15
bumanie, I think his windows is on /dev/sda3, a primary partition.

---

