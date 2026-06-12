---
title: "Can I make it so my hard drives are mounted on startup?"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by sogeking99 on 2012-09-06
Every time I boot up my second hard drive is not mounted, and Rythmbox has to look for all my tracks again.

---

### Post by shreepads on 2012-09-06
> **sogeking99 said:**
> Every time I boot up my second hard drive is not mounted, and Rythmbox has to look for all my tracks again.

Is it listed in /etc/fstab file? 

- If so please show us the content in /etc/fstab

- If not, then you need to setup an fstab entry for the drive so that it mounts automatically on boot up

---

### Post by sogeking99 on 2012-09-06
I don't think it is in there no, this is my fstab:

# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk	none	swap	sw	0	0

---

### Post by jerome1232 on 2012-09-06
> **sogeking99 said:**
> I don't think it is in there no, this is my fstab:

# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0

mount the disk and show us the output of these commands 
```
mount
sudo blkid
```

---

### Post by sogeking99 on 2012-09-06
Okay, here it is.

owner@ubuntu:~$ mount
/dev/loop0 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda4 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/owner/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=owner)
/dev/sr0 on /media/GW2_DVD2 type udf (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)
/dev/sda2 on /media/YAY! type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/8ECC6480CC646505 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
owner@ubuntu:~$ sudo blkid
[sudo] password for owner: 
/dev/loop0: UUID="9b16030c-08f8-4f5d-b228-63e13bca7839" TYPE="ext3" 
/dev/sr0: LABEL="GW2_DVD2" TYPE="udf" 
/dev/sda2: LABEL="YAY!" UUID="46C29470C2946649" TYPE="ntfs" 
/dev/sda4: UUID="E8A427C0A427905C" TYPE="ntfs" 
/dev/sda5: UUID="8a10bdee-acca-4c7e-b8e2-2841444cdd98" TYPE="swap" 
/dev/sdb1: UUID="8ECC6480CC646505" TYPE="ntfs" 
owner@ubuntu:~$

---

### Post by jerome1232 on 2012-09-06
You have serveral disks mounted, which one is it that you want to permanently mount. (is it Yay! or the other one?)


As an aside I'm sure there's a gui way for you to do this, have you tried using the package** pysdm **I recall it being a user friendly way to muck around with your fstab.

---

### Post by ENigma885 on 2012-09-06
You can use a simple GUI for that; NTFS Configuration Tool
```
sudo apt-get install ntfs-config
```

Then launch it from your dash menu or from Terminal
```
gksudo ntfs-config
```

---

### Post by sogeking99 on 2012-09-06
Something is wrong with this I think. My Rythmbox says all my songs are missing files, even though I have the drive mounted, and there is no restart option on my PC? If I log off, then try to log on it hangs and I have to force restart.

EDIT: Oh I found restart. Yes my PC hangs when trying to shut down, restart and re-login. It seems the only way I can turn this off is by forcing it?

On booting up I am getting something like 'sda4 failed to mount, press S to skip or M to set manually'

---

### Post by jerome1232 on 2012-09-06
That drive you are mounting isn't your windows drive is it? if so then you don't actually need to mount it. since you are using wubi all of your windows files can be found under /host

---

### Post by abexman on 2012-09-13
Dumb question. So I am on Ubuntu 12, not Wubi. Can I just edit this fstab file in a text editor and add/remove drives as needed? Should drives like USB sticks or other external drives be included in that list, if I may only use them once or so, and then remove them? Should they be listed there if they are no longer present? I guess just trying to understand how and why the fstab file is used.

---

### Post by jerome1232 on 2012-09-13
> **abexman said:**
> Dumb question. So I am on Ubuntu 12, not Wubi. Can I just edit this fstab file in a text editor and add/remove drives as needed? Should drives like USB sticks or other external drives be included in that list, if I may only use them once or so, and then remove them? Should they be listed there if they are no longer present? I guess just trying to understand how and why the fstab file is used.
based on your mount output, you're using Wubi . open your file  browser , click file system n left hand pane. look for host, if it exists then that's where your windows files are at.

Excuse any typos I'm on my phone atm

---

### Post by oldfred on 2012-09-13
@jerome1232
abexman is not the OP who does have wubi.  He is just hijacking sogeking99 thread. :)

You should only mount partitions from permanent disks, as you temporary mount partitions from USB or other removeable devices.
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

### Post by draalin on 2012-09-13
I made a guide a couple of hours ago for fstab auto mounting on 12.04+

Screenshots included!

[http://ubuntuserverhelp.com/mounting-with-fstab/](http://ubuntuserverhelp.com/mounting-with-fstab/)

---

### Post by jerome1232 on 2012-09-14
For a new guy, I'd just recomend installing Psydm, unless you want to dig a litte into the manual editing of config files.

---

