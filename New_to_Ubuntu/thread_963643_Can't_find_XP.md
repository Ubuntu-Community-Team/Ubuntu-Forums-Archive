---
title: "Can't find XP"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by ex-para on 2008-10-30
I just yesterday installed Ubuntu and I must say with no problems, but I don't know where to now find WinXP. First I tried to install using the CD from windows but it would not so I shut down and rebooted with the disc in where it goes. When it booted up I did the install from the install icon on the Ubuntu desktop and it installed. When I booted up after install it went strait to Ubuntu, I thought it would give me a choice between WinXP or Ubuntu the same as when booting NimbleX but surely it must be possible to access Winxp in some way as for one thing I need to delete a lot of stuff there. 
A reply would be appreciated.

---

### Post by echo.whoami on 2008-10-30
in a terminal type : sudo fdisk -l and tell me what does it gives you

---

### Post by Northsider on 2008-10-30
Did you make a new partition for the Ubuntu install (during the installation process)?  If not, you may have formatted/overwritten your windows partition.

---

### Post by kansasnoob on 2008-10-30
Echo.whoami is right, we need to see the output of:

```
sudo fdisk -l
```

(That's a lower case L at the end.)

---

### Post by ex-para on 2008-10-30
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
I did not make any partitions.
Thanks for the replies.

---

### Post by ex-para on 2008-10-30
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 1023 MB, 1023410176 bytes
62 heads, 32 sectors/track, 1007 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Disk identifier: 0x3b6feeba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1008      999392    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1023, 61, 32) logical=(1007, 28, 32)

Disk /dev/sdc: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3816      976880    e  W95 FAT16 (LBA)
barrie@barrie-laptop:~$

---

### Post by M!K3_$ on 2008-10-30
If you wrote over your windows partition while installing ubuntu, there is nothing you can do. Just accept your loss.

However, if your partition is still there, but perhaps GRUB (the bootloader) isn't reconizing windows for some reason you can try [supergrub]("http://supergrub.forjamari.linex.org/"). This will show you all of your operating systems installed and allow you to boot into them. Just burn the .iso, pop it in, reboot your machine and follow the instructions.

good luck :D

---

### Post by ex-para on 2008-10-31
OK, thanks for the replies just one thing when boot up Windows XP Prof does come up but goes off and on to Ubuntu very fast, does this mean anything.

---

