---
title: "Formatting external hdd for backup?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Deadmode on 2008-04-27
Hey there I need a little help formatting this 500gb external fat32 hd to ext3.  I'm going to be using it solely for the purpose of backing up my box.  It shows up with the title "12E8-3A6D" under /media/.  So, the command should be something like ```
# mkfs.ext3 /media/12E8-3A6D
``` Right?

---

### Post by Tatty on 2008-04-27
I have never used the mkfs command before, but according to [wikipedia]("http://en.wikipedia.org/wiki/Mkfs") it would need to go someting like mkfs -t ext3 /media/12E8-3A6D.  However It might be easier to use gparted, it is a graphical partition manager...
```

sudo apt-get install gparted
```  Then find it under System->Administration

---

### Post by hackle577 on 2008-04-27
I would use GParted like Tatty described, it's easier and less risky.

---

### Post by hackle577 on 2008-04-27
The steps will be something like this:

[LIST=1]
[*]Download GParted
[*]Unmount your external drive
[*]Select your external drive in gparted
[*]Delete the partition on the disk
[*]Format the entire disk to ext3
[/LIST]

---

### Post by Deadmode on 2008-04-28
Thank you for your posts.  I have it formated ext3 now.  But I don't how to find the path of the hard drive.  The hard drive auto mounts on my desktop which is good, but doesn't show up in /media. I want to tell sbackup that that hard drive /dev/sdb1 is the destination for backup files.  How do I go about that?
Would ```
sudo mount /dev/sdb1 /mnt/storage
```be ok? And then just tell sbackup to save there?  Or would mounting sdb1 to /mnt/storage only be temporary?

---

### Post by hackle577 on 2008-04-29
Plug in your drive and wait for the icon to appear on the desktop. Right-click on the icon, select Properties, and then the Volume tab. The Mount Point line should tell you where the drive is being mounted.

I'm not quite sure about the sbackup stuff, as I've never used that program before.

---

### Post by vanadium on 2008-04-29
External drives normally do mount under /media. I am sure that, when you plug in the drive, you will be able to see a new directory under /media where your drive is mounted. You will discover that also using the approach of hackle577.

---

