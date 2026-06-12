---
title: "cannot format drive.....???"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by mooglinux on 2008-05-08
i am trying to install 8.04, deleted my old partitions and when i try to format with the installer it gave me an error. went back with gparted and got a more specific error
```
GParted 0.3.5

Libparted 1.7.1

Delete /dev/sdb1 (unknown, 74.50 GiB) from /dev/sdb  00:00    ( SUCCES )
     	
calibrate /dev/sdb1  00:00    ( SUCCES )
     	
path: /dev/sdb1
start: 63
end: 156248189
size: 156248127 (74.50 GiB)
delete partition  00:00    ( SUCCES )
libparted messages    ( INFO )
     	
Error informing the kernel about modifications to partition /dev/sdb2 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sdb2 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sdb (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sdb.

========================================

Create Primary Partition #1 (ext3, 74.50 GiB) on /dev/sdb  00:00    ( ERROR )
     	
create empty partition  00:00    ( SUCCES )
     	
path: /dev/sdb1
start: 63
end: 156248189
size: 156248127 (74.50 GiB)
set partitiontype on /dev/sdb1  00:00    ( SUCCES )
     	
new partitiontype: ext3
create new ext3 filesystem  00:00    ( ERROR )
     	
mkfs.ext3 /dev/sdb1
     	
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/sdb1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
libparted messages    ( INFO )
     	
Error informing the kernel about modifications to partition /dev/sdb1 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sdb1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
Error informing the kernel about modifications to partition /dev/sdb2 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sdb2 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sdb (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sdb.
Error informing the kernel about modifications to partition /dev/sdb1 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sdb1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
Error informing the kernel about modifications to partition /dev/sdb2 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sdb2 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sdb (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sdb.

========================================

```
What do i need to do to fix this?

---

### Post by angry_johnnie on 2008-05-08
Right out of your error message:

This means Linux won't know about any changes you made to /dev/sdb2 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.

So, try rebooting and see what happens. :-)

---

### Post by sujoy on 2008-05-08
pretty straightforward huh!

i will be surprised if it doesn't work after a reboot :)

---

### Post by hyper_ch on 2008-05-08
reboot is not required, just unmounting the drive should be enough.

---

### Post by njparton on 2008-05-08
```
 
sudo mkfs.ext3 -f /dev/sdb1

```
 
-f will force it to format the partition if it detects something on there already.

---

### Post by mooglinux on 2008-05-08
Solved! i just restarted, and booted the live cd without trying to do all manner of things to access my ntfs partittion. worked like a breeze!

---

