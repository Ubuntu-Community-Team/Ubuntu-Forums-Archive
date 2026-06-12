---
title: "Viewing more than just File System in Terminal?"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by lemmingrebel on 2012-07-19
So I can see my "File System" ... but I'd like to use terminal to refer to another drive I'm using.

The drive is currently referred to under "Devices" as "20 GB File System" ... 
 
How do I get to it?

---

### Post by M!K3_$ on 2012-07-19
You can use the following command to see what partitions are currently mounted, and where they are mounted to:
```
mount
```

You can view all attached disks and their partitions with the following command:
```
sudo fdisk -l
```

If you would like to mount a partition use the following:
```
sudo mount <path to partition> <path to directory>
```
For example:
```
sudo mount /dev/sdb1 /mnt/harddrive
```

---

### Post by lemmingrebel on 2012-07-19
Terminal says it's already mounted.

I just want to refer to a file on that drive ...

---

### Post by M!K3_$ on 2012-07-19
> **lemmingrebel said:**
> Terminal says it's already mounted.

I just want to refer to a file on that drive ...

Then simply refer to file on the partition under the mountpoint listed.

I think you may benifit from this:
[http://beginlinux.com/twitter/1094-the-beginners-guide-to-the-ubuntu-terminal]("http://beginlinux.com/twitter/1094-the-beginners-guide-to-the-ubuntu-terminal")

OR this:
[http://www.youtube.com/watch?v=CGBsurVdLGY]("http://www.youtube.com/watch?v=CGBsurVdLGY")

---

### Post by lemmingrebel on 2012-07-19
Okay, reading now - thanks!

---

### Post by JamezQ on 2012-07-20
it is most likely under /media.

Sometimes it will have the same name as nautilus, and sometimes not.

However there should not be too many in there, so feel free to try them all.

cd /media/YourDrive

Then do a "ls" directory listing to see if this is *your* drive.

---

