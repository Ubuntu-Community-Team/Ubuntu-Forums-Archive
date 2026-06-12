---
title: "[SOLVED] why cant I unmount partition #2?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-07-26
[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

2GB USB

The problem is with partition 2. What this tutorial is attempting to do is unmount partitions 1 and 2 before formatting the partitions. Step 8 works. Step 9 works. However in step 10  typing "umount /dev/sdb2"  it will tell you partition 2 is not found. Yet partition 2 clearly exists:

            start   End     blocks  ID System
/dev/sdb1p1   0     751     1466672  6 FAT 16
/dev/sdb1p2 752     1009    503874  83 Linux  

THanks

---

### Post by eightmillion on 2008-07-26
Can you post the outputs of "mount" and "ls /dev/sdb*"?

---

### Post by Lateforgym on 2008-07-26
How?

---

### Post by eightmillion on 2008-07-26
Open a terminal and type "mount" without quotations marks and hit enter. Do the same with "ls -l /dev/sdb*". Then copy the outputs and paste them here.

---

### Post by Lateforgym on 2008-07-26
It appears I have successfuly formatted partition 1 and named it ubuntu841
It still tells me partition 2 doesnt exist 

ubuntu@ubuntu:~$ **mount**
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/ubuntu841 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

ubuntu@ubuntu:~$ ls -l /dev/sdb*
brw-rw---- 1 root disk 8, 16 2008-07-26 10:55 /dev/sdb
brw-rw---- 1 root disk 8, 17 2008-07-26 10:55 /dev/sdb1

---

### Post by eightmillion on 2008-07-26
Ok, step 10 in the tutorial is just to make sure that this partition is not mounted. It's not, so you should go ahead with the next step and report if you have any errors.

---

### Post by Lateforgym on 2008-07-26
went to step #11 and got this error:

root@ubuntu:/home/ubuntu# umount /dev/sdb2
umount: /dev/sdb2: not found
root@ubuntu:/home/ubuntu# mkfs.ext2 -b 4096 -L Casper-rw /dev/sdb2
mke2fs 1.40.8 (13-Mar-2008 )
Could not stat /dev/sdb2 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
root@ubuntu:/home/ubuntu#

---

### Post by eightmillion on 2008-07-26
This is what I expected. For some reason only one partition was created on your flash drive. You're going to need to try the tutorial again starting from step 6. After you do step 6 run "ls /dev/sdb*". The output should be as follows...

[INDENT]
 root@ubuntu:# ls /dev/sdb*
/dev/sdb  /dev/sdb1  /dev/sdb2
[/INDENT]

---

### Post by Lateforgym on 2008-07-26
ok I got it. Im rather sleepy at this point. I was scared I would fdisk my HDD so I didnt follow step 7 properly and did "fdisk /dev/sdb1" when it should have been "fdisk /dev/sdb". 


THanks!!! Your the best!:popcorn:

---

### Post by eightmillion on 2008-07-26
Excellent. Glad I could help. :)

---

