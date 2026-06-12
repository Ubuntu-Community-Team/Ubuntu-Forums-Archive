---
title: "oh oh do i have to reinstall? recover??"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Daverobb on 2008-07-14
i've been trying to change my read/write permissions on my usb/bluetooth mounted flash drive and having problems for a long time now but ...

last night i changed a line from the /etc/fstab file by mistake - I think it was my primary (ubuntu) drive and i changed the entry [error= -ro] to [errror= -rw] 

this morning it says it can't load the xfile and the error string looks like it can't write to the primary disk and so won't go into the GUI.  So, I can get into recovery mode but i don't know how to change that line back to the original to see if that fixes it.

if someone can help me through this one i'd be be time happy!!

---

### Post by YaroMan86 on 2008-07-14
Do you know exactly what change you made the the fstab on accident?

---

### Post by Daverobb on 2008-07-14
sorry - that command i changed was [error=remount-rw] from [error=remount-ro]

---

### Post by YaroMan86 on 2008-07-14
Simply change it back to the way it was.

Also, remember it's usually a good idea to back up the fstab before changing it manually. This command will do it:

```

sudo cp /etc/fstab /etc/fstab_backup

```

That way, when things go sour, you can just delete the messed up fstab and rename the backed up fstab. This is done from the LiveCD or another Linux install, of course:

```

sudo rm /etc/fstab
sudo mv /etc/fstab_backup /etc/fstab

```

---

### Post by sisco311 on 2008-07-14
You can edit the file with nano(from recovery mode):
```
nano /etc/fstab
```Ctrl+o Enter = save
Ctrl+x = exit
Ctrl+x Y Enter = save and exit

The default options for the "/" (root) partition are: *relatime,errors=remount-ro*

---

### Post by Daverobb on 2008-07-14
# /dev/sda1
UUID=a453e473-6f4b-4102-8841-4320b0d4bd50 / ext3 defaults,errors=remount-rw 0 1


this is the line but i found it in another post because i'm not at home now but i can only get to it through terminal on recovery mode later

---

### Post by Daverobb on 2008-07-14
thanks!

---

### Post by sisco311 on 2008-07-14
> **Daverobb said:**
> # /dev/sda1
UUID=a453e473-6f4b-4102-8841-4320b0d4bd50 / ext3 defaults,errors=remount-rw 0 1


this is the line but i found it in another post because i'm not at home now but i can only get to it through terminal on recovery mode later
from a terminal you need to rum the command as root:
```
sudo nano /etc/fstab
```
(in recovery mode you are logged in as root)

---

### Post by YaroMan86 on 2008-07-14
No need for sudo when in the recovery console. You're already root.

---

### Post by sisco311 on 2008-07-14
> **YaroMan86 said:**
> No need for sudo when in the recovery console. You're already root.
Sorry, I misread the OP's post.
I thought he/she can boot to a (non-root) virtual terminal.

---

### Post by ajgreeny on 2008-07-14
Just a thought;  how did you edit the fstab file in the first place?  If you used gedit there may well be a backup file (fstab~) in /etc with the appropriate date so you will know it is the right one.  If there is one, check its contents with ```
cat /etc/fstab
``` in recovery mode, and if it is the correct one you can just restore it by renaming the current fstab ```
mv /etc/fstab /etc/fstab.bak
``` and then renaming the fstab~ to fstab in a similar manner with ```
mv /etc/fstab~ /etc/fstab
```

---

### Post by Daverobb on 2008-07-14
ok -- got into recovery mode and then into nano -- edited the file but it wouldn't let me save - error message was that /etc/fstab was read only.

---

### Post by sisco311 on 2008-07-14
try to remount the partition (rw):
```
mount /dev/sd?? -o remount,defaults
```/dev/sd?? = use the *mount* command to find the "name" of the partition
(EDIT: it's in the fstab 
**#/dev/sd??**
UUID=.... / ext3 ..).
or boot with the live cd, mount the partition and edit the file:
```
gksu gedit /media/*MOUNTPOINT*/etc/fstab
```

---

### Post by Daverobb on 2008-07-14
> **sisco311 said:**
> try to remount the partition (rw):
```
mount /dev/sd?? -o remount,defaults
```/dev/sd?? = use the *mount* command to find the "name" of the partition
(EDIT: it's in the fstab 
**#/dev/sd??**
UUID=.... / ext3 ..).
or boot with the live cd, mount the partition and edit the file:
```
gksu gedit /media/*MOUNTPOINT*/etc/fstab
```
so the 

[mount /dev/sd?? -o remount,defaults]

command will find the device itself?  I'm not sure if that's what you are saying or if I should just enter it -- i'm pretty sure it is /dev/sdb1

---

### Post by sisco311 on 2008-07-14
> **Daverobb said:**
> so the 

[mount /dev/sd?? -o remount,defaults]

command will find the device itself?  I'm not sure if that's what you are saying or if I should just enter it -- i'm pretty sure it is /dev/sdb1

then use: mount /dev/sdb1 -o remount,defaults

---

### Post by Daverobb on 2008-07-14
did it -- here was the error message:

```

[135.678938] EXT3-fs: unrecognized mount option "errors=remount-rw" or missing value
mount: /not mounted already, or bad option

```

---

### Post by Daverobb on 2008-07-14
am using the live cd now

got to terminal

when i ```
ubuntu@ubuntu:~$ gksu gedit /media/MOUNTPOINT/etc/fstab

```

then there is nothing there - obviously because i'm in the live cd but how do i edit the original line?  how can i mount the drive?

---

### Post by sisco311 on 2008-07-14
try:
```
sudo mount /dev/sdb1 /mnt -t ext3
gksu gedit /mnt/etc/fstab
```

---

### Post by Daverobb on 2008-07-14
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt -t ext3
mount: special device /dev/sdb1 does not exist
```

??

---

### Post by sisco311 on 2008-07-14
you can use 
```
sudo fdisk -l
```to list your partition.

maybe it's sd**a**1:
```
sudo mount /dev/sda1 /mnt -t ext3
...
```

---

### Post by Daverobb on 2008-07-14
I guess I was wrong before because this is what comes out:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.9 GB, 40982151168 bytes
240 heads, 63 sectors/track, 5293 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         611     4619128+  12  Compaq diagnostics
/dev/hda2   *         612        5293    35395920    7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe14d0055

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19080   153260068+  83  Linux
/dev/hdb2           19081       19457     3028252+   5  Extended
/dev/hdb5           19081       19457     3028221   82  Linux swap / Solaris

```

and it looks like it's /dev/hdb1(?)

I know that i changed the file in what appeared to be /dev/sdb1

should i mount it?

---

### Post by sisco311 on 2008-07-14
hdb1 is the ubuntu partition:
```
sudo mount /dev/hdb1 /mnt -t ext3
gksu gedit /mnt/etc/fstab
```

---

### Post by Daverobb on 2008-07-14
Got it - here is the saved file 

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=dda2ffed-bb6f-49fc-b71e-a82b8c5e84cf / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=8f5368e0-4e5d-4d68-8136-c98c8cb78c57 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/sda2 /media/HP_PAVILION ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Any thoughts?

my original problem was that I couldn't get an ntfs phone/mp3 drive to write files to, only delete from.

---

### Post by sisco311 on 2008-07-14
looks ok, but check the UUID:
```
sudo vol_id -u /dev/hdb1
```
if it's
> dda2ffed-bb6f-49fc-b71e-a82b8c5e84cf
reboot.

---

### Post by Daverobb on 2008-07-14
rebooted and it works!!

ran th fdisk -l command and it now appears as /dev/sdb1 

obviously i'm way too new to this but why?  just interested in learning about it

---

### Post by sisco311 on 2008-07-14
[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]In recent kernels both PATA and SATA (SCSI too) drives are handled by libata  
library. It calls all the drives sd* .

Did you use an old live cd?  (Dapper?)

[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by Daverobb on 2008-07-14
oh yes, just noticed it was 7.10 -- that explains it

---

### Post by Daverobb on 2008-07-14
thanks again -- i'll keep trying to figure out the drive permission issues i've had but with backing up!

---

