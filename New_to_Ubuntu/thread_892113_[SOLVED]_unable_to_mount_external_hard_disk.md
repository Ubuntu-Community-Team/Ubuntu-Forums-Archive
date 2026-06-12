---
title: "[SOLVED] unable to mount external hard disk"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by KhuntienNang on 2008-08-16
im a newbie here, only a few days old with ubuntu. 

i can't seem to access my external usb hard drive. it says "cannot mount volume - unable to mount the volume 'external Data'." 

could someone help? 
i followed some command help i found online, but doesnt seem to work? and im afraid to mess things up by command line, so i figured i better ask the experts here. 


thanks

---

### Post by drs305 on 2008-08-16
Please post the following: (fdisk -small L)
```
sudo blkid
sudo fdisk -l
cat /etc/fstab
```

This will give us information to help you discover what's wrong.

---

### Post by KhuntienNang on 2008-08-17
uh, it's long.
here is what i got

```


/dev/sda1: UUID="CCAC8DFBAC8DE076" LABEL="System" TYPE="ntfs"
/dev/sda2: UUID="FC0C19A00C19574C" LABEL="Data" TYPE="ntfs"
/dev/sdb1: UUID="dd9769df-a0af-4e62-99e6-50c44eed702c" TYPE="ext3"
/dev/sdb5: TYPE="swap" UUID="1ccee203-d12d-48d7-938f-e11c679c5445"
/dev/sdc1: UUID="D02843712843561E" LABEL="External Data" TYPE="ntfs"
webble@Webble:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300000000000 bytes
255 heads, 63 sectors/track, 36472 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x390e390d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7150    57432343+   7  HPFS/NTFS
/dev/sda2            7151       36472   235528965    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x018b018b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18705   150247881   83  Linux
/dev/sdb2           18706       19457     6040440    5  Extended
/dev/sdb5           18706       19457     6040408+  82  Linux swap / Solaris

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96da96da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3647    29294496    7  HPFS/NTFS
webble@Webble:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=dd9769df-a0af-4e62-99e6-50c44eed702c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=1ccee203-d12d-48d7-938f-e11c679c5445 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
webble@Webble:~$

```

---

### Post by drs305 on 2008-08-17
There doesn't appear to be anything wrong in the information you posted. Since you say you are new to ubuntu, I would suspect the problem lies in an 'unclean' shutdown of the drive from within windows. This happens if an external device is turned off or removed without using the 'safely remove device' option or a normal shutdown.

To correct the problem, you have a couple of options:
1. With the device plugged in, restart windows and do a normal shutdown. That should clear the error messages and allow it to work normally in linux. This would be the preferred option.

2. From within ubuntu, install 'ntfsprogs', a collection of utilities for ntfs partitions. Then run 'ntfsfix' to remove the error message.
```

sudo aptitude install ntfsprogs
ntfsfix /dev/sdc1

```


Hopefully one of these will correct your problem and allow the drive to mount. Let us know which one you used to solve the problem.

External devices are not normally meant to be included in fstab because the device name is dynamic (it could be sdc1 one day, sdg1 the next), depending on what external devices are connected. However, if this is a device that is normally connected, your previous post has given us the information to easily add an entry to fstab so the device is mounted on boot up. You can set the owner, group, access permissions, etc via fsatb.

If you wish to do this, let us know and tell us what you want the mount point to be (e.g. /media/*some.mountpoint.name* ) .

---

### Post by KhuntienNang on 2008-08-17
Thank's a lot! 
i tried the first step you suggested, it works now. 

lesson learned, always diconnect/dismount usb properly. 

another question:
so, say in the future if someone plugs off the usb ext hd or somehow it got disconnected without doing the dismounting properly, would ubuntu have problem detecting it next time? so does it mean suggestion #2 has to be taken?

---

### Post by drs305 on 2008-08-17
> **KhuntienNang said:**
> Thank's a lot! 
i tried the first step you suggested, it works now. 

lesson learned, always diconnect/dismount usb properly. 

another question:
so, say in the future if someone plugs off the usb ext hd or somehow it got disconnected without doing the dismounting properly, would ubuntu have problem detecting it next time? so does it mean suggestion #2 has to be taken?

I have had unexpected disconnects of external ntfs drives in ubuntu before that powered up without problem the next time (fortunately). It doesn't mean that will always be the case. If it happens in ubuntu then option #2 (ntfsfix) will probably work in that ntfsfix resets the ntfs journal and fixes some minor ntfs errors.

---

