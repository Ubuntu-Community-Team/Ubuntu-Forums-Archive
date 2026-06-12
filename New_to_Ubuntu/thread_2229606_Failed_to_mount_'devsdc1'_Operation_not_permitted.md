---
title: "Failed to mount '/dev/sdc1': Operation not permitted"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by omally2 on 2014-06-14
Hi,

I was running win 7 and Ubuntu with dual boot everything ok.
I was given win 8 as a present and upgraded win 7 to 8.
Dual boot still works but when in Ubuntu I cant access any of the hard drives.
Get this message:
Error mounting /dev/sdc1 at /media/weights/New Volume: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdc1" "/media/weights/New Volume"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdc1': Operation not permitted
The NTFS partition is in an unsafe state........

Its got to be something to do with win 8!
Please Help 

I hate windows!!!!

---

### Post by gaxfax on 2014-06-14
Win8 keeps the disk 'on' by default, sorry I can't remember the name of the process to disable, something to do with "Fast Startup".
got rid of that mess myself.

Check here:
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by sudodus on 2014-06-14
I think the problem is caused by hibernation. Windows 8 hibernates by default, a method to make it boot faster. It can be hard to disable it completely, but I managed to do it this way (more than a year ago, before 8.1, I hope the method is still valid).

[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

See this link for more details
[URL="http://ubuntuforums.org/showthread.php?t=1769482&page=52&p=12608648#post12608648"]
[Boot-Repair] Graphical tool to repair the PC boot in 1 click! #1038[/URL]

---

