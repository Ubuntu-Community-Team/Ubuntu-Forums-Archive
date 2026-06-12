---
title: "No disk space left, free space on partition"
date: 2015-11-25
forum: New to Ubuntu
---

### Post by JuniorGenius on 2015-11-25
I'm running Ubuntu Desktop 15 32bit on VirtualBox, with a Windows 7 64bit host. I'm quite new to Ubuntu, and have no idea what I'm doing wrong. I will get a message something along the lines of "The filesystem Root has only 0bytes of disk space left!". I've tried using gparted to no avail. I'm not quite sure what information to supply, here are some images:

[IMG]http://i.imgur.com/MalmyYj.png[/IMG]
[IMG]http://i.imgur.com/PbnuNus.png[/IMG]
[IMG]http://i.imgur.com/dwi5Pu2.png[/IMG]

---

### Post by v3.xx on 2015-11-25
This is a guest install on mine

[ATTACH=CONFIG]265776[/ATTACH]

How did you install?  Looks like you tried to manually create the file system.  I just use the install option "Use entire disk"

---

### Post by JuniorGenius on 2015-11-26
I believe I did the same.. I'll try resizing the partitions to make them more like yours and let you know what happens. ^^

Nevermind, my partitions don't even look like yours at all. I am so lost.. no idea what to do short of a reinstall which I'd really rather not do.

I've saved a backup and am attempting a reinstall. I don't see any "Use Entire Disk" option..

---

### Post by oldos2er on 2015-11-26
Moved to New to Ubuntu.

---

### Post by JuniorGenius on 2015-11-26
Thank you, and thanks for merging my posts. Sorry about that.

A clean install has fixed the problem, however I'm still not sure what happened before. I'm on to a problem with VirtualBox shared folders. I guess I should make a new topic for that?

---

