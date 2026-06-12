---
title: "Windows Veteran Trying to Mount Ext USb HDD"
date: 2014-01-23
forum: New to Ubuntu
---

### Post by johnson-stuart2013 on 2014-01-23
Did a Ubuntu install on a dell inspiron. Have relevent drivers, need help with the mount command process.

---

### Post by GaryTheCat on 2014-01-23
I have a dell inspiron - I just plug my USB HDD in and it pops up as a little button on the left.

That probably doesn't help much......

---

### Post by Bashing-om on 2014-01-23
johnson-stuart2013; Hi ! Welcome to the forum .


The external usb drive should be auto detected, and shown in the file manager.

The guts and the gore of attaching file systems,.... well ->
These will give you a good introduction to mounting, and file systems in the ubuntu world:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

By all means, kick back, read, and enjoy.

As you have questions or things you do not understand, by all means, -we are here - ask .

[INDENT]the longest journey begins
with this first step
[/INDENT]

---

### Post by spencer the great on 2014-01-24
List the filesystems on your computer:
```
df -m
```
which lists the filesystems and tells you how much disk space is used in each one.
Find the one with the used/available/percentage sizes that looks like your hdd (it's in megabytes; df -k for kilobytes, df --block-size=1G for gigabytes)
Look in the first column ("Filesystem") for the corresponding row
It should begin with "/dev" (no quotes)

Create a folder where you want the files to appear (I prefer "mnt" in my home folder):
```
$ mkdir mnt
```
Mount the drive (the filesystem is the one you found earlier):
```
$ sudo mount FILESYSTEM mnt
```
replace FILESYSTEM with the filesystem file you found earlier with df.
And you should be all set!
To remove it safely, type:
```
$ sudo umount mnt
```

---

### Post by coldcritter64 on 2014-01-24
> **spencer the great said:**
> ...
Create a folder where you want the files to appear (I prefer "mnt" in my **home** folder):
```
$ mkdir mnt
```
Mount the drive (the filesystem is the one you found earlier):
```
$ sudo mount FILESYSTEM **~/**mnt
```
replace FILESYSTEM with the filesystem file you found earlier with df.
And you should be all set!
To remove it safely, type:
```
$ sudo umount **~/**mnt
```

note the ~/ is for your home folder. Cheers

**Edit** absolute paths are not necessary, your original post works Perfectly OK - no changes needed. If you are not working in the home folder, as is the default behaviour, the full path can make a difference to the mount command. My post is not really a correction more an addition. Cheers

---

