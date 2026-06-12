---
title: "New installation: Help with partitioning SSD"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by aeron2 on 2014-02-27
Hey guys,

i have built my fist home server, and i am planning to install Ubuntu Server on it.
I will use it only as a media server, and some backup for my photo's and documents.
I have 1 x Samsung 840 Evo SSD 128GB installed for the OS, and 3x 2tb HDD's for storage of my movies, tv shows and music.
On the OS drive (SSD) i will install things as Sabnzbd+, Sickbeard, Plex, as wel as a Samba server to share in XBMC on my Mac Mini.
I am not going to install other OS's on the SSD, just Ubuntu Server.

Now on to my question:

Most of the tutorials i have found mention to choose the partitioning option " Guided - Use entire disk and setup LVM ".
[FONT=Verdana][SIZE=2][COLOR=#666666]But, since i use the entire SSD as an OS drive only, shouldn't i choose " Use Entire Disk " instead?
[/COLOR][/SIZE][/FONT]Or is it wise to create one big partition?
The thing is, according to several people, it is wise to have some unallocated space (Overprovisioning?) for an SSD, about 10% of the SSD capacity.
In this case, i DO have to use the LVM option, right?

I hope someone can point me out in the right direction!

---

### Post by nunecas123 on 2014-02-27
Well, it's always very convenient to have a spare partition, at least for security reasons (backup files, for example).
I recommend you to have another partition, as it is always safer. ;)

---

