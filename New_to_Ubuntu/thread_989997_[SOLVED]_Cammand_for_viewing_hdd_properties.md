---
title: "[SOLVED] Cammand for viewing hdd properties"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Yaspoon on 2008-11-22
Hey peoples.
I'm after a shell command, that will display the hdd properties. Like when you right click on the hdd in gnome, and hit properties then click on the drive and volume tabs. Is there a command that gives you this kind of information, from the shell
Thanks

---

### Post by marshall.robert on 2008-11-22
perhaps ```
df -h
``` will be what you need...

---

### Post by unutbu on 2008-11-22
```
sudo lshw -C disk

```
will tell you the vendor.
```

udevinfo -a -p /sys/block/sdb
```

(after changing sdb to the appropriate name for the drive)
will yield the vendor, the model, the firmware revision number, the serial number, the connection speed. For example:
```

    ATTRS{vendor}=="Ativa   "
    ATTRS{state}=="running"
    ATTRS{rev}=="5.00"
    ATTRS{model}=="2GB             "
    ATTRS{serial}=="054131808000691B"
    ATTRS{speed}=="480"
```
```

mount
```

will tell you the mount point, filesystem type and mount options.
```

blkid

```
will tell you the UUID.
```

sudo tune2fs -l /dev/sdb1
```
(after changing sdb1 to the correct partition name)
will tell you the volume label if the filesystem is ext2 or ext3

---

### Post by Yaspoon on 2008-11-22
Okay as I was reposting you have posted the info I wanted what a legend thank you very much

---

