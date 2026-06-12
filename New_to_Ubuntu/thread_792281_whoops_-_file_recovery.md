---
title: "whoops - file recovery?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by intheevening on 2008-05-12
I installed ubuntu earlier, from a live disc, on a laptop that was running windows XP. Noob that I am, I went with the guided partitioning, and, noob that I am, made a mess of it. 

I had assumed that the data existing on my hard disk would be put into one partition, and then ubuntu would set up its partitions. Of course, what actually happened is that I lost all of the data I had. 

I can't say I'm massively fussed about losing windows xp, but some of the actual files I would rather, you know, not lose. 

Once I realised what I did, I started up again running from the live disc and desperately tried to recover something with gpart or parted. I even tried ntfsundelete. Unsurprisingly, none of this was to any avail, I don't have much idea what I am doing.

So, a desperate plea for help?

---

### Post by jnorth on 2008-05-12
> **intheevening said:**
> I installed ubuntu earlier, from a live disc, on a laptop that was running windows XP. Noob that I am, I went with the guided partitioning, and, noob that I am, made a mess of it. 

I had assumed that the data existing on my hard disk would be put into one partition, and then ubuntu would set up its partitions. Of course, what actually happened is that I lost all of the data I had. 

I can't say I'm massively fussed about losing windows xp, but some of the actual files I would rather, you know, not lose. 

Once I realised what I did, I started up again running from the live disc and desperately tried to recover something with gpart or parted. I even tried ntfsundelete. Unsurprisingly, none of this was to any avail, I don't have much idea what I am doing.

So, a desperate plea for help?

For starters to clarify what you did on installation, how about an output of the following commands (run these from your terminal under the Accessories menu).  You can do a "cat --help" and "fdisk --help" if you want to verify that the commands I am giving you won't hurt your system.
```
cat /etc/fstab
```
```
cat /boot/grub/menu.lst
```
```
sudo fdisk -l /dev/sda
```

---

### Post by litago on 2008-05-13
You should take a look at this post: [http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)
Might use it myself :)

---

### Post by intheevening on 2008-05-13
> **jnorth said:**
> For starters to clarify what you did on installation, how about an output of the following commands (run these from your terminal under the Accessories menu).  You can do a "cat --help" and "fdisk --help" if you want to verify that the commands I am giving you won't hurt your system.
```
cat /etc/fstab
```
```
cat /boot/grub/menu.lst
```
```
sudo fdisk -l /dev/sda
```
Sure thing:
> ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4185853a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9553    76734441   83  Linux
/dev/sda2            9554        9729     1413720    5  Extended
/dev/sda5            9554        9729     1413688+  82  Linux swap / Solaris
From what I can tell, it is not that I've lost a partition as much as I have completely overwritten what was originally on the hard disk when creating the current partitions, and I'd quite like some of what was on the hard disk back ;). 

I thought about perhaps trying to convert the primary partition into ntfs - which I hope it was before I installed ubuntu - and then using ntfsprogs...? I'm really not sure.

**edit:**

It seems like an awful lot of people have fallen into this trap, from what I've seen googling. It looks like I may just have to invest in some proper file recovery. 

And back-up in future ^^.

---

### Post by jnorth on 2008-05-13
> **intheevening said:**
> From what I can tell, it is not that I've lost a partition as much as I have completely overwritten what was originally on the hard disk when creating the current partitions, and I'd quite like some of what was on the hard disk back ;). Yeah I was kind of hoping that maybe you left it at guided and the partition was still there, just not accessible. (Wasn't sure how familiar you were with partitioning)  You're right though, you overwrote it :)

> **intheevening said:**
> I thought about perhaps trying to convert the primary partition into ntfs - which I hope it was before I installed ubuntuMost likely it was if you had XP

> **intheevening said:**
> and then using ntfsprogs...? I'm really not sure.
**edit:**
It seems like an awful lot of people have fallen into this trap, from what I've seen googling. It looks like I may just have to invest in some proper file recovery. 
And back-up in future ^^.Depends on how much you want to spend on it.  I've found some file recovery services to be priced to the point of exclusion for me personally, but it depends on your data.  If it's something you can live with losing, but want to make at least an attempt at doing yourself, then I would (as in the post above) give testdisk a try.  I'd personally recommend booting up from a livecd, doing an apt-get install testdisk from the livecd terminal, and then proceeding from there.  Less chance of overwriting even more data that way.

---

