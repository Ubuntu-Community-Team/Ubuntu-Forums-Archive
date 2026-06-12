---
title: "Post boot internal /non-os/storage/ drive renme&quot;foo&quot;/ &gt; &quot;foo1&quot;/'foo2&quot;-Why?How to Stop"
date: 2015-10-22
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2015-10-22
thanks for reading. 
Questions, (random, can't determine "why") but 

My Internal non-os drives (FATMAN is a partition). 
These Drives are renaming themselves appending a 1,2.3 to the name. 

Why is this occurring and how can I stop/prevent in future? 
(the problem is it fubs my backups as I need an absolute path. *sigh* for backup. 

THANKS!

****
```

IF IT MATTERS....
"FATMAN" is a Partition of /dev/sda

"SATURN" is a 2nd (IDE) SATA drive /dev/sdb

see screen shot. 

(LACIEPAPPY IS AN EXTRAL USB 2TB DRIVE). "LARGE DRIVE" (not key). 

```

I've been simply deleting the "empty"/"wrong" drive(s) named...but tired of doing that. 
Thx.

---

### Post by buzzingrobot on 2015-10-22
No clue, really, but they wouldn't rename themselves.  Something  might execute once a day, make a copy, and append an integer in sequence to create a unique name. 

Curious that they're all shown as 4.1kb folders.  Are there files inside?  Identical files?

---

### Post by tgalati4 on 2015-10-23
Post your /etc/fstab.  Without hard mounts at boot, partitions (file systems) will get named by the kernel (most likely gnome virtual file system--gvfs) and it will store the metadata, including the name.  If something changes to that file system, it will get remounted and given a new name so as not to conflict with with an existing mount.

Is this a dual-boot system?  It's possible that booting into the non-linux operating system is doing something to the partition so it looks different each time.

---

### Post by whereismymindat2 on 2015-11-29
Hey Guys, Thanks for reply
Here is my fasttab (blkid formated) and the mtab

SO FAR, it looks like "friendly-recovery" is my answer. I have used it, and it seems to keep it from appending the number to it. 

Also, I too am curious why *********ALL MY FILES********* FOLDERS (report that size) It's been this way since I first installed XUbuntu and (even reinstalls,etc.). 
Any advice, greatly appreciated. 

```

root@Dawg:~# blkid
/dev/sda1: UUID="0062ef42-dde7-4c20-ae98-3c8737e2310b" TYPE="ext4" 
/dev/sda2: UUID="3cef394d-d973-421a-84bf-09713c825a50" TYPE="ext4" 
/dev/sda3: UUID="a071dd41-fd99-435c-acff-33b989416c37" TYPE="ext4" 
/dev/sda4: UUID="51fc86b5-1cd5-4836-bd37-37861a8dc1b1" TYPE="swap" 
/dev/sda5: UUID="23063667-64b2-4855-816d-9ff3d2b70eec" TYPE="ext4" 
/dev/sda6: LABEL="FATMAN" UUID="1a87a354-4a9c-45d8-aa04-b6057404b263" TYPE="ext4" 
/dev/sda7: UUID="ce592891-af33-4216-b749-dd4c91eed22c" TYPE="ext4" 
/dev/sda8: UUID="4bb5a0f7-8cb3-4156-b824-06a23501a8cc" TYPE="ext4" 
/dev/sda10: LABEL="HOME" UUID="bbcdf444-f56d-444c-84ab-86e5e9de4ab9" TYPE="ext4" 
/dev/sda11: UUID="418d0b5c-fd32-40b3-b1f5-d589df04d29c" TYPE="ext4" 
/dev/sda14: UUID="0c216394-3e37-4911-92d3-d84748549d38" TYPE="ext4" 
/dev/sdb1: LABEL="SATURN" UUID="d251cebb-08f1-4220-9dca-528844fe0a45" TYPE="ext4" 
/dev/sdc1: LABEL="LACIEPAPPY" UUID="642905D54A5F6BD2" TYPE="ntfs" 




```



```

MTAB
/dev/sda7 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
none /sys/fs/pstore pstore rw 0 0
/dev/sda2 /boot ext4 rw 0 0
/dev/sda10 /home ext4 rw 0 0
/dev/sda11 /var ext4 rw 0 0
/dev/sda3 /tmp ext4 rw 0 0
/dev/sda5 /opt ext4 rw 0 0
/dev/sda8 /srv ext4 rw 0 0
/dev/sda1 /usr ext4 rw 0 0
/dev/sda14 /usr/local ext4 rw 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=bender 0 0
/dev/sdb1 /media/bender/SATURN ext4 rw,nosuid,nodev,uhelper=udisks2 0 0
/dev/sda6 /media/bender/FATMAN ext4 rw,nosuid,nodev,uhelper=udisks2 0 0
/dev/sdc1 /media/bender/LACIEPAPPY fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=512 0 0


```

---

