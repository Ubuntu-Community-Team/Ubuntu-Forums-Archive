---
title: "Webmin and can't use additional hard drive"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by david_brown on 2014-02-16
Hi, simple set up - old PC recycled as home server. Running 12.04.4 and the box is headless. I can access it by PuTTY and webmin. I have the OS on a separate small hard drive and have a 2TB drive I want to use for storage. 

The problem I have is that I can't see how to create a shared folder on this drive. On the Webmin home screen it says that 107Gb is used and 2.03Tb available, so it obviously recognises the disk somehow. In the option "Partitions on local disks" I see it as SATA Device C 1.86Tb formatted as Linux used by /home. In edit ide parameters (nothing changed!!) I can press check speed and it gives me a result so looks like it's working.In edit partition I can see the partition details as 


[TABLE="width: 100%"]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Location**[/TD]
[TD="class: ui_form_value, colspan: 1"]SCSI device C partition 1[/TD]
[TD="class: ui_form_label, align: right"]**Device file**[/TD]
[TD="class: ui_form_value, colspan: 1"]/dev/sdc1[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Type**[/TD]
[TD="class: ui_form_value, colspan: 1"]Linux[/TD]
[TD="class: ui_form_label, align: right"]**Extent**[/TD]
[TD="class: ui_form_value, colspan: 1"]1 - 243202 of 243201[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Status**[/TD]
[TD="class: ui_form_value, colspan: 1"]Mounted on /home as ext4[/TD]
[TD="class: ui_form_label, align: right"]**Size**[/TD]
[TD="class: ui_form_value, colspan: 1"]1.86 TB[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Filesystem label**[/TD]
[TD="class: ui_form_value, colspan: 1"]None


[/TD]
[/TR]
[/TABLE]
But when I come to create a Samba file share I just cannot find the flipping thing! I'm new to Ubuntu and on a VERY steep learning curve, so any help here is greatly appreciated.

---

### Post by jjk2 on 2014-02-16
hey david, 

welcome to ubuntu!

can you post the output of
```
sudo fdisk -l
```
and
```
sudo mount
```
and 
```
sudo df -h
```

it looks like the drive is working.
in linux (as opposed to windows) drives are mounted somewhere on the filesystem before you can use it.
It looks like your drive is mounted on the folder /home, which means that if you put files somewhere in the /home directory they are actually on the 2 tb hard drive.

btw:
i dont know webmin, but if i think you should set it up to use the /home folder somehow.

JJK

---

### Post by david_brown on 2014-02-16
Hi, and thanks for the welcome :)



root@ubuntu:/home/david# sudo fdisk -l


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8b32


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488396799   244197376   83  Linux


Disk /dev/sdb: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032f3f


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    35155967    17576960   83  Linux
/dev/sdb2        35158014    39069695     1955841    5  Extended
/dev/sdb5        35158016    39069695     1955840   82  Linux swap / Solaris


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0005cb16


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907028991  1953513472   83  Linux


Disk /dev/mapper/cryptswap1: 2002 MB, 2002780160 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3911680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d9ce7ed


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
root@ubuntu:/home/david#

****


root@ubuntu:/home/david# sudo mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda1 on /var type ext4 (rw)
/dev/sdc1 on /home type ext4 (rw,noexec,nosuid,nodev)
/home/david/.Private on /home/david type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=ec2e3b42011fa969,ecryptfs_fnek_sig=fbad765cea84b958)
root@ubuntu:/home/david#

**


root@ubuntu:/home/david# sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              17G  1.2G   15G   8% /
udev                  1.4G  4.0K  1.4G   1% /dev
tmpfs                 552M  936K  551M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.4G  8.0K  1.4G   1% /run/shm
/dev/sda1             230G  408M  218G   1% /var
/dev/sdc1             1.8T   68M  1.7T   1% /home
/home/david/.Private  1.8T   68M  1.7T   1% /home/david
root@ubuntu:/home/david#

Any of this help?

Thanks!

BTW, disk SDA is another drive I have in the box that I'm not worried about - just need to get one working for now. SDB is the OS drive and SDC is the 2TB one I'm trying to work with

---

### Post by david_brown on 2014-02-16
I *think* I have solved it. Logging into the server on a terminal window, mkdir /home/movies chmod 777 the new folder and it appears as a shared folder under windows 7. I'm currently copying the movies file across and way more than the OS sized disk has been coped so far, so it MUST be going onto the 2TB drive.

---

### Post by jjk2 on 2014-02-16
The disk /dev/sdc is the 2 tb one, and the partition /dev/sdc1 is the one you need.
it is correctly mounted at /home. 

So now i know for sure that everything you place inside the /home directory.

i think that means the problem is solved?

btw, better use code tags around blocks of code.

JJK

---

