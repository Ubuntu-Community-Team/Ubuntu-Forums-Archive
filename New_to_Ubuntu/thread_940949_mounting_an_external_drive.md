---
title: "mounting an external drive"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by polarbear12345 on 2008-10-07
well i have an ext disk drive with 4 partitions....i changed the mount point of one of the partitions to /media/drive_z in its properties...
when i unmounted it and tried to remount i fail...


i get msg frm system---->

     unable to mount the volume 'New Volume'
     DETAILS>
     mount_point cannot contain the following    characters:newline,G_DIR_SEPERATOR(usually /)

i m not getting now the same option which i changed in properties

plzzzzzzz help

---

### Post by nkri on 2008-10-07
Try this:
```
mount /dev/*partition_on_external_harddrive* /media/drive_z
```

If it says something about insufficient privileges:
```
sudo mount /dev/*partition_on_external_harddrive* /media/drive_z
```

If these don't work, I think you might need to make an entry in /etc/fstab, but I don't understand that file and can't help if the above commands don't work:(

Also, if you aren't sure about which partition or disk name it is, post  the output of:
```
sudo fdisk -l
```

Good luck!
-nkri

---

### Post by aparigraha on 2008-10-07
[How To fstab]("http://ubuntuforums.org/showthread.php?t=283131")

---

