---
title: "Mounting issue at start up"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by joebutton64 on 2013-12-05
On start up I receive a message saying that the drive is not ready and it gives me options to continue to wait, press S to skip, or press m for Manual mount. If this has already been posted I am sorry for the repost!

---

### Post by Bashing-om on 2013-12-05
joebutton64; Hi !

That error is generally indicative of file system corruption. This is a less invasive method to run the file system check/repair utility:
Boot the liveDVD to "try ubuntu" mode:
Terminal commands:
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo fdisk -lu ##to identify your disk(s) and partitions.
sudo e2fsck -C0 -p -f -v /dev/sda1 ##Checking the 1st disk(sda) ,1st partition (sda1)
#IF there are errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

``` (the '#' denotes comments, not to be entered as any command)
Also "assumed" is that '/' (root) that you need to verify is installed onto that 1st partition on that 1st hard drive.

Post back on results and for any additional advise.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

