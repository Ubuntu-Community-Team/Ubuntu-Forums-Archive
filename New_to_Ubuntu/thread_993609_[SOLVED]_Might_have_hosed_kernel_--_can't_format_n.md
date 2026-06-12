---
title: "[SOLVED] Might have hosed kernel -- can't format newly re-sized partition with Gparte"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by akelsall on 2008-11-25
I'm trying to resize an existing partition (taking 50Mb of an existing 500 Mb partition) as a test. I figured out how to resize, but when I go to format the new partition (as a logical partition / ext3), it gives me the following error message. Also, now, when I run Gparted, it keeps saying "The kernel is unable to re-read the partition tables on the following devices: - /dev/sda" 

Have I hosed my root partition? I have not re-booted since causing the error (in hopes that if I did hose something, I can fix it before re-booting). Any advice/help would be GREATLY appreciated.

Thanks,

Andy

Also, while I'm at it, if you can describe the correct way to resize and create a new logical partition, I'd appreciate it!


========================================

Libparted 1.7.1

Format /dev/sda16 as ext3  00:02    ( ERROR )
     	
calibrate /dev/sda16  00:01    ( SUCCES )
     	
path: /dev/sda16
start: 429706683
end: 429803009
size: 96327 (47.03 MiB)
set partitiontype on /dev/sda16  00:01    ( SUCCES )
     	
new partitiontype: ext3
create new ext3 filesystem  00:00    ( ERROR )
     	
mkfs.ext3 /dev/sda16
     	
mke2fs 1.40.8 (13-Mar-2008
Could not stat /dev/sda16 -- No such file or directory

The device apparently does not exist; did you specify it correctly?
libparted messages    ( INFO )
     	
Error informing the kernel about modifications to partition /dev/sda16 -- Invalid argument. This means Linux won't know about any changes you made to /dev/sda16 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sda.

---

### Post by akelsall on 2008-11-26
Well, when I got up this morning, I decided to just try and delete the newly created partition, and that seems to have fixed the problem (I no longer get that kernel message when starting gparted). Guess I need to read up some more on gparted before I REALLY break something.... :lolflag:

---

