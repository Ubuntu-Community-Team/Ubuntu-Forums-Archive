---
title: "Accessing Amiga filesystems on x86 Ubuntu"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Billsey on 2008-08-02
I used to use Amiga computers, and I have a couple of SCSI hard drives left. Recently, I took possession of a SCSI cable that should let me physically connect those hard drives to one of my Ubuntu boxes, but I can't find anything anywhere about whether or not Ubuntu on x86 supports the Amiga filesystems. Can someone inform me, please ([EMAIL="p3@earthlink.net"]p3@earthlink.net[/EMAIL])?

There is also a thread from January 2008 from a person trying to get their PPC Mac up with Ubuntu, but they keep getting an error that looks like the PPC kernel thinks it has an Amiga partition involved. It would be nice of someone could help them, too.

---

### Post by JillSwift on 2008-08-02
A quick look at Google says you can mount those with "affs", the Amiga Fast File System module. I can't find those in the repositories, but I see references to it all over.
Sadly packages.ubuntu.com is down or very slow right now, that being where you can get detailed info about packages for Ubuntu.

---

### Post by sisco311 on 2008-08-02
just try to mount the partition with the mount command:
```
sudo mount -t affs /dev/sd**XY **/mnt
```

also make sure the affs module is loaded:
```
lsmod | grep affs
```

to load the module:
```
sudo modprobe affs
```

---

