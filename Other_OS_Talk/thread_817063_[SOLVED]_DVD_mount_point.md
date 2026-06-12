---
title: "[SOLVED] DVD mount point"
date: 2008-06-03
forum: Other OS Talk
---

### Post by melrom on 2008-06-03
I am attempting to burn a DVD iso via the command line, but after checking fstab, I can't find where it's located, but graphically, it appears that the DVD mounted. Here is the output of fstab:

```

/dev/VolGroup00/LogVol00 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/VolGroup00/LogVol01 swap                    swap    defaults        0 0


```


Note: I'm doing this in CentOS 5.1.

-MelRom

---

### Post by hermes0710 on 2008-06-03
what are the contents of your /media folder?

---

### Post by melrom on 2008-06-03
it's empty.

---

### Post by melrom on 2008-06-03
but if I right-click on it, it gives me the option to unmount it??

---

### Post by bapoumba on 2008-06-03
Moved to "Other OS Talk".

---

### Post by Bungo Pony on 2008-06-03
There are certain things that cannot be mounted:

- blank media
- audio CDs
- Drive with no disk

You'll have to write directly to the device. Put in a data disc and see where it gets mounted. Then you'll know the device to write to.

---

### Post by melrom on 2008-06-04
yeah, i sort of fixed it in a roundabout way. thanks for your input.

---

