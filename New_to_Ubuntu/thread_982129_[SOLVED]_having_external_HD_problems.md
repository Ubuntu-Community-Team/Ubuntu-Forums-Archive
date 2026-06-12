---
title: "[SOLVED] having external HD problems"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by scones on 2008-11-14
Ok so I am new to ubuntu and i just started using 8.4 and everything was working fine now i am runing 8.10 intreped and i no longer have permmision to my external hard drive or my 2gb USB stick. ok so to not be a pain on anyone i searched the forums and tried to fix it my self well now i can no longer mount my hard drive. I did use the live CD and it will mount but i do not have ownership as root does. I do not know what I did or how to fix it because the last time i tried it crached and i had to reinstall 8.10 i lost everything on my internal but that is ok i just want to get it back to working right. I am trying to fix my USD stick first just in-case something goes wrong.

ok so i took some screenshots (attachments) the first 2 are the error mesg. I get the next 2 are storage device manager where sda1 and sdb1 are coming up as the same device (I think there is a problem) 




next is the 
scones@scones-laptop:~$ sudo fdisk -l 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e3c3604

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11986    96277513+  83  Linux
/dev/sda2           11987       12161     1405687+   5  Extended
/dev/sda5           11987       12161     1405656   82  Linux swap / Solaris

Disk /dev/sdb: 2032 MB, 2032664576 bytes
255 heads, 63 sectors/track, 247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f1772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         247     1983996   83  Linux


then there is this
scones@scones-laptop:~$ sudo blkid
[sudo] password for scones: 
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="eea8fb28-37d0-4590-b34a-42a8f1fc7c14" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="c6b4740a-6f4d-4539-802c-b9b19327db4e" 
/dev/sdb1: UUID="7f38c1b0-e946-44cf-a1de-6ae6554d8314" SEC_TYPE="ext2" TYPE="ext3" 

thank you

---

### Post by taurus on 2008-11-14
Did you create a mount point, /media/sdb1, for it?

Applications -> Accessories -> Terminal
```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
df -h
```

---

### Post by scones on 2008-11-14
scones@scones-laptop:~$ sudo mkdir /media/sdb1
mkdir: cannot create directory `/media/sdb1': **File exists**
scones@scones-laptop:~$ sudo mount -t ext3 /dev/sdb1 /media/sdb1
mount: **mount point /media/sdb1 is not a directory**
scones@scones-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              91G  2.7G   84G   4% /
tmpfs                 235M     0  235M   0% /lib/init/rw
varrun                235M  104K  235M   1% /var/run
varlock               235M     0  235M   0% /var/lock
udev                  235M  2.7M  233M   2% /dev
tmpfs                 235M  400K  235M   1% /dev/shm
lrm                   235M  2.0M  233M   1% /lib/modules/2.6.27-7-generic/volatile

yes it says that it already exists but then says that mount point /media/sdb1 is not a directory

---

### Post by taurus on 2008-11-14
Can you post the output of this?

```
ls -la /media
```
What if you create a new mount point and see if you can mount it this time?

```
sudo mkdir /mnt/sdb1
sudo mount -t ext3 /dev/sdb1 /mnt/sdb1
df -h
```

---

### Post by scones on 2008-11-14
ok so creating a new mount point seems to work but I am back to the same problem that started this whole thing i do not have permmision to write it is in root


scones@scones-laptop:~$ sudo mkdir /mnt/sdb1
scones@scones-laptop:~$ sudo mount -t ext3 /dev/sdb1 /mnt/sdb1
scones@scones-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              91G  2.7G   84G   4% /
tmpfs                 235M     0  235M   0% /lib/init/rw
varrun                235M  104K  235M   1% /var/run
varlock               235M     0  235M   0% /var/lock
udev                  235M  2.7M  233M   2% /dev
tmpfs                 235M  400K  235M   1% /dev/shm
lrm                   235M  2.0M  233M   1% /lib/modules/2.6.27-7-generic/volatile
**/dev/sdb1             1.9G   35M  1.8G   2% /mnt/sdb1**


scones@scones-laptop:~$ ls -la /media
total 28
drwxr-xr-x  5 root root 4096 2008-11-14 12:56 .
drwxr-xr-x 20 root root 4096 2008-11-13 18:36 ..
lrwxrwxrwx  1 root root    6 2008-11-13 18:22 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-11-13 18:22 cdrom0
drwxr-xr-x  3 root root 4096 2008-11-14 11:17 disk
-rw-r--r--  1 root root   59 2008-11-14 12:56 .hal-mtab
-rw-------  1 root root    0 2008-11-14 12:55 .hal-mtab-lock
drwxr-xr-x  2 root root 4096 2008-11-13 19:45 sda5
-rw-r--r--  1 **root root**    5 2008-11-13 19:43 sdb1

---

### Post by taurus on 2008-11-14
> **scones said:**
> 
scones@scones-laptop:~$ ls -la /media
total 28
drwxr-xr-x  5 root root 4096 2008-11-14 12:56 .
drwxr-xr-x 20 root root 4096 2008-11-13 18:36 ..
lrwxrwxrwx  1 root root    6 2008-11-13 18:22 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-11-13 18:22 cdrom0
drwxr-xr-x  3 root root 4096 2008-11-14 11:17 disk
-rw-r--r--  1 root root   59 2008-11-14 12:56 .hal-mtab
-rw-------  1 root root    0 2008-11-14 12:55 .hal-mtab-lock
drwxr-xr-x  2 root root 4096 2008-11-13 19:45 sda5
**[COLOR="Blue"]-rw-r--r--  1 [B]root root**    5 2008-11-13 19:43 sdb1[/COLOR][/B]

There is your problem.  /media/sdb1 should be a directory, not a file.  So, you can remove /media/sdb1 (file) and create a directory /media/sdb1. 

```
sudo rm /media/sdb1
sudo mkdir /media/sdb1
```
Now, reboot.  Your /dev/sdb1 should now be mounted to /media/sdb1 if you have it as such in /etc/fstab.

```
df -h
```

And if you want to write to /media/sdb1 without using sudo/gksudo, then you can change the ownership of /media/sdb1 from root to your login name, scones.

```
sudo chown -R scones:scones /media/sdb1
ls -la /media
```

---

### Post by scones on 2008-11-14
thank you so much have been going through this for days and it looked so simple now hope i can remember how to do this for my 250gb drive now

---

