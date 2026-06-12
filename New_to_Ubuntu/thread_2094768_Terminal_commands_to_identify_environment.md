---
title: "Terminal commands to identify environment"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by GordThompson on 2012-12-14
I've been reading a lot of posts in this forum recently and have learned a great deal. However, while I've seen lots of terminal commands to display the OS and kernel versions, enumerate hardware, show networking status, etc., I haven't yet found ones that would reliably identify

1. The active desktop environment.

2. Whether the session is _not_ persistent, e.g., running from a Live CD or equivalent. (From my own mucking about I wonder if grepping /etc/fstab for 'aufs' could be used as a reliable indicator?)

Thanks for any pointers!

---

### Post by debodas on 2012-12-14
echo $DESKTOP_SESSION  - identifies desktop environment.

---

### Post by tgalati4 on 2012-12-14
Yes, grepping fstab would be a reliable way to do it.  Although there are many, many live CD/DVD's you would have to compile a list of markers to uniquely identify each different type of live environment.

When logged into my freenas file server I find the following:

[tgalati4@freenas ~]$ cat /etc/fstab
# Device                Mountpoint      FStype  Options         Dump    Pass#
/dev/ad1s1a             /       ufs     rw              1       1
proc /proc procfs rw 0 0
# Used for htop if I can ever get it to work
# linproc /compat/linux/proc linprocfs rw 0 0

freenas runs the ufs file system and it is running from a hard disk, not a live usb or CD.

But on my Jaunty laptop:


tgalati4@tpad-Gloria7 ~ $ echo $DESKTOP_SESSION
default

Which is not very helpful in identifying that I am running a Gnome2 desktop.

---

### Post by bab1 on 2012-12-14
> **tgalati4 said:**
> Yes, grepping fstab would be a reliable way to do it.  Although there are many, many live CD/DVD's you would have to compile a list of markers to uniquely identify each different type of live environment.

When logged into my freenas file server I find the following:

[tgalati4@freenas ~]$ cat /etc/fstab
# Device                Mountpoint      FStype  Options         Dump    Pass#
/dev/ad1s1a             /       ufs     rw              1       1
proc /proc procfs rw 0 0
# Used for htop if I can ever get it to work
# linproc /compat/linux/proc linprocfs rw 0 0

freenas runs the ufs file system and it is running from a hard disk, not a live usb or CD.

But on my Jaunty laptop:


tgalati4@tpad-Gloria7 ~ $ echo $DESKTOP_SESSION
default

Which is not very helpful in identifying that I am running a Gnome2 desktop.

I would use ```
user@host~$** env**
```
Amongst other things it shows```
GNOME_DESKTOP_SESSION_ID=Failsafe
```...in my case

---

### Post by tgalati4 on 2012-12-14
tgalati4@tpad-Gloria7 ~/Desktop $ env | grep DESKTOP
DESKTOP_SESSION=default
GNOME_DESKTOP_SESSION_ID=this-is-deprecated

No help here either.

---

