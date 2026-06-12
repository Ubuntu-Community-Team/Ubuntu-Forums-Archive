---
title: "How make an extra virtual hd visible"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by deme2 on 2014-07-18
I am using VMWare Player with Ubuntu 14. I created one more virtual hd named dev/sdb1. I can see a file in dev name sdb1 (type = block device (inode/blockdevice)). I was expecting to see this HD under Computer in Nautilus but I don't. I am very new in Ubuntu. I guess I have to mount this and it will be enough so I tried use Disk Utility but I dind't find how. Am I in correct direction? Do I only have to mount this? If so, how can I do this?

---

### Post by billdozor on 2014-07-18
Assuming the virtual hard drive you have added is already partitioned and a file system exists on it, yes, you just need to mount it.

Here are the steps that should be followed:

[LIST=1]
[*]Create a new virtual hard drive in VMWare Player, start up Ubuntu.
[*]Open a terminal, use fdisk to create a partition on the new hard drive
[LIST]
[*]sudo fdisk /dev/sdb
[*]n (new partition)
[*]p (for primary)
[*]Press Enter to accept default values for partition number, first sector, and last sector
[*]w (write changes and exist)
[/LIST]

[*]Create a file system on the new partition (/dev/sdb1)
[LIST]
[*]sudo mkfs -t ext4 /dev/sdb1
[LIST]
[*]That creates a file system of type ext4 on the new partition.
[/LIST]
[/LIST]

[*]Create a directory for the new hard drive to be mounted.
[LIST]
[*]This can be anywhere on the filesystem.
[*]Example: sudo mkdir /mnt/Storage
[/LIST]

[*]Mount the hard drive
[LIST]
[*]sudo mount -t ext4 /dev/sdb1 /mnt/Storage
[/LIST]
[/LIST]

Good luck!

---

### Post by nerdtron on 2014-07-18
While you can do that on the terminal, this is Ubuntu Desktop right? It almost same what you do in windows, when you attach a new hard drive to you computer you need to format it. 
So on Ubuntu, you can use the Disks Utility or install Gparted. Once you see the newly attached attached hard drive, you can create partitions format it using the GUI tools. Recommended file systems would be ext4 and xfs.
Once you create partitions and formatted them your drive should show up on Nautilus and then click it to mount it.

---

