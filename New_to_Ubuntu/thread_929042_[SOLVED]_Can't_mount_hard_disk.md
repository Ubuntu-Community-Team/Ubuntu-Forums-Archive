---
title: "[SOLVED] Can't mount hard disk"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by hellomoto on 2008-09-24
Hopfully this will be an easy problem to solve....

I have just added a new 60gb Hard Disk into my xubuntu box. 
Seams to be connected up fine and is set to act as a slave disk. 

But I can't seam to see the hard disk when I load my OS. Im aware I have to mount it but I can't even see it to mount. 

I know its formatted to NTFS (i just had it as an 2nd HD in a windows PC). 

So where should the HD apear in xubuntu if its been installed correctly? And how do I mount it?

Thankyou!

---

### Post by Elfy on 2008-09-24
check that it's there with ```
sudo fdisk -l
``` , you could add it to fstab if you wanted it to mount at startup

alternatively you could mount it as and when you needed it

---

### Post by hellomoto on 2008-09-24
its there, 

```



Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a96af06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7297    58613121    7  HPFS/NTFS
mark@ubuntu:~$ sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
mark@ubuntu:~$ 

```

Do you know the command to mount this.

Many Thanks

---

### Post by Elfy on 2008-09-24
If you wan to just mount it once, you'll need to have somewher of it to mount - either in /media ( in which case it might show on the desktop - not usre with xubuntu) or /mnt where it won't

make a folder ```
sudo mkdir /mnt/disk
``` and then mount the drive in there ```
sudo mount -t ntfs /dev/sdb1 /mnt/disk
```

You could change disk as long as it's the saem in each command, do you want it to mount each time you boot?

---

### Post by hellomoto on 2008-09-24
heya, thaqt worked great, ty.

Yes I would like it to mount every time. Could you please let me know what I have to be in the fstab file?

I would like the disk to be nameed hd2 if possible. 

Thankyou

---

### Post by drs305 on 2008-09-24
Another option for NTFS drives is ntfs-config. Install it and the first time you run it (System Tools, NTFS Configuration Tool) it will ask for the desired mountpoint and then configure the partition for read/write using ntfs-3g.

Install it with the command:
```
sudo apt-get install ntfs-config
```

Another useful tool is ntfsprogs, which includes several apps, one of which will allow you to easily label ntfs partitions.

---

### Post by Elfy on 2008-09-24
Ok - I'll go with mounting it in /mnt if you want it in media then change it

```
sudo mkdir /mnt/hd2
```
Open fstab to edit
```
gksudo mousepad /etc/fstab
```
add this line to fstab

```
/dev/sdb1       /mnt/hd2 ntfs-3g auto,rw,utf8   0       0
```
Save it, now unmount from the old folder and remount in new one, alos remove the old folder

```
sudo umount /mnt/disk
sudo mount -a
```
As long as that has completed without error run, if there is an erro please post whole thing here including commnds

```
sudo rm -r /mnt/disk
```

---

### Post by hellomoto on 2008-09-24
I would rather mount it via fstab but I just can't rember what I need to put in.

---

### Post by Elfy on 2008-09-24
ntfs-config does add it to fstab - I wasn't sure however of where it would go in the xubuntu menus :) so did the 'hard' way

---

### Post by hellomoto on 2008-09-24
just one error

```

[mntent]: warning: no final newline at the end of /etc/fstab

```

---

### Post by Elfy on 2008-09-24
Mmmm not seen that one - can you post

```
cat /etc/fstab
```

Edit - before that - edit the file again, go to end of last line and enter then save and close, try the mount -a command again.

---

### Post by hellomoto on 2008-09-24
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cf6dc38d-660b-49ff-a37a-95c6e44d0a5f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=69dce69e-0564-44b6-b796-e3c533a26455 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /mnt/hd2 ntfs-3g auto,rw,utf8   0       0mark@ubuntu:~$ 


```

---

### Post by Elfy on 2008-09-24
Did you edit it and add a blank line to the bottom - if so it should be ok now. Youc an make sure it's mounted with ```
df -h
```

---

### Post by drs305 on 2008-09-24
> **hellomoto said:**
> 
/dev/sdb1       /mnt/hd2 ntfs-3g auto,rw,utf8   0       0**mark@ubuntu:~$ **


If that line is actually in your fstab due to a cut/paste error (or any other reason, actually), remove the part in bold.
```

/dev/sdb1       /mnt/hd2 ntfs-3g auto,rw,utf8   0       0

```

---

### Post by hellomoto on 2008-09-24
welll i don't know what that error was but i restarted the PC and the HD mounts every time! so many thanks for your help! Couldn't of done it with out you!

---

### Post by Elfy on 2008-09-24
catch drs305 - didn't see that :)

---

### Post by lwvmobile on 2008-09-24
Here is the lines I used to mount in fstab if it helps you.

```
/dev/hde1	/media/STT120NTFS	ntfs
/dev/sdb1	/media/STT320NTFS	ntfs

```

Just that simple in Hardy. Feel free to tab inbetween each thing though, and If you want the icon on the desktop put it in media and be sure to create the folders you intend to use in media first using the mkdir command.

:popcorn:

---

