---
title: "[SOLVED] Samba Errors with Nautilus as root"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by 44tr on 2008-09-16
Hi!  I just got through changing my son's username on his computer with the help of this thread:

 [http://ubuntuforums.org/showthread.php?t=918809](http://ubuntuforums.org/showthread.php?t=918809)

At the end, I noticed that I get some unusual errors when I open nautilus as root that I would like explained and addressed.

```
druid@chris-desktop2:~$ gksudo nautilus
Initializing nautilus-share extension

** (nautilus:6641): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

seahorse nautilus module shutdown
druid@chris-desktop2:~$
```

This error only occurs when I open nautilus as root.  I have no local printer connected, just print over the network. So can someone help me please? :)

---

### Post by 44tr on 2008-09-18
Either no one knows what is causing this, or it isn't very important to fix I guess.  Ideas or comments?

---

### Post by mc4man on 2008-09-18
i don't know anything about samba but *possibly* there is a connection between what happens when you run gksudo nautilus and 'samba'.

When you run gksudo nautilus the system will attempt to mount any unmounted 'removable media'(shared?) under root. If the 'media' is unmountable. then nautilus will segfault.

This is easily observed by inserting a blank cd/dvd in a drive and running gksudo nautilus. (segfaults

or

If you were to have a usb drive connected but _not mounted_ it will mount under root (unless it's borked and unmountable, then a segfault.

If your 'samba' is treated the same way and 'unmountable' then you'll get a segfault

---

### Post by pro003 on 2008-09-18
happens all the time when trying to browse samba network with nautilus. But why use it? Is there a problem browsing as regular user? For me there are many improvements of samba in 8.04

---

### Post by 44tr on 2008-09-19
> **pro003 said:**
> happens all the time when trying to browse samba network with nautilus. But why use it? Is there a problem browsing as regular user? For me there are many improvements of samba in 8.04

I still use nautilus to copy and paste files.  If you do it as a regular user, you don't have the permissions to write files to the file system or read them from unmounted ntfs partitions (a lot easier to mount a partition in nautilus when you don't remember the device name.

I know there is probably a more efficient command line way, but it doesn't help when you don't know what it is, or it takes more time to find out and remember.  Thanks for the input though.

---

### Post by 44tr on 2008-09-19
Thanks to the hint, I figured out that part of the error was that I didn't share any folders (I installed samba just to share printer); once I shared my Public folder, that part of the error went away.  Now I just have this left:

```
chris@office1:~$ gksudo nautilus
Initializing nautilus-share extension

** (nautilus:8189): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSseahorse nautilus module shutdown
chris@office1:~$ 

```

I am using Nautilus 2.22.3 which is the latest stable version in Ubuntu 8.04.  I wonder what kind of 'monitor' nautilus is trying to add ...  other ideas, or should I not worry about it?

---

