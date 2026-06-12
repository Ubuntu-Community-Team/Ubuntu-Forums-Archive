---
title: "Trouble uninstalling ubuntu"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Chafmere on 2008-06-04
I want to take ubuntu off my laptop. I need the extra space for work purposes. I thought a good way would be to reset factory settings on my acer aspire 5720z but it errors when I try to. Is there an alternate way to unistall ubuntu? Windows vista came pre-installed.

---

### Post by myusername on 2008-06-04
are you dual booting? if not you can just reinstall vista

---

### Post by billgoldberg on 2008-06-04
If you don't feel like reinstalling vista (or xp):

Format the ubuntu partitions (/, /home and swap).

I suggest using the gparted live cd (ubuntu live cd also has this program, so you could use that cd).

Let gparted format you linux partition(s), then format them to ntfs.

I wouldn't join the partitions toghether as this can take a very very very long time (I did it once and aborted after 4 days).

Then you can use the other partition from vista (or xp) to put files on.

But first you'll have to repair the vista or xp master boot record or vista (or xp) won't boot.

This can be done with the "super grub disk" (a live cd).

---

### Post by SunnyRabbiera on 2008-06-04
How big is the hard drive?
Vista is a space hog, what in vista do you need?
Ubuntu has plenty of its own work tools if you know where to find it.

---

### Post by Chafmere on 2008-06-04
I deleted the partition. When I restarted Grub wouldn't start (I was not aware that grub would still exist). Now I can't use my computer for anything!!! Help. I was duel booting and now i'm using my ubuntu live cd!!!

---

### Post by myusername on 2008-06-04
pop in a windows install or restore cd and go to repair (NOT AUTO REPAIR!) and do this from the command line:

fixboot

then

fixmbr

and you should be ok

---

### Post by Chafmere on 2008-06-04
I don't have a windows CD!!! Vista came pre-installed!!

I'm looking at that "Super Grub Disk" to help me.

---

### Post by billgoldberg on 2008-06-04
Super grub disk will have an option to boot into windows or repair the master boot record.

(1000th post :p :p :p)

---

### Post by cacycleworks on 2008-06-04
+1 about just reinstalling windblows. That would be the system restore media.

---

