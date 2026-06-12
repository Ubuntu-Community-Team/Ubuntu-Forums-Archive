---
title: "How to change default mount options for fuse type WD Passport external storage"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by yy90 on 2013-03-29
One of my external storage devices (WD My Book) is mounting with noexec. I would like it to be mounted with exec, and don't know how to change this. 


Distro = Ubuntu 12.04 (Precise)

I have 2 external USB storage devices:

lsusb:
-----------
Bus 001 Device 002: ID 1058:1130 Western Digital Technologies, Inc. 
Bus 002 Device 006: ID 1058:0730 Western Digital Technologies, Inc. 

which mount automatically as follows:

mount
-----------
/dev/sdb1 on /media/My Book type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/yy90-1tba type ext3 (rw,nosuid,nodev,uhelper=udisks)

Although it's not obvious from the above, the mybook device is getting mounted noexec (presumably that's the default?). The other device (yy90-1tba) is mounted with exec permissions (assuming the default for ext3 is different?). 


There are no entries in /etc/fstab for these devices as I can't figure out how to identify the device UUID uniquely to put into an fstab entry. In any case, I am not sure what / where the default mount options being used for the fuseblk filesystem.  

I've done a lot of searching but haven't found something that could exactly help my case. I've grepped for fuse all over without finding the relevant config file. I've tried running gconf-editor and dconf-editor without success (per some search results) as they didn't show any relevant (storage) config options. Note,  I am not running Unity but legacy desktop. 

Questions
---------------------
1 What is doing the automounting of the device? 
2 Where are the default storage options?
3 Where would I make the change to mount my device with exec permissions if not in fstab? 
4. How do I uniquely identify each device as each might or might not be plugged in at any given time (so might be /dev/sdb1, or /dev/sdc1, etc)

Any help is much appreciated!

---

### Post by yy90 on 2013-03-29
I did find the following (only other change was relabelling it to MyBook without the space:

/dev/sdc1: LABEL="yy90-1tba" UUID="942d4aca-f6d6-4489-b58a-6ebccc192d22" TYPE="ext3" 
/dev/sdb1: LABEL="MyBook" UUID="F21843B31843759F" TYPE="ntfs" 

However, the fstab entry:
UUID=F21843B31843759F /media/MyBook    fuseblk rw,auto,blksize=4096,user,suid,dev,exec 0 0

Did not succeed. I got the error:

Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I had used fuseblk as the fs type as that's what it was successfully mounting as. Changing that to ntfs gave me another error:

Error mounting: mount exited with exit code 1: helper failed with:
WARNING: blksize option is ignored because ntfs-3g must calculate it.
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://tuxera.com/community/ntfs-3g-faq/#unprivileged](http://tuxera.com/community/ntfs-3g-faq/#unprivileged)

So I'm unclear what I can do next.  I want to be able to mount the device as a usr and have my scripts run on the fs.  Any help would really be appreciated!

---

