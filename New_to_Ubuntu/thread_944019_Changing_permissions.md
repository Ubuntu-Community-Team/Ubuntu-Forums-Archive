---
title: "Changing permissions"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Commander_Keen on 2008-10-10
Question.
  how would I change permissions File/Folder located on a 2nd Drive/partition.
  It needs to go Root to Group/jrothschild (?) and from Read only to read & write.

---

### Post by sokopok on 2008-10-10
to change the owner of a file:
sudo chown username:groupname filename

to change permissions:
sudo chmod u+rw filename

or via file manager (nautilus or dolphin): right click the folder and change the owner/permissions there. You need to be root to change owner/permission of a file owned by root, so start nautilus using:
gksudo nautilus

---

### Post by bodhi.zazen on 2008-10-10
Changing ownership and permissions depends on the file system. The command sokopok gave you will work on any linux native file system (ext 2 / 3 , reiserfs, etc) but not Windows partitions (FAT or NTFS).

For FAT and NTFS you set ownership at the time of mounting:

mount /dev/sdxy /media/mount_point -o uid=1000,gid=100,umask=007

---

### Post by Commander_Keen on 2008-10-11
> **bodhi.zazen said:**
> Changing ownership and permissions depends on the file system. The command sokopok gave you will work on any linux native file system (ext 2 / 3 , reiserfs, etc) but not Windows partitions (FAT or NTFS).

For FAT and NTFS you set ownership at the time of mounting:

mount /dev/sdxy /media/mount_point -o uid=1000,gid=100,umask=007

-------------------------------------------
Here is my copy of my fstab
How do I add your lines to my fstab?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=449a2a16-e64c-4388-a94d-9bab0bc784ed /               reiserfs notail,relatime 0       1
# /dev/sda2
UUID=1a8b641c-99d9-4954-b62f-0b098f143c68 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda4      /media/Application  vfat user,auto,fmask=01111,dmask=0000
/dev/sda3      /media/Backup       vfat user,auto,fmask=01111,dmask=0000

---

### Post by unutbu on 2008-10-11
To edit fstab:```

gksu gedit /etc/fstab

```
Perhaps try something like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=449a2a16-e64c-4388-a94d-9bab0bc784ed /               reiserfs notail,relatime 0       1
# /dev/sda2
UUID=1a8b641c-99d9-4954-b62f-0b098f143c68 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda4      /media/Application  vfat user,auto,fmask=01111,dmask=0000 [COLOR="Red"]0 2[/COLOR]
/dev/sda3      /media/Backup       vfat user,auto,fmask=01111,dmask=0000 [COLOR="Red"]0 2[/COLOR]
[COLOR="Red"]/dev/sdb1      /media/mount_point  vfat uid=1000,gid=1000,umask=007 0 2[/COLOR]

```

Changes have been marked in red. 
Each line of the fstab (which is not commented out with a # sign) must have 6 space-separated fields. Your lines for /media/Application and /media/Backup would not work since they each contained only 4 fields.

Change /dev/sdb1 to the correct device name for the partition you wish to mount.

Change /media/mount_point to whatever you wish to be the mount point. (Make sure the mount point exists.)

You might also want to check out bodhi.zazen's very useful guide to fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

