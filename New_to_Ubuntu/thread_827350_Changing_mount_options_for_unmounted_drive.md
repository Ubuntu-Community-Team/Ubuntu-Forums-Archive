---
title: "Changing mount options for unmounted drive"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by GepettoBR on 2008-06-12
I changed the mount options for my microSD card via right-clicking the link on my Desktop, and tried remounting it for the changes to take effect. Now, it won't mount ("invalid mount options") and I don't know how to access those options again. I do know that the card is identified as /dev/sda1 when I plug it in (thanks to GParted) but that's about all I know.

So, can anyone tell me how to access the mount options, or how to restore them to default, when the drive refuses to be mounted? If all else fails, I can back up the data on the card in Windows and format it, but I'd rather learn how to do this in case the situation arises again.

---

### Post by Nythain on 2008-06-12
dont know wich "mount options" you are talking about, but you could look in fstab:
gksu gedit /etc/fstab
and see if you can find teh device listed there, and whatever options you told it or want to remove... fstab holds all the "mount options" i know of for devices, so if that doesnt help much, its beyond me

---

### Post by GepettoBR on 2008-06-13
Thanks for the suggestion. I had forgotten to say that Ihad already tried that, fstab apparently doesn't list flashdisks and memory cards. The only listings in fstab are for the partitions in hda (my internal hard disk), the cd-rom drive and the floppy drive. 

The SD card, however, does appear under Places>Computer, where it tries and fails to mount if I double-click the icon, and the card reader is correctly listed when I run lsusb.

---

### Post by cariboo on 2008-06-13
Check /etc/mtab that is were your mount options will show up.

Jim

---

### Post by GepettoBR on 2008-06-13
They aren't there either. Here's the content of both files:

/etc/fstab```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=fc9e1b2e-4d9e-4ac2-a614-c227afe866c7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda7
UUID=6cd1d351-3d1c-4e86-ae6b-7188f6d74f2c /home           ext3    relatime        0       2
# /dev/hda5
UUID=12460b9d-9a17-4095-92f4-9d4d8993ace3 /media/storage  ext3    relatime        0       2
# /dev/hda1
UUID=58DC6541DC651A90 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda8
UUID=511b1517-da6c-46a2-a3c2-3f25fd47f64b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

/etc/mtab```
/dev/hda6 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-18-generic/volatile tmpfs rw 0 0
/dev/hda7 /home ext3 rw,relatime 0 0
/dev/hda5 /media/storage ext3 rw,relatime 0 0
/dev/hda1 /windows fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/paulo/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=paulo 0 0
```

---

### Post by MasterSander on 2008-06-13
Did you make the directory in your /media/ folder, try this: sudo mkdir /media/storage

EDIT: I mis-saw, hda5 is storage try making the dir for what name the card has in fstab

---

### Post by MasterSander on 2008-06-13
I've reread the post and saw that I was too quick, but if you can remember the name it mounted under, then you can try the command sudo mkdir /media/<NAME>

---

### Post by santorini on 2008-12-24
i think this should be filed as a bug

i have the same problem, googled and can't find answer (yet). i fiddled with my computer for a while and found the (nice and graphical) solution

(alt-f2, if it's not in your menu) open gconf-editor (NOT using root, just your current user)

navigate to system -> storage -> volumes 

you should see your device settings listed according to UUID here. then delete the wrong values on the right pane.

have peace =-)

---

### Post by palgan on 2009-01-23
> **santorini said:**
> 

navigate to system -> storage -> volumes 

you should see your device settings listed according to UUID here. then delete the wrong values on the right pane.



It worked for me! Thanks a lot for sharing your findings.

---

