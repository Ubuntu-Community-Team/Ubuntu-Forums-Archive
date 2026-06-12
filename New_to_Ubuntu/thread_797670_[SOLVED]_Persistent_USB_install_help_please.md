---
title: "[SOLVED] Persistent USB install help please"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-05-17
So I am trying to get a persistent install of Ubuntu 8.04 on a USB flash drive, but I am running into a problem. I am following the guide from [here]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/") but I am getting stuck on the partitioning part. For some reason it wont partition the fat16 part, I get an error. So I decided to try and use gparted, but I get this error. ```
GParted 0.3.5

Libparted 1.7.1

Create Primary Partition #1 (fat16, 753.05 MiB) on /dev/sdb  00:00    ( ERROR )
     	
create empty partition  00:00    ( SUCCES )
     	
path: /dev/sdb1
start: 63
end: 1542239
size: 1542177 (753.02 MiB)
set partitiontype on /dev/sdb1  00:00    ( SUCCES )
     	
new partitiontype: fat16
create new fat16 filesystem  00:00    ( ERROR )
     	
mkdosfs -F16 -v /dev/sdb1
     	
mkdosfs 2.11 (12 Mar 2005)
mkdosfs: /dev/sdb1 contains a mounted file system.

========================================

``` Any clues as to why this is happening?

---

### Post by shifty_powers on 2008-05-17
tried using the gparted live cd?

---

### Post by yellowbread on 2008-05-18
In gparted, right clicking the partition brings up a menu with options for mounting or unmounting the partition. Unmount the partition you are working on, then try again.

---

### Post by slughappy1 on 2008-05-19
It was unmounted. I used fdisk and got rid of all of the partitions on the drive, and then tried again the next morning. Thankfully that worked

---

