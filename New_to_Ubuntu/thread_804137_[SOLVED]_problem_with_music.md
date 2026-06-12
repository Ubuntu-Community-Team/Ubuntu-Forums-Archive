---
title: "[SOLVED] problem with music"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by stalkier on 2008-05-22
Ok it isn't really a problem. Here is what I want to do.

I either need to add my additional hdd (IDE) to the fstab (I have no idea how) to get it to automount. OR I need to copy my mp3 folder to my filesystem. I would just copy the folder to my home directory but I setup my system using 3 partitions. (a /root,/home, and a swap). The home directory only has 5GB free. The mp3 folder is 14GB.

I am forgetting to mount my hdd and when I startup Amarok it goes retarted on me and then I have to "find" all my mp3 files again. 

If you have any suggestions other than what I have above then I would be glad to read them. I am still learning Linux commands etc and am using Ubuntu 8.04 as a primary OS now. Thanks.

---

### Post by iaculallad on 2008-05-22
> **stalkier said:**
> Ok it isn't really a problem. Here is what I want to do.

I either need to add my additional hdd (IDE) to the fstab (I have no idea how) to get it to automount. OR I need to copy my mp3 folder to my filesystem. I would just copy the folder to my home directory but I setup my system using 3 partitions. (a /root,/home, and a swap). The home directory only has 5GB free. The mp3 folder is 14GB.

I am forgetting to mount my hdd and when I startup Amarok it goes retarted on me and then I have to "find" all my mp3 files again. 

If you have any suggestions other than what I have above then I would be glad to read them. I am still learning Linux commands etc and am using Ubuntu 8.04 as a primary OS now. Thanks.

To automount your other drive, you can insert this line of text on your /etc/fstab file (at the bottom-most of the file).

**/dev/sda2 /media/sda2 ntfs defaults,umask=007,gid=46 0 1**

just replace the sda2 with the drive that corresponds to your own drive.

**sudo gedit /etc/fstab**

---

### Post by stalkier on 2008-05-22
No good. It won't automount. :( 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9492fca5-2901-42a2-9e1c-39722f161e93 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=58bfea79-ed14-4f42-a92f-8fb7ddd86f1f /home           ext3    relatime        0       2
# /dev/sda3
UUID=5a6048c7-8f4e-442e-b5df-7d8ed7d0aef6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda2 /media/sdb1 ntfs defaults,umask=007,gid=46 0 1

---

### Post by iaculallad on 2008-05-22
> **stalkier said:**
> No good. It won't automount. :( 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9492fca5-2901-42a2-9e1c-39722f161e93 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=58bfea79-ed14-4f42-a92f-8fb7ddd86f1f /home           ext3    relatime        0       2
# /dev/sda3
UUID=5a6048c7-8f4e-442e-b5df-7d8ed7d0aef6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda2 /media/sdb1 ntfs defaults,umask=007,gid=46 0 1

Post your fstab, so we know what to automount:
[B]
sudo fstab -l[/B]

(that's small L)

---

### Post by stalkier on 2008-05-22
john@john-desktop:~$ sudo fstab -l
sudo: fstab: command not found
john@john-desktop:~$

---

### Post by iaculallad on 2008-05-22
> **stalkier said:**
> john@john-desktop:~$ sudo fstab -l
sudo: fstab: command not found
john@john-desktop:~$

My mistake (doing three jobs at a time), make that  :-)

sudo fdisk -l

---

### Post by stalkier on 2008-05-22
Not a problem buddy. I appreciate your help.

> john@john-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8122

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3650    29318593+  83  Linux
/dev/sda2            3651        4500     6827625   83  Linux
/dev/sda3            4501        4865     2931862+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f573ac5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9963    80027766    7  HPFS/NTFS
john@john-desktop:~$ 


---

### Post by iaculallad on 2008-05-22
Try this:

**sudo mkdir /media/windrive**

sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab

and paste this line of the very end of fstab file

/dev/sdb1 /media/windrive ntfs defaults,umask=007,gid=46 0 1

then restart

---

### Post by stalkier on 2008-05-22
> **iaculallad said:**
> Try this:

**sudo mkdir /media/windrive**

sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab

and paste this line of the very end of fstab file

/dev/sdb1 /media/windrive ntfs defaults,umask=007,gid=46 0 1

then restart

Thank you mt friend. It works like a charm. I thought it didn't work at first because it did not have a icon on the desktop. It did work though and I imported my mp3 folder once again and then restarted to see if it stuck. It did indeed. Thanks again for your time.

---

### Post by iaculallad on 2008-05-22
> **stalkier said:**
> Thank you mt friend. It works like a charm. I thought it didn't work at first because it did not have a icon on the desktop. It did work though and I imported my mp3 folder once again and then restarted to see if it stuck. It did indeed. Thanks again for your time.

No problem, You're very much welcome. Go Ubuntu.

---

