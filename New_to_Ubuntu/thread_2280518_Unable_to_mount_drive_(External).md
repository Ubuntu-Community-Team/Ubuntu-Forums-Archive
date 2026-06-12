---
title: "Unable to mount drive (External)"
date: 2015-05-31
forum: New to Ubuntu
---

### Post by robbie6 on 2015-05-31
Hi all. I have a hard drive with a windows os installed on it. It's from an old machine that broke down a year ago. However I got a sata-usb cable to hook it up to my current ubuntu machine, however I get the following error message.


[CENTER][/CENTER]
[I]Error mounting /dev/sdc2 at /media/robbie/4CA45547A4553524: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdc2" "/media/robbie/4CA45547A4553524"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdc2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
[/I]



Does anyone know what commands would be useful for solving this error? Thank you.

---

### Post by sandyd on 2015-05-31
Windows was not shut down properly, as a result, there are two things you can do in Ubuntu.
Note that attaching the drive to a Windows computer and making it check the disk is probably the best thing to do.

1. Mount read only
```

sudo mkdir /mnt/tmp
sudo mount -t ntfs  -ro /dev/sdc2 /mnt/tmp

```
You should now be able to read the files at /mnt/tmp


2. Attempt to fix with ntfsfix
```

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdc2
```

---

