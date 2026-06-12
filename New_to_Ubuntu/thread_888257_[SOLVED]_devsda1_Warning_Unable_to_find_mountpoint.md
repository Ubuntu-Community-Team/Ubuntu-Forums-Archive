---
title: "[SOLVED] /dev/sda1 Warning: Unable to find mountpoint"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by MooseMagnet on 2008-08-12
/dev/sda1 in GParted says "Warning: Unable to find mountpoint?
and
/dev/sda1 does NOT appear in System Monitor > File Systems

I recently had a failure, and rebuilt from the Feisty 7.04 CD, then used rsync to restore everything.

Have I done something wrong? It doesn't seem right.

When the system failed, it said "not enough disk space," and it would not boot. So, I started from scratch. It seems to be working okay. But this info about /dev/sda1 does not look correct.

Do I still have a problem?

Thank you

---

### Post by tamoneya on 2008-08-12
what are the results of the following commands:```
cat /etc/fstab
sudo fdisk -l
sudo umount /dev/sda1
```

---

### Post by MooseMagnet on 2008-08-13
rich@rich-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=536f21dd-c960-4e4c-bbb0-620549294d6e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=97a7e51f-c176-4176-947d-6749b2b1bbc9 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0rich@rich-laptop:~$ 

------------------------------------

rich@rich-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7111    57119076   83  Linux
/dev/sda2            7112        7296     1486012+   5  Extended
/dev/sda5            7112        7296     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux
rich@rich-laptop:~$ 

-------------------------------------------

rich@rich-laptop:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
rich@rich-laptop:~$

---

### Post by tamoneya on 2008-08-13
it seems like the device node naming got messed up.  Lets confirm though:```
sudo blkid /dev/sda1
```
If it is something other than : 536f21dd-c960-4e4c-bbb0-620549294d6e then it means that the IDs got messed up.

---

### Post by MooseMagnet on 2008-08-13
rich@rich-laptop:~$ sudo blkid /dev/sda1
/dev/sda1: UUID="4b965817-e3ad-4e72-8905-81f851c5662d" SEC_TYPE="ext2" TYPE="ext3" 
rich@rich-laptop:~$ 



I'm really flying blind here. Trying my best to understand it.

---

### Post by MooseMagnet on 2008-08-13
One more.

rich@rich-laptop:~$ ls /dev/disk/by-uuid/ -l
total 0
lrwxrwxrwx 1 root root 10 2008-08-12 15:22 4b965817-e3ad-4e72-8905-81f851c5662d -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-08-12 15:22 97a7e51f-c176-4176-947d-6749b2b1bbc9 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-08-12 21:54 f84273db-f3fe-4c63-98f2-669f7e13bcb4 -> ../../sdb1
rich@rich-laptop:~$

---

### Post by tamoneya on 2008-08-13
> **MooseMagnet said:**
> rich@rich-laptop:~$ sudo blkid /dev/sda1
/dev/sda1: UUID="4b965817-e3ad-4e72-8905-81f851c5662d" SEC_TYPE="ext2" TYPE="ext3" 
rich@rich-laptop:~$ 



I'm really flying blind here. Trying my best to understand it.

Okay let me explain.  The UUID is used to identify the drive.  the file /etc/fstab is used to automount partitions when the OS boots.  It is referencing a UUID but something got changed around (dont know why so dont ask).  So what we can do is change the UUID in fstab.  So replace 536f21dd-c960-4e4c-bbb0-620549294d6e with 4b965817-e3ad-4e72-8905-81f851c5662d.  To edit fstab run this: ```
gksudo gedit /etc/fstab
```

You should also check /dev/sda5.  Basically run through the entire process again but modifying the second UUID in fstab and replacing /dev/sda1 with /dev/sda5

---

### Post by MooseMagnet on 2008-08-13
I changed the UUID for /dev/sda1 and restarted. It seems okay now. Before this fix, the pic icons were blue boxes instead of the small pic. They are the small pic again. /dev/sda1 looks okay in GParted and System Monitor > File Systems.

Is this correct now?

rich@rich-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=4b965817-e3ad-4e72-8905-81f851c5662d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=97a7e51f-c176-4176-947d-6749b2b1bbc9 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
rich@rich-laptop:~$ 

---------------------------

Looking in GParted and System Monitor > File Systems, /dev/sda5 looks okay.

I'm not sure what you're suggesting I do with /dev/sda5. Change its UUID also?

---

### Post by tamoneya on 2008-08-13
looks much better.  Tell me what this output is:```
sudo blkid /dev/sda5
```
Then I can tell you if there is a problem with /dev/sda5 as well.

---

### Post by MooseMagnet on 2008-08-14
rich@rich-laptop:~$ sudo blkid /dev/sda5
Password:
/dev/sda5: TYPE="swap" UUID="97a7e51f-c176-4176-947d-6749b2b1bbc9" 
rich@rich-laptop:~$

---

### Post by tamoneya on 2008-08-14
> **MooseMagnet said:**
> rich@rich-laptop:~$ sudo blkid /dev/sda5
Password:
/dev/sda5: TYPE="swap" UUID="97a7e51f-c176-4176-947d-6749b2b1bbc9" 
rich@rich-laptop:~$

Okay that UUID matches correctly.  It seems to me as if you are all set.  If you could mark thread as solved in the thread tools menu to the upper right of your first post that would be awesome.

Thanks

---

