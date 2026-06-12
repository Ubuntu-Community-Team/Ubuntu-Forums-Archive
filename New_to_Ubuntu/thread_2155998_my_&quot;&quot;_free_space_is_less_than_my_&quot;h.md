---
title: "my &quot;/&quot; free space is less than my &quot;/home&quot; free space. How can it be?"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by benamsalem on 2013-06-20
when I run "df" in command line, i get:
```
Filesystem           1K-blocks     Used Available Use% Mounted on
/dev/mapper/VG1-root   9611492  8947704    175548  99% /
udev                                4023732     12            4023720     1% /dev
tmpfs                               1614416    1044         1613372     1% /run
none                                5120          0              5120           0% /run/lock
none                                4036040    4316         4031724      1% /run/shm
/dev/sda3                         457760      359486     73852        83% /boot
/dev/mapper/VG1-home     706955360 29089456 641954636   5% /home
```

as you can see seems like the home is bigger than the root. does it make sense? the root is not the container of /home?
I have to mention that I have an encrypted system, so maybe it affects somehow.
anyway, I will really be great if you can suggest me where to store file from "/" (it's in 99% use as you can see)

---

### Post by steeldriver on 2013-06-20
Hello and welcome to the forum

You have an LVM-based installation, with / and /home in separate logical volumes (like separate partitions - only a bit less permanent), so no in this case root is *not* the container of home although they likely exist within the same volume group and physical volume (partition)

The first thing you should probably do is see if you can clean up / with regular housekeeping:

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

If that doesn't free up enough space, then you could consider shrinking your home volume and extending your root volume using LVM tools

---

### Post by benamsalem on 2013-06-20
I think I get you, but something weird in my system - when I try to cleanup the root, I see the /home under "/" (actually that where most of the used storage located), so I can't move files from /home to /home, it would worth nothing...

---

### Post by capscrew on 2013-06-20
> **benamsalem said:**
> I think I get you, but something weird in my system - when I try to cleanup the root, I see the /home under "/" (actually that where most of the used storage located), so I can't move files from /home to /home, it would worth nothing...

What you are seeing is not /home **in** /.  Rather /home is **attached** to /.  You have 2 volumes (/dev/mapper/VG1-root and /dev/mapper/VG1-home).  The filesystem are different but connected together (one mounted to another)  In your case  /home is mounted to the filesystem / at the mount point of /home.  It might make it clearer if I use an example of what I do.  I have a partition that I mount at /srv/samba and another partition that I mount at /data.  Neither of these partitions are physically (HDD) part of the partition that is mounted at /.  One attaches at /data and the other at /srv/samba.  A mount point is nothing more than a directory that you choose to mount a separate filesystem to.

Note the header (in red) from the df command```
[COLOR="#FF0000"]**Filesystem**[/COLOR]           1K-blocks     Used Available Use% [COLOR="#FF0000"]**Mounted on**[/COLOR]
```

---

