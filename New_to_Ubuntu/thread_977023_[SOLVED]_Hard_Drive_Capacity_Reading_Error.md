---
title: "[SOLVED] Hard Drive Capacity Reading Error"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Kunks on 2008-11-09
I just put a new western digital 80 GB hard drive in a dell dimension,Pentium 4 running Ubuntu 8.10...my disk usage analyzer says it's 142.2 GB but its really only 80 (see screen shot)why does it think it's bigger than it is???? Just curious as everything else is working great.

---

### Post by taurus on 2008-11-09
Are you sure you are looking at the right drive?  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by unutbu on 2008-11-09
I think there is some strangeness in the way baobab (disk usage analyzer) adds up disk space. The problem has to do with gvfs-fuse-daemon.

See [https://bugs.launchpad.net/ubuntu/+source/baobab/+bug/244086](https://bugs.launchpad.net/ubuntu/+source/baobab/+bug/244086)

I think it is better to rely on the terminal's
df -h for the filesystem size, or sudo fdisk -l for the partition size.

---

### Post by Kunks on 2008-11-09
Here are the results... obviously correct



Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b24a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9353    75127941   83  Linux
/dev/sda2            9354        9729     3020220    5  Extended
/dev/sda5            9354        9729     3020188+  82  Linux swap / Solaris
dave@dave-desktop:~$ 
What drive was the disk usage analyzer looking at ??? a as I have one hard drive & 1 cdrom & 1 floppy drive????

---

### Post by unutbu on 2008-11-09
I think gvfs (GNOME virtual files system) is used for things like shared SAMBA directories. I think this is what is throwing off the totals as reported by disk usage analyzer.

---

