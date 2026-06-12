---
title: "My friend can't eject"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by white_eagle-mk on 2008-05-09
After upgrading to hardy he can't eject:
his /etc/fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=461e8baa-f6a5-466a-a451-2f5e088f9e60 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=faf2cf59-d3a9-452d-8eaa-5c62798e55cc none            swap    sw              0       0
/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

note that I had the same problem and also scd0 was first hdc and someone in #ubuntu suggested him and me to change it from hdc to scd0 and it then eject worked at me, but not at him (thus making the cd-rom it cannot read cd discs)... Any fix?

---

### Post by SunnyRabbiera on 2008-05-09
have you tried to unmount the volume?

---

### Post by white_eagle-mk on 2008-05-09
He tried booting with the Live CD, and he could boot from it, just ubuntu changed the location (as i found out on on #ubuntu) for the cdrom0 device in hardy and now a patch is required, I'll say again, he gets this error message when he does eject in terminal: ```
  eject: tried to use `/dev/hdc' as device name but it is no block device eject: unable to find or open device for: `cdrom' 
```

---

