---
title: "[SOLVED] Eeepc: SD card writable by root only"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by t0p on 2008-10-31
I'm running Hardy on an Eeepc 701.  I've got a 4GB SDHC card mounted permanently to act as back-up storage.  Problem is, the card is writable by root only.

Here's the */etc/fstab*:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c0c8253c-ec64-49e1-86a8-d844c7628449 /               ext3    noatime,errors=remount-ro 0       1
# /dev/sda5
UUID=51dde39a-71e4-4607-bacc-877963971657 none            swap    sw              0       0
/dev/sdb1     /media/MMCSD     auto     user,auto,exec,rw     0     0

```

The card is */dev/sdb1*.  Can anyone tell me how to make the card writable by my user account without having to use *sudo*?

---

### Post by stephanvaningen on 2008-10-31
It is possible in fstab to provide permissions information in that line (cfr. the umask-parameter of the mount command). I suggest you configure that for your SD-card.
You can add "umask=ugo" in the fstab's fourth column.
i.e: 
 ```
/dev/sda5 /media/fat vfat umask=777 0 0
```

The 777 is drastic, but means that user, group and others may read, write and execute anything on it...

---

### Post by t0p on 2008-10-31
> **stephanvaningen said:**
> It is possible in fstab to provide permissions information in that line (cfr. the umask-parameter of the mount command). I suggest you configure that for your SD-card.
You can add "umask=ugo" in the fstab's fourth column.
i.e: 
 ```
/dev/sda5 /media/fat vfat umask=777 0 0
```

The 777 is drastic, but means that user, group and others may read, write and execute anything on it...

Okay, I don't know what you're on about,

Can someone please tell me how I can make the SD card, /dev/sdb1, writable for my user account without sudo?

---

### Post by t0p on 2008-10-31
Okay, after pondering stephanvaningen's advice, I thought I got it.  So, I changed the line in /etc/fstab that begins /dev/sdb1 so it read:

```
/dev/sdb1   /media/MMCSD   vfat   umask=777   0   0
```

Then I restarted the computer, navigated to the card in nautilus... and got an error message that I didn't have permission to view the card's contents!  *Sneck!!*

So, I still need some help, people.

---

### Post by t0p on 2008-10-31
I've read a [guide to editing /etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html"), and I'm as confused as ever.

This is the relevant line in my /etc/fstab:

```
/dev/sdb1     /media/MMCSD     auto     user,auto,exec,rw     0     0
```

In the 4th column, the word *user* is supposed to mean /dev/sdb1 is mountable by a regular user.  If it was supposed to be mountable only by root, it would read *nouser* instead... except it is root-mountable only.

This is flaming ridiculous...

---

### Post by t0p on 2008-11-02
Okay, problem solved.  I edited /etc/fstab, changing the /dev/sdb1 line to:

```
/dev/sdb1   /media/MMCSD   vfat   umask=000   0   0
```

See, the umask value needed to be 000, not 777 as suggested by stephanvaningen.  Anyway, my user account can now write to the card (though it still can be mounted and unmounted only by root... dunno how to fix that...)

---

