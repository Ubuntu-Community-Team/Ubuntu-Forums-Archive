---
title: "Please help about software RAID 1"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by bestrag on 2011-12-05
[SIZE=4]I read more than few articles about setting software RAID 1 and each time I configured my HDDs ( 1Tb SATA both ) I ended up reinstalling entire box because something went wrong. Now I know there is a lot of info out there about how to set your RAID, however, it seems to me that non answered straight to practical question.

I run 11.10 Desktop 32bit. One HDD is bootable and it is separate 150GB 

1 - how to set my other two HDDs to be in RAID 1
2 - how to map my /home to that RAID

I really need help. I am learning gnu/linux and I feel that there is always going to be a lot to learn... 

take care
[/SIZE]

---

### Post by tob10 on 2011-12-06
> **bestrag said:**
> 
1 - how to set my other two HDDs to be in RAID 1
Assuming the disks are /dev/sdb and /dev/sdc. You do not need to have any partition on them since you will be using the entire disk.
```
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
```
You will see a warning using this new device for boot. Since you will use it as /home you can answer y and hit enter to create the raid device.

Verify its creation
```
cat /proc/mdstat
```
> **bestrag said:**
> 
2 - how to map my /home to that RAID
You need to first mount your new home to a temp location and move users home dir to it.

a) Make filesystem on new partition
```
sudo mkfs.ext4 /dev/md0
```
b) Make a temp mount point
```
sudo mkdir /mnt/newhome
```
c) Mount the new device to a temp location.
```
sudo mount /dev/md0 /mnt/newhome
```
d) Copy all files to new home
```
sudo rsync -rav /home/ /mnt/newhome/
```
e) Unmount new device and mount it as /home
```
sudo umount /mnt/newhome
sudo mount /dev/md0 /home
```
f) Log in with a user to make sure everything is OK. Do not log out your current session. If something goes wrong you have to restart the server.

**Make the new home mount at boot**

g) Get the UUID of /dev/md0
```
sudo blkid /dev/md0
```
h) Copy the UUID and add a new entry in /etc/fstab.
```
UUID=a9b1b5e1-a519-4d0a-bcea-2828d8bc6ab2 /home           ext4    defaults        0       2
```
i) Reboot computer and make sure everything is working OK.

**Note** Make sure youre using UUID in fstab. On my system the raid device is renamed after reboot. If youre using UUID it doesnt matter what its name is in /dev.


If you have lots if data in /home you want to remove all files in old /home to free up disk space for /. To do that you first have to unmount /home and then delete everything in /home/. Then remount your new /home

1) Move yourself to /
```
cd /
```
2) Unmount /home
```
sudo umount /home
```
3) Make sure its unmounted
```
cat /proc/mounts | grep home
```
4) Remove all files in /home
```
sudo rm -rf /home/*
```
5) Remount new /home
```
sudo mount /dev/md0 /home
```


**If you change your mind about the raid and want to remove it do the following**

First make sure the device is not mounted. If it is mounted; unmount it.

1) Fail all disks
```
sudo mdadm --manage /dev/md0 --fail /dev/sdb /dev/sdc
```
2) Remove all disks
```
sudo mdadm --manage /dev/md0 --remove /dev/sdb /dev/sdc
```
3) Stop the raid
```
sudo mdadm --manage --stop /dev/md0
```
4) Zero the superblock on all disks to make them not recognized as part of a raid.
```
sudo mdadm --zero-superblock /dev/sdb /dev/sdc
```


Have fun! :)

---

### Post by bestrag on 2011-12-11
Oh man,

I can not describe how open source is changing my life right now. It first started with just few shallow installs. But, I am telling you, right now, I am completely nuts about it.

This is just mighty

ps: this was my very first ever post in Open source community. I was always way too pissed about dealing with all this crap. And just after I made this post I never even start thinking for a moment why would I run Linux other than drop Windows. But in one moment I just glued every single work-flow I did, and more importantly I WILL HAVE, into one HELL OF A RIDE

I love you all guys

seriously
thank you

---

