---
title: "Accessing  Vista Partition from Gutsy"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by McMagic on 2008-05-01
Dual boot vista and gutsy on respective HD's, u have access to vista HD but i cant configure wine to it, change the name of the drive, etc. every time the comp boots in gutsy i have to use sudo password to open it, and then its mounted for the rest of the session. Is there a setting i need to change in vista? or a force command for terminal? hlp plz!

thanks

---

### Post by Gripp on 2008-05-01
i'm not sure that i follow the bit about configuring wine to it... maybe explain what you;re trying to do

otherwise, if you are able to mount the drive using sudo mount -t dir dir then you likely only need to add this line to your fstab.  

which would be ```
sudo nano /etc/fstab
``` then just use the previous lines as an example.  if you aren't able to get it from there then try posting more info about your disks and file type, etc.

---

### Post by Paqman on 2008-05-01
Psychocats has a really good guide about [mounting Windows partitions](http://www.psychocats.net/ubuntu/mountwindows).

---

### Post by McMagic on 2008-05-02
the following is printout from sudo fdisk -l::

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16351635

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7936    63745888+   7  HPFS/NTFS
/dev/hda2            7938        9598    13341982+   c  W95 FAT32 (LBA)
/dev/hda3            9599        9729     1052257+  d7  Unknown

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00068bb9

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9366    75232363+  83  Linux
/dev/hdb2            9367        9729     2915797+   5  Extended
/dev/hdb5            9367        9729     2915766   82  Linux swap / Solaris
```

i acquired NTFS configuration tool, but it cannot see /dev/hda1, and neither is it included in my fstab file:

```
  GNU nano 2.0.6              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=0575b148-bfb4-4023-99c1-ceec910a32f3 /               ext3    defaults,erro$
# /dev/hdb5
UUID=26ecea5b-a2f3-4734-a125-60aa1322dce1 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


```

---

