---
title: "[SOLVED] fstab troubles"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Korijn on 2008-09-23
I have this line in the /etc/fstab file on my Ubuntu Server (command line) box:

```

/dev/sdb1       /media/external ntfs-3g defaults,utf8   0       0

```

When I just casually power it on it will mount properly. If I issue this command, the mount is suddenly gone:

```

sudo shutdown now -r

```

If I then issue this command:

```

sudo mount -a

```

It mounts properly!

What's wrong? It's incredibly annoying, I use the box to play around and learn more about Ubuntu but this is kind of crippling my progress. I use the disk very often. :)

Here's the full /etc/fstab file:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=26fabc9d-85c3-49fb-887f-764394730841 /               ext3    relatime,erro$
# /dev/sda5
UUID=244192d6-53df-4fe5-8d8d-284cbc118c12 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/external ntfs-3g defaults,utf8   0       0
/var/www        /home/korijn/www auto   bind    0       0
/var/www/torrentflux/downloads /home/korijn/downloads auto bind 0 0
/media/external/Muziek /home/korijn/muziek auto bind 0 0

```

---

### Post by bodhi.zazen on 2008-09-23
What is the question exactly ?

> sudo shutdown now -rreboots your computer , and as part of rebooting, disks are unmounted.

Assuming the reboot was aborted, sudo mount -a re-mounts them.

---

### Post by Korijn on 2008-09-24
Well, if I reboot the disks are logically unmounted indeed, but they are not mounted again afterwards.

---

### Post by bodhi.zazen on 2008-09-24
Ah, so they do not automagically mount when booting or rebooting.

Try updating your fstab line:

```
/dev/sdb1       /media/external ntfs-3g auto,rw,utf8   0       0
```

auto = auto mount
rw = read and write access.

---

