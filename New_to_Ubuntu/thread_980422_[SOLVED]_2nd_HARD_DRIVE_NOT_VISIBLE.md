---
title: "[SOLVED] 2nd HARD DRIVE NOT VISIBLE"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by CarolinaGuy on 2008-11-12
How do I access the second hard drive in my SAMBA SERVER system. You can see that I have 2 hard drives (hda and hdd) as shown below. This is basically for getting familiar and setup until my new hard drive arrives at which time I will remove the 15G and replace it with a 1 terabyte drive.


charlie@ubuntu7:~$ su
Password:
root@ubuntu7:/home/charlie# fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000af620

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4865      747022+   5  Extended
/dev/hda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/hdd: 15.0 GB, 15000330240 bytes
16 heads, 63 sectors/track, 29065 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x18a52310

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       29065    14648728+  83  Linux
root@ubuntu7:/home/charlie#

In MY NETWORK PLACES I have these entries 

allusers on ubuntu7 server (Samba, Ubuntu) (Ubuntu7)

family on ubuntu7 server (Samba, Ubuntu) (Ubuntu7)

hda public hard disk on ubuntu7 server (Samba, Ubuntu) (Ubuntu7)


The second hard drive (hdd, 15g) does not SHOW UP.

The second hard drive was connected when UBUNTU 7.10 was loaded on the system. It has 1 partition, it is a linux partition.

I suspect that it requires formatting and /or a **[B]**MOUNT POINT or DIRECTORY [/B]created??

THANKS in advance.

CarolinaGuy

---

### Post by taurus on 2008-11-12
Can you mount the second harddrive, /dev/hdd1, as

```
sudo mkdir /media/hdd1
sudo mount -t ext3 /dev/hdd1 /media/hdd1
df -h
```

---

### Post by cdtech on 2008-11-12
Your correct, a mount point and also inserted within your /etc/fstab file:
```

# Entry for /dev/hdd :
/dev/hdd1 /mnt/hdd1 ext3 defaults,errors=remount-ro 0 1

```
then you can just run:
```
sudo mount -a
```

---

### Post by cdtech on 2008-11-12
Rule of thumb - Your /media directories are for auto mount devices and your /mnt are for created mounts. Such as your USB memory, external drives, they are named by device and HAL will use the device names for mount points within your /media partition.

---

### Post by CarolinaGuy on 2008-11-12
When I run sudo mount -t ext3 /dev/hdd1 I get this error.



root@ubuntu7:/home/charlie# sudo mkdir /media/hdd1
root@ubuntu7:/home/charlie# sudo mount -t ext3 /dev/hdd1 /media/hdd1
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu7:/home/charlie#


root@ubuntu7:/home/charlie# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  654M   34G   2% /
varrun                125M  184K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   68K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
root@ubuntu7:/home/charlie#



THANKS

CarolinaGuy

---

### Post by steveneddy on 2008-11-12
try this link from the links in my sig

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by CarolinaGuy on 2008-11-12
steveneddy

I'm not trying to mount a Windows partition on drive hdd. It partition an a linux partition and I trying to format it for either ext2 or ext3 file system. For some reason I keep getting this error:

root@ubuntu7:/home/charlie# sudo mount -t ext3 /dev/hdd1 /media/hdd1
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so 

CarolinaGuy

---

### Post by cdtech on 2008-11-12
Try:
```
sudo mount /dev/hdd1 /mnt/hdd1
```
From the "man" page:
> For most types all the mount program has to do is issue a simple mount(2) system call, and no detailed knowledge of the filesystem type is required.

---

### Post by CarolinaGuy on 2008-11-13
cdtech

THANKS for your help

I did as you suggested and received this:


root@ubuntu7:/home/charlie# fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000af620

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4865      747022+   5  Extended
/dev/hda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/hdc: 15.0 GB, 15000330240 bytes
16 heads, 63 sectors/track, 29065 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x18a52310

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       29065    14648728+  83  Linux

root@ubuntu7:/home/charlie# sudo mount /dev/hdc1 /mnt/hdc1
mount: mount point /mnt/hdc1 does not exist
root@ubuntu7:/home/charlie#


CarolinaGuy

---

### Post by taurus on 2008-11-13
You need to create a mount point first before you can mount a device to it.

```
sudo mkdir /mnt/hdc1
```

---

### Post by CarolinaGuy on 2008-11-13
taurus,

THANKS for your assistance; still no-go; see listing.

Password:
root@ubuntu7:/home/charlie# fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000af620

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4865      747022+   5  Extended
/dev/hda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/hdc: 15.0 GB, 15000330240 bytes
16 heads, 63 sectors/track, 29065 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x18a52310

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       29065    14648728+  83  Linux

root@ubuntu7:/home/charlie# sudo mkdir /mnt/hdc1
mkdir: cannot create directory `/mnt/hdc1': File exists
root@ubuntu7:/home/charlie#
root@ubuntu7:/home/charlie#

I have done a lot of reading and research. I'm stumped.

CarolinaGuy

---

### Post by CarolinaGuy on 2008-11-14
tauras, cdtech and steveneddy,

I really appreciate each of you taking the time to help me.

I have made some progress but I still don't see the second drive listed under My network places.


To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Fri Nov 14 18:05:16 2008 from 192.168.1.101
charlie@ubuntu8:~$ su
Password:
root@ubuntu8:/home/charlie# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  743M   34G   3% /
varrun                125M  164K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   56K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
/dev/sdb1              14G  164M   13G   2% /storage
/dev/sdb1              14G  164M   13G   2% /media
root@ubuntu8:/home/charlie#

CarolinaGuy

---

### Post by taurus on 2008-11-14
> **CarolinaGuy said:**
> 
root@ubuntu8:/home/charlie# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  743M   34G   3% /
varrun                125M  164K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   56K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
[B][COLOR="Blue"]/dev/sdb1              14G  164M   13G   2% /storage
/dev/sdb1              14G  164M   13G   2% /media[/COLOR][/B]
root@ubuntu8:/home/charlie#

CarolinaGuy

WoW!  Don't need to mount the same drive, /dev/sdb1, at two different locations: /storage & /media.  You can unmount one of them.

```
sudo umount /media
```

However, I don't see any /dev/sdb from your output of fdisk -l!  What's the output of this command?

```
sudo blkid
```

Bet /dev/sdb1 is actually /dev/hdc1 since both are 15GB.

---

### Post by CarolinaGuy on 2008-11-14
taurus

THANKS again, here the output


root@ubuntu8:/home/charlie# sudo blkid
/dev/sda1: UUID="9d4d3b01-9796-42af-90ee-ad9f4e8b53ab" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="fb4be99e-0238-4325-a95b-94e22a789c38"
/dev/sdb1: UUID="174cd9df-7dd8-46a2-8154-8b8ad4a384f3" TYPE="ext3"
root@ubuntu8:/home/charlie#



root@ubuntu8:/home/charlie# sudo umount /media
root@ubuntu8:/home/charlie# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  744M   34G   3% /
varrun                125M  172K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   56K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
/dev/sdb1              14G  167M   13G   2% /storage
root@ubuntu8:/home/charlie#

UNMOUNT DONE!!!


CarolinaGuy

---

### Post by taurus on 2008-11-14
Does "174cd9df-7dd8-46a2-8154-8b8ad4a384f3" look like the UUID in /etc/fstab for /dev/sdb1--/storage?

```
cat /etc/fstab
```
I think everything is fine for you now.  The only thing left is if you want to be able to write to /storage without using sudo or becoming root, you can change the ownership if /storage from root to your login name, charlie.

```
sudo chown -R charlie:charlie /storage
ls -la /storage
```

---

### Post by CarolinaGuy on 2008-11-14
taurus,

Again Thanks.

Does "174cd9df-7dd8-46a2-8154-8b8ad4a384f3" look like the UUID in /etc/fstab for /dev/sdb1--/storage?


Yes, this is sdb1.

Other commands executed. Thanks for all your help.

CarolinaGuy

---

### Post by taurus on 2008-11-14
Okay, you are all set then.  Enjoy your new /storage space.

---

### Post by steveneddy on 2008-11-15
> **CarolinaGuy said:**
> steveneddy

I'm not trying to mount a Windows partition on drive hdd. It partition an a linux partition and I trying to format it for either ext2 or ext3 file system. For some reason I keep getting this error:

root@ubuntu7:/home/charlie# sudo mount -t ext3 /dev/hdd1 /media/hdd1
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so 

CarolinaGuy

The steps are the same if you just read the directions.

The tutorial will teach you to mount any partition, windows or not, in your Ubuntu installation.

---

