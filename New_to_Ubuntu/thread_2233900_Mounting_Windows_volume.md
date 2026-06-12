---
title: "Mounting Windows volume"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by shalom3 on 2014-07-11
I want to access files in the partition with windows 8.
but when i mount the partition it provides the following message

> Error mounting /dev/sda4 at /media/shalom/Windows 8: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda4" "/media/shalom/Windows 8"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

how can I successfully mount the windows volume? 
Windows is not running in background (im not sure how that's possible) what is mounting with "ro" mount option? if i do that can i copy files?

---

### Post by sotiris2 on 2014-07-11
I think you have to disable fast startup on windows8 so they really shut down instead of semi-hybernating. See [here](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html) for a guide.

---

### Post by Impavidus on 2014-07-11
+1.

Mounting with the ro option means mounting read-only. In that case you can copy files from the Windows partition, but not to it. In any case it's best to only write to Windows data partitions, not to the OS partitions (the "C:\ drive" or recovery partitions), as it's easy to damage Windows.

---

