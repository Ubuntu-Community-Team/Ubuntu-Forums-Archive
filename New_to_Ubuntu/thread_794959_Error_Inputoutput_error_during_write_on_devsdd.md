---
title: "Error: Input/output error during write on /dev/sdd"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Jest3r on 2008-05-15
Hello all,
  I am having a problem reading my usb device. Is that any way of starting fresh with the device, so that i can relabel it and partition it.
# parted /dev/sdd
```

GNU Parted 1.7.1
Using /dev/sdd
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p                                                                
Error: Unable to open /dev/sdd - unrecognised disk label.                 
(parted) mklabel 
New disk label type? msdos                                                
Error: Input/output error during read on /dev/sdd                         
Retry/Ignore/Cancel? r                                                    
Error: Input/output error during read on /dev/sdd                         
Retry/Ignore/Cancel? i                                                    
Error: Input/output error during write on /dev/sdd                        
Retry/Ignore/Cancel? c
(parted) q
```

# hdparm -iv /dev/sdd
```

/dev/sdd:
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 1952/64/32, sectors = 3999743, start = 0
 HDIO_GET_IDENTITY failed: Invalid argument
```


# ls -l /dev/sdd*
```
brw-rw---- 1 root plugdev 8, 48 2008-05-15 18:37 /
```

fsck /dev/sdd
```
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdd
Could this be a zero-length partition?
```

---

### Post by sdennie on 2008-05-15
Is it possible that the usb device is dead?  USB keychains are particularly fickle (in my experience) so, it's possible that you simple have a dead USB device.

---

### Post by Xiong Chiamiov on 2008-05-15
Have you tried using a parted frontend, like GParted or QTParted?  Also, have you tried using fdisk?

---

### Post by Jest3r on 2008-05-15
> **vor said:**
> Is it possible that the usb device is dead?  USB keychains are particularly fickle (in my experience) so, it's possible that you simple have a dead USB device.
Hope not :(. This is an ipod.

> **Xiong Chiamiov said:**
> Have you tried using a parted frontend, like GParted or QTParted?  Also, have you tried using fdisk?

Tried the gui's they fail to read the disk label. So i can't do anything useful with them.

---

### Post by Jest3r on 2008-05-15
It would seam that the superblock is broken on my ipod. 

If i was to find someelse with the same ipod as me,Could i use dd to grab the superblock from the working ipod and use that on mine(the broken one)??

---

