---
title: "How boot to &quot;maintenance mode&quot;"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by movrshakr on 2008-07-12
Occasionally, during boot of Gutsy, I will see a message that fsck is being "forced."  Sometimes it finds things to fix and sometimes it says fsck must be run in maintenance mode--and leaves the screen at a maintenance mode prompt.

Is there any way to boot straight into this mode instead of it progressing to the login GUI?

Is this the same as what used to be called single-user mode?

---

### Post by ibuclaw on 2008-07-12
It is whatever you want to call it.

Single User Mode, Maintenance Mode, Recovery Mode, etc.

It should be option 2 in your GRUB menu (Press ESC before the Ubuntu kernel boots up).

If you wish to check to see if you have that option in GRUB. A typical example of what it will look like in the menu.lst file is here:
```

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=1234 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

```

Note the "**ro single**" at the end of the kernel line.

[EDIT]
Can you post the output of this command?
```
cat /etc/fstab
```

Regards
Iain

---

### Post by movrshakr on 2008-07-12
I guess hitting ESC is the key (no pun intended) for that.

Here is fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bebd331b-d7a8-4a5e-b15f-337ad9c517d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=473d0e8e-c51e-4ae0-bd20-ee5ba635daaf none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by ibuclaw on 2008-07-12
Ah, OK.
fstab is fine (I was curious how many partitions you had and whether or not they were all being checked too frequently).

Yes, I suppose it is ESC on boot then.

Regards
Iain

---

