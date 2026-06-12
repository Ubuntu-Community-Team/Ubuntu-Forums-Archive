---
title: "Routine disk check question"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by richg on 2008-10-11
I have a 3.2g, 2gb ram, integrated mobo PC running Ubuntu 8.04 very well. What is happening when I power up the PC and a Routine disk check starts? Yes, I know the drive is being checked but details. This happens once in a while. Never any errors. THe IDE drive is a 80gb. I do not partition and I use a name and password. No dual boots. One drive, one OS. One user.
Thanks.

Rich

---

### Post by Keen101 on 2008-10-11
It's a linux thing. It checks to make sure your linux file system is in good working order, and helps prevent against data corruption. If it does find errors, it probably means your Hard Drive is either going bad, or you've been doing too many hard shutdowns. I wouldn't worry about it.

I had it fail on me once, and had me do a maunal check. I ran the manual check, and it fixed all kinds of corrupted files. I really think this is a life saver program. It's kind of like windows scan disk, you know if you shutdown wrong and boot up, but this is for linux.

---

### Post by richg on 2008-10-11
Hi Keen101

Thanks. That is what I figured. I have been running'Buntu 8.04 since it came out and have not seen this drive check until a month or two ago. Maybe this application was in one of the Updates. I do the updates as soon as I get a notification. I looked though my PC and could not find anything that seemed to be about this little process. I have been using PCs for some years but do not like working under the hood.

Rich

---

### Post by jerome1232 on 2008-10-11
It just runs the check ~every 30 boots. You can change that with... I believe the command was tune2fs on ext3 let me double check that. It's actually a feature of the file system and has been in place since I've used linux ( ~2 years)

edit: Yeah tune2fs, run man tune2fs to find out how to use it.

---

### Post by richg on 2008-10-11
Hi Jerome 1232

Thanks but that is written in techiish which I understand very little of.
I have no problem with the drive check. I was just curious.

Rich

---

### Post by NoVista on 2008-10-12
You might find this package useful:

[http://wiki.ubuntu.com/AutoFsck](http://wiki.ubuntu.com/AutoFsck)

---

### Post by Nielsoerbaek on 2008-10-12
hi, i wants me to run a manual check as well. How do i do that?

---

### Post by jerome1232 on 2008-10-12
You have to unmount the partition first (so if you want to run it on / then you must do it from a live cd)

then run e2fsk on it (if it's an ext3 or ext2 file system)

Example code if you wanted to run a simple check that will repair a filesystem of /dev/sda1

```
sudo -i
umount /dev/sda1
e2fsck -pv /dev/sda1
exit
```

You could also use gparted
(system-administration-Partition Editor) See screenshot.

---

