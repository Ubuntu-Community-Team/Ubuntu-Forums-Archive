---
title: "[SOLVED] lost swap"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by C.S.Cameron on 2008-09-07
I was playing with the GParted live disk.
Seem to have lost my swap trying to make a partition windows could see.
The swap space is still there in GParted,
But System Monitor shows Zero swap available.
Is there an easy solution to reconnect it.

---

### Post by Pro-reason on 2008-09-07
Yes, you must have an incorrect reference in your fstab file.

Post the output of ```
cat /etc/fstab
``` and we'll be able to correct it.

---

### Post by C.S.Cameron on 2008-09-07
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=e9e69233-ddcd-476d-8999-a4f67cf863ea /               ext3    relatime,errors=remount-ro 0       1
# /dev/sde5
UUID=da3b107e-7b13-48b5-a174-4466ac136c67 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
cscameron@cscameron-8GB:~$

---

### Post by Pro-reason on 2008-09-07
Ah sorry, I forgot to ask you to post the output of &#8220;sudo fdisk -l&#8221; and &#8220;sudo blkid&#8221; too.

If you change &#8220;UUID=da3b107e-7b13-48b5-a174-4466ac136c67&#8221; into &#8220;/dev/sde5&#8221;, it will probably fix it, but it would be better to give me the output of the above commands so I can be sure.

When posting output on the forums, remember to enclose it in [noparse]```
...
```[/noparse] tags, for legibility.

---

### Post by C.S.Cameron on 2008-09-07
cscameron@cscameron-8GB:~$ sudo fdisk -l
[sudo] password for cscameron: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0e2f0e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       38913   178361662+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22252c0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04435e8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sdc2           16709       19457    22081342+   7  HPFS/NTFS

Disk /dev/sdd: 8011 MB, 8011120640 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x289f289e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         796     6393838+  83  Linux
/dev/sdd2             797         973     1421752+   5  Extended
/dev/sdd5             797         973     1421721   82  Linux swap / Solaris



cscameron@cscameron-8GB:~$ sudo blkid
/dev/sda1: UUID="74F0BEC8F0BE8FBA" TYPE="ntfs" LABEL="Local Disk" 
/dev/sda2: UUID="58C4C917C4C8F870" LABEL="Local Disk" TYPE="ntfs" 
/dev/sdb1: UUID="BE344EFE344EB963" LABEL="200 G" TYPE="ntfs" 
/dev/sdc2: UUID="98843BAB843B8B30" LABEL="NewVolume" TYPE="ntfs" 
/dev/sdc1: UUID="EEB4A186B4A151BF" TYPE="ntfs" 
/dev/sdd5: TYPE="swap" UUID="3479c076-4d22-4259-b269-22f9c21441cb" 
/dev/sdd1: UUID="e9e69233-ddcd-476d-8999-a4f67cf863ea" TYPE="ext3" 
cscameron@cscameron-8GB:~$

---

### Post by kansasnoob on 2008-09-07
[http://ubuntuforums.org/showthread.php?t=879192](http://ubuntuforums.org/showthread.php?t=879192)

---

### Post by Pro-reason on 2008-09-07
```
*cscameron@cscameron-8GB:~$ sudo fdisk -l*
[sudo] password for cscameron: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0e2f0e2

   Device Boot      Start         End      Blocks   Id  System
[B]/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       38913   178361662+   7  HPFS/NTFS[/B]

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22252c0e

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1       24792   199141708+   7  HPFS/NTFS**

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04435e8a

   Device Boot      Start         End      Blocks   Id  System
[B]/dev/sdc1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sdc2           16709       19457    22081342+   7  HPFS/NTFS[/B]

Disk /dev/sdd: 8011 MB, 8011120640 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x289f289e

   Device Boot      Start         End      Blocks   Id  System
[B]/dev/sdd1   *           1         796     6393838+  83  Linux
/dev/sdd2             797         973     1421752+   5  Extended
/dev/sdd5             797         973     1421721   82  Linux swap / Solaris[/B]

```

```

*cscameron@cscameron-8GB:~$ sudo blkid*
/dev/sda1: UUID="74F0BEC8F0BE8FBA" TYPE="ntfs" LABEL="Local Disk" 
/dev/sda2: UUID="58C4C917C4C8F870" LABEL="Local Disk" TYPE="ntfs" 
/dev/sdb1: UUID="BE344EFE344EB963" LABEL="200 G" TYPE="ntfs" 
/dev/sdc2: UUID="98843BAB843B8B30" LABEL="NewVolume" TYPE="ntfs" 
/dev/sdc1: UUID="EEB4A186B4A151BF" TYPE="ntfs" 
/dev/sdd5: TYPE="swap" UUID="3479c076-4d22-4259-b269-22f9c21441cb" 
/dev/sdd1: UUID="e9e69233-ddcd-476d-8999-a4f67cf863ea" TYPE="ext3" 
cscameron@cscameron-8GB:~$
```

That's how you ought to have formatted it.  Anyway.

Your swap partition is located on partition 5 on SATA drive D.  This can be referred to as “/dev/sdd5” or by its unique identification number “UUID="3479c076-4d22-4259-b269-22f9c21441cb”.

If you look at your /etc/fstab file, the line that mentions the swap currently says this:
```

# /dev/sde5
UUID=da3b107e-7b13-48b5-a174-4466ac136c67 none swap sw 0 0
```
The bit that starts with a “#” is not part of the configuration; it's just there for your information.

Change the UUID currently mentioned to the correct UUID.  Alternatively, you could replace it with “/dev/sdd5”.

To edit the file, do either one of the following commands:

```

sudo nano  /etc/fstab
gksu gedit /etc/fstab
```

---

### Post by C.S.Cameron on 2008-09-08
Thanks Pro-reason.
Worked first time.

---

