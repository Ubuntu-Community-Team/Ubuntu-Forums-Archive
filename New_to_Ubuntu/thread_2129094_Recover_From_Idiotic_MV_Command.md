---
title: "Recover From Idiotic MV Command?"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by philwx on 2013-03-25
I have trashed my Ubuntu 12.04 file system with an idiotic mv command. 

```
/var/www$ sudo mv /* /var/www/drupal
```

Ahhhh! To recover I tried:
```
/var/www$ sudo mv /var/www/drupal/* /
```
and
```
/var/www$ sudo mv /var/www/drupal/* /..
```

Both these returned:
```
bash: /usr/bin/sudo: No such file or directory
```

I am posting this from another pc. The trashed PC is sat waiting for my next move. Is there anything I can do to recover this?

Please help. And of course feel free to mock me.

---

### Post by sandyd on 2013-03-25
> **philwx said:**
> I have trashed my Ubuntu 12.04 file system with an idiotic mv command. 

```
/var/www$ sudo mv /* /var/www/drupal
```

Ahhhh! To recover I tried:
```
/var/www$ sudo mv /var/www/drupal/* /
```
and
```
/var/www$ sudo mv /var/www/drupal/* /..
```

Both these returned:
```
bash: /usr/bin/sudo: No such file or directory
```

I am posting this from another pc. The trashed PC is sat waiting for my next move. Is there anything I can do to recover this?

Please help. And of course feel free to mock me.
You are currently missing the sudo binary (and the dynamic loader, ld-linux.so has probably become messed as well)

What I would suggest:

Boot to a Linux LiveCD, mount the Ubuntu partition there, and move the folders back to their original location.

If you post the output of
```

sudo fdisk -l
``` from a livecd,
we can probably help you further by giving you complete commands to run.

---

### Post by philwx on 2013-03-25
Thanks for helping sandyd. Here's the output:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a4aba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   972648447   486323200   83  Linux
/dev/sda2       972650494   976771071     2060289    5  Extended
/dev/sda5       972650496   976771071     2060288   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe9f8e9f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488392064   244196001    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 15.9 GB, 15892217856 bytes
255 heads, 63 sectors/track, 1932 cylinders, total 31039488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009c707

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    31037579    15518758+   c  W95 FAT32 (LBA)

```

---

### Post by philwx on 2013-03-25
I have mounted sda1 to /mnt. I have changed directory to /mnt/var/www/drupal.

Should I do this?
```

ubuntu@ubuntu:/mnt/var/www/drupal$ sudo mv /mnt/var/www/drupal/* /mnt/ 
```

---

### Post by philwx on 2013-03-25
Ok I did perform the command and everything is back and running just fine.

Thanks sandyd. 

(btw I have a little 3 legged dog but I love cats too)

---

### Post by philwx on 2013-03-25
I am having a really stupid day. How do I mark this thread as SOLVED?

There is nothing regarding solved on the thread tools menu (only print, email and subscribe items).

Found solution for marking as SOLVED here: [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

