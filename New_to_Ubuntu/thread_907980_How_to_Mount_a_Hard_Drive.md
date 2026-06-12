---
title: "How to Mount a Hard Drive"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Chompy on 2008-09-02
I have a hard drive, at /dev/hda1 . I want to mount it because it says unmounted.

How important is it where I mount it?


Aside, this is my fstab file:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda1 swap swap defaults 0 0

and my menu.lst is blank.

My goal is to restart and begin running ubuntu. How?

Thanks to you.

---

### Post by vikramaditya on 2008-09-02
I dunno...I just go to "Places" and open one of my 4 internal drives from there.  Is your drive not being detected by the os?

---

### Post by hubie on 2008-09-02
Do you have other partitions on that drive, or just one.  If you had others, I would expect to see /dev/hda1, /dev/hda2, etc.

The way your fstab is set up, it is mounting the partition at /dev/hda1 as swap, and it doesn't know anything about the other partitions (if they exist).  This would explain why you can't see the drive.

---

### Post by abhishek.malhotra35 on 2008-09-02
From your fstab file, it looks like your /dev/hda1 is swap space. You don't need to mount it. Its mounted already. It is a partition used by linux. As for some other partitions(if you have), you can enter them in fstab file, so that they automatically get mounted when OS boots. Or you can manually mount the partitions yourself using mount command. As for the question where to mount, you can mount anywhere. but preferred locations are media or mnt.

---

