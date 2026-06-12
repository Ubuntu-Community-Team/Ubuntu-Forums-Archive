---
title: "unable to resize ntfs"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by vincentvega_1985 on 2008-05-27
hey guys!

i just got a new laptop with windows media center edition preinstalled. I wanted to shrink the ntfs partition, because i really want to keep this windows, and there's only a recovery disc with it, which formats the whole disc and installs it from scratch.
I've tried several ways, with the ubuntu live cd, with gparted live cd, with gparted in the ubuntu live cd, with partition magic. The first 3 ways wouldn't let me do anything. it told me, the ntfs partition is mounted and can't be unmounted. partition magic told me it can do it, but whenn the pc restarts and the trys to make the changes, it tells me about some error and restarts.

can anyone helps me? i'd really appreciate it!

cheers

---

### Post by sayakb on 2008-05-27
Defrag your NTFS partition and try again with partition magic. NTFS partitions have fragments of data all over and defragmenting would arrange it to the beginning of the disk.

---

### Post by vincentvega_1985 on 2008-05-27
i defragmented it several times before, forgot to write that. but there is some data a little further in the disc, which apparently can't be moved.
it's a 120 gig disc, i want to shrink it to 30, and the unmoveable data is definitely inside the first 30 gigs

---

### Post by kansasnoob on 2008-05-27
Since you say "brand new" describing your Media Center I assume you have either Vista Premium or Ultimate. I'd personally NOT use Gparted to do the partitioning, although it is possible, I'd prefer to use Vista's Disk Management tools as outlined in this tutorial:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Just be aware that there is always about a 5% chance of losing data or screwing up your Windows OS!

---

### Post by logos34 on 2008-05-27
> **kansasnoob said:**
> Since you say "brand new" describing your Media Center I assume you have either Vista Premium or Ultimate. I'd personally NOT use Gparted to do the partitioning, although it is possible, I'd prefer to use Vista's Disk Management tools as outlined in this tutorial:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Just be aware that there is always about a 5% chance of losing data or screwing up your Windows OS!

+1. In fact, from all I've read, I'd go further: NEVER use anything other than Vista's disk utility to resize.

OTH, if it's XP MCE you have, then take a look at this:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

---

### Post by forestpixie on 2008-05-27
Also it could well be the pagefile, I've had to turn that off and then defrag before now before I could move on, but the vista and it's disk managemnt ttol is a good point indeed.

---

### Post by Duck2006 on 2008-05-27
> **logos34 said:**
> +1. In fact, from all I've read, I'd go further: NEVER use anything other than Vista's disk utility to resize.

OTH, if it's XP MCE you have, then take a look at this:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

+2 on that one.

---

