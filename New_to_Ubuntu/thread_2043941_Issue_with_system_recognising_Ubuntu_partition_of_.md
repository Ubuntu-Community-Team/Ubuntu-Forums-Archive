---
title: "Issue with system recognising Ubuntu partition of hard-drive from previous computer"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by SiddharthaWolf on 2012-08-17
Hi, I recently had a problem with my previous laptop due to what was probably the influence of an electrical storm. I believe it affected the processor/fan, as the computer began shutting down randomly at increasingly shorter intervals. At one point I stupidly tried to reinstall ubuntu (thinking my problem may be a software-related one), but of course it closed down mid-install, leaving me unable to access Ubuntu any more.

I got a new computer today and mounted the previous hard-drive as external, and initially it was showing the Ubuntu partition as accessible. However, the domain I wished to access (/home) must have been encrypted, as I was unable to see all the contents (instead only seeing two read-only files whose names I can't remember). Stupidly - again - I tried opening it through Windows 7, and it asked me if I wanted to check the disk for errors. I did, and now the partition is showing up as "Unknown" in Gparted, and not at all in Ubuntu or Windows. Does anybody have any advice for how I may be able to access it? It would be much appreciated. :)

---

### Post by SiddharthaWolf on 2012-08-17
Just a quick update - I ran testdisk on the drive, following a recommendation I found elsewhere, and it ran fine except for a short section where it said "Read Error at 76004/38/21" as well as saying "Warning: number of heads/cylinder mistmatches" and the same about sectors per track.

---

### Post by Bashing-om on 2012-08-17
--wolf;
  HI ... A word to the wiser: Windows tools for windows problems, Unix tools for ubuntu situations. 
That said try this, from the terminal:
```
sudo fdisk -l
```to find the name of the external device as ubuntu sees it.
then try and check/fix the file system with:
```
sudo fsck -f /dev/sdX
```where 'X'  is the designater from the fdisk command.
[INDENT]HTH <==BDQ


edit: do the file system check/fix with the disk unmounted .. preferably from the live CD or other external means.




[/INDENT]

---

