---
title: "mount the volume read-only with the 'ro' mount option"
date: 2016-06-13
forum: New to Ubuntu
---

### Post by 20GT on 2016-06-13
Ive searched and found... start with "Make a mount point" call it anything you like.
but I have no idea what that is.


```
Error mounting /dev/sda1 at /media/steve/9016A0A716A09030: Command-line  `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000"  "/dev/sda1" "/media/steve/9016A0A716A09030"' exited with non-zero exit  status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```

---

### Post by Impavidus on 2016-06-14
"Make a mount point" means that you have to create an empty directory. Any directory can serve as a mount point, and technically it doesn't even have to be empty, but it's easiest if you just take an empty directory. If you're doing this in terminal, use```
mkdir <name of directory>
```It's best to avoid spaces in the name, or else escape them.

---

### Post by oldfred on 2016-06-14
It also looks like you have left Windows 8 or 10 with fast start still turned on. That is always on hibernation and the Linux NTFS driver will not mount a NTFS partition that is hibernated nor if it needs chkdsk.

I have used these as mount points.
/mnt/data
/mnt/shared
/mnt/Windows

The auto mount is usually in /media/$USER, but I manually mount in /mnt. The /media mounts show in left panel of Nautilus. But I link all folders into /home, so I do not want it in Nautilus so /mnt works.

 Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0 

Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

Partitions I do not want mounted all the time, or only use occasionally, I label them, so they mount by label not UUID which I do not know which is which.

       [URL="https://help.ubuntu.com/community/Fstab"]https://help.ubuntu.com/community/Fstab
[/URL]
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. [URL="https://help.ubuntu.com/community/Fstab"]
[/URL]

---

### Post by 20GT on 2016-06-16
thanks for all the help
this also help immensely
[https://www.quora.com/How-do-I-mount-a-drive-in-read-only-mode-in-Ubuntu](https://www.quora.com/How-do-I-mount-a-drive-in-read-only-mode-in-Ubuntu)

---

