---
title: "Grub rescue promt, dual boot problem"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by zull0017 on 2012-03-07
Hi to all

i had a working dual boot system winxp (installed first) and ubuntu 10.04.
After a boot from live usb.. the grub menu fails to start. I am in the grub rescue>  promt.
I log through my live usb.In terminal, the command sudo fdisk -l outputs this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ded4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5810    46664014    7  HPFS/NTFS
/dev/sda2            5810       19458   109625345    f  W95 Ext'd (LBA)
/dev/sda5            5810        6592     6282170    7  HPFS/NTFS
/dev/sda6            7566        7649      666624    7  HPFS/NTFS
/dev/sda7            6592        7517     7431168   83  Linux
/dev/sda8            7517        7566      387072   82  Linux swap / Solaris
/dev/sda9            7650       18591    87889920    7  HPFS/NTFS
/dev/sda10          18591       19458     6958080    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    b  W95 FAT32

I tried to fix it with this command : " sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev  && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt"
and i get this message :   mount: mount point /mnt/dev does not exist

when i try this: "sudo mount /dev/sda1 /mnt"  it does it sucessfully and then i try again the command above and i get this error: " fuse: mount failed: Device or resource busy"

Can anybody help me??

Thanks in advance!!!

---

### Post by oldfred on 2012-03-07
Your Linux partition is sda7, trying to mount NTFS partitions leads to the fuse errors as they are not Linux and you need fuse to mount NTFS.

One of the easier ways to repair.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

If you are getting a grub prompt you may be able to manually boot. Then repair grub after booting.

Manual boot:
See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,7), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

or:

set prefix=(hd0,7)/boot/grub
set root=(hd0,7)
linux (hd0,7)/vmlinuz root=/dev/sda7 ro
initrd (hd0,7)/initrd.img
boot

---

