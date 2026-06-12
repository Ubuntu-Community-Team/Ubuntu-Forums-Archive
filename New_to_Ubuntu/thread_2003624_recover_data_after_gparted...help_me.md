---
title: "recover data after gparted...help me"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by tmaius on 2012-06-14
i-ve used gparte live in order to decrease the hard disk storage and create a new hard disk
after ubuntu doesn-t start anymore

     sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="f009afa0-8cc7-441d-b303-0b4d1ce429e4" TYPE="ext4" 
/dev/sda3: LABEL="simo7" UUID="513E50EE46192B4A" TYPE="ntfs" 
/dev/sdb1: LABEL="simo2" UUID="53AB-E584" TYPE="vfat" 

fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f009afa0-8cc7-441d-b303-0b4d1ce429e4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=2a1bdd9a-a0f6-41c0-8835-4f65265b071d none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
tmpfs /home/simo/temp_d tmpfs nodev,nosuid 0 0


i read that uuid number sould be the same...but it is
and so I think there sould be another problem
so now I-ve tried to save my data and format
after chamge some permissione i find in my home two files:
Access-Your-Private-Data.desktop  
README.txt

and readme says:
-------------
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
------------
this is the result:
 ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly

help me please!
(sorry for english)

---

### Post by tmaius on 2012-06-14
nothing?
please

---

### Post by mapes12 on 2012-06-14
Try this:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tmaius on 2012-06-14
it asks me the command:
sudo chroot "/media/f009afa0-8cc7-441d-b303-0b4d1ce429e4" apt-get install -fy
sudo chroot "/media/f009afa0-8cc7-441d-b303-0b4d1ce429e4" dpkg --configure -a
sudo chroot "/media/f009afa0-8cc7-441d-b303-0b4d1ce429e4" apt-get purge -y --force-yes grub-common

these the answers

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

dpkg: error: unable to access dpkg status area: Read-only file system


W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.


and with chmod i can't change permission

how to remove grub2 with an alternative way?

---

### Post by tmaius on 2012-06-14
ok I've done everything of bootrepair but the boot doesn't go...it stops in a line about battery mode or something else

---

### Post by mapes12 on 2012-06-15
Can you boot from a live Ubu CD/USB and access the partition where the data is that you want to recover? If yes then copy it to external media then go for a fresh install.

---

### Post by tmaius on 2012-06-15
it's what i've done
 i find in my home two files:
Access-Your-Private-Data.desktop 
README.txt

and readme says:
-------------
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
"Access Your Private Data"

or

From the command line, run:
ecryptfs-mount-private
------------
this is the result:
ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly


is it possible that 12gb of free space that I left are not enough?

---

