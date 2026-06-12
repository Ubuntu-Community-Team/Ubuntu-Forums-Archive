---
title: "File format for backup drive"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by bpgunner on 2008-10-21
When i set up a partition in my backup drive for Ubuntu, what file format should I use, and the type of partition, extended?

---

### Post by swisscow on 2008-10-21
Mine is ntfs so I can share files with the infrequently used windows partition I have. I don't believe it matters that much depending on what access it - but I will gladly stand and be corrected.

I have also used FAT32 without problem, and EXT2 in the past

---

### Post by bpgunner on 2008-10-21
I was going to use ntfs, but I didnt see that option in the Gparted tool, I want to do a compete image backup.
Should I make it a primary or extended?

---

### Post by swisscow on 2008-10-21
If you want ntfs I think you have to install ntfs-3g via synaptic and ntfsprogs.

As for primary or extended....????? Can't remember. Just used gparted to make one wacking great partition

---

### Post by bpgunner on 2008-10-21
Lol, ok!

---

### Post by drubin on 2008-10-21
I would use ntfs simplely because if there is an issue and you need to restore it you might not have access to a linux machine and it is easier to read ntfs then ext3 (I know you can download drivers for ext3)

---

### Post by swisscow on 2008-10-21
> **drubin said:**
> I would use ntfs simplely because if there is an issue and you need to restore it you might not have access to a linux machine and it is easier to read ntfs then ext3 (I know you can download drivers for ext3)

That is a good point. And it makes it more portable.

---

### Post by stinger30au on 2008-10-21
if worst comes to worst, there should be a utility on the free dos boot cd here

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

that will format the hdd to ntfs

or if it is external usb, plug it in to a windows xp machine and format it there

---

### Post by drubin on 2008-10-21
> **stinger30au said:**
> if worst comes to worst, there should be a utility on the free dos boot cd here

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

that will format the hdd to ntfs

or if it is external usb, plug it in to a windows xp machine and format it there

I have deff formated ubuntut with ntfs option. Cant remember what I did exactly might have been from the live cd though :)

---

### Post by wolfen69 on 2008-10-21
i use fat32 because any os will automatically mount it.

---

### Post by drubin on 2008-10-21
> **wolfen69 said:**
> i use fat32 because any os will automatically mount it.

Linux can now mount ntfs with very very little effort ubuntu mounts ntfs standard now with ntfs-3g

---

