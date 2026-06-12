---
title: "Automatically mounting my ext3 drive and adding journaling?"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Aanidaani on 2008-05-24
Hey guys. I have two questions and I'll start off with the easier one first. I installed a new drive to hold my Linux partition and a media partition (with music, movies) that I access from both Windows and Linux. Windows is on a completely separate drive and I have no problems booting, etc. 

However, when I formatted the media partition, I chose ext3 without journaling. Is there any way I can activate journaling to better protect that partition?

My next question concerns mounting: whenever I log into Linux I have to manually mount the drive using "sudo mount /dev/sda1 /media/Storage" I tried adding to my fstab file, but it doesn't seem to work. Here are the lines from the fstab:

```
# /dev/Storage
/dev/sda1	/media/Storage	ext3 users,defaults,umask=000 0 0
```

What can I do to make the partition automatically mount? Thanks for the help!

---

### Post by logos34 on 2008-05-24
to add journaling:

sudo umount /media/Storage

sudo tune2fs -j /dev/sda1

Maybe fstab should read "ext2" (no journaling) ?

---

### Post by Aanidaani on 2008-05-24
Okay, I followed your instructions and now I feel stupid: apparently journaling was already enabled. Since the drive is already ext3, what should I do about the fstab to get it to mount? It's still not working...

---

### Post by hyperair on 2008-05-24
Another method is this:
```
sudo debugfs -R "features +has_journal" /dev/sda1
```

To check the features enabled in the filesystem, run this command:
```
sudo debugfs -R "features" /dev/sda1
```

The only difference between ext2 and ext3 is that ext3 has journaling. So if an ext2 partition is given journalling support, it becomes ext3. If journalling support is removed from an ext3 partition, it becomes ext2.

EDIT: Don't forget to run a file system check when you're done. 
EDIT 2: Aanidaani, I only just saw your post. Perhaps you didn't use ext3? Or perhaps the options you used are wrong? Run this command to find out the appropriate filesystem and options to use (after you've mounted it already using the manual mount command):
```
mount | grep /dev/sda1
```

You should get an output that looks like this:
```
/dev/sda1 on /media/Storage type ext3 (rw,noatime)
```
In this case, the options are "rw,noatime", and the filesystem type is "ext3". The fstab line which corresponds to this is as follows:
```
/dev/sda1 /media/Storage ext3 rw,noatime 0 0
```

---

### Post by Aanidaani on 2008-05-24
I followed your instructions and changed my fstab to include those tags. When I rebooted everything mounted perfectly. Thanks for the help! :KS

---

### Post by hyperair on 2008-05-24
No problem. =) Glad to be of assistance.

---

