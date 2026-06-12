---
title: "Mounting Windows 8.1 Partition"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by snerd2 on 2014-04-13
Sorry, I know there are many threads of this question, but I have had no luck at all. Running 14.04 LTS final beta, I have turned off fast start in Windows, even turned system off completely, and still no luck. It says Windows is in an unsafe state. I don't know where to begin now. Thank you.

---

### Post by snerd2 on 2014-04-13
Error mounting /dev/sda1 at /media/snerd/Local Disk: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda1" "/media/snerd/Local Disk"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

---

### Post by westie457 on 2014-04-13
Welcome to the Forum snerd2.

> [COLOR=#000000]The NTFS partition is in an unsafe state. Please resume and shutdown[/COLOR]
[COLOR=#000000]Windows fully (no hibernation or fast restarting), or mount the volume[/COLOR]
[COLOR=#000000]read-only with the 'ro' mount option.[/COLOR]

There is the problem and what  you need to do. This is probably the best way to disable fastboot.

[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

And this to disable hibernation.

[http://www.eightforums.com/performance-maintenance/4932-how-turn-hibernate-completely-off.html](http://www.eightforums.com/performance-maintenance/4932-how-turn-hibernate-completely-off.html)

---

### Post by Mark Phelps on 2014-04-13
Even when you are able to mount it, you should mount the OS partition read-only.  Making changes to a Windows OS NTFS partition from inside Ubuntu risks corrupting the Windows filesystem -- which may then prevent it from booting, making it really hard to repair.

---

