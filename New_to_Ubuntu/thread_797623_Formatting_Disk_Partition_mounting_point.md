---
title: "Formatting Disk Partition mounting point?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Swatfoot on 2008-05-17
Ok I want to give more space to linux right now Im dual booting vista and linux Ive decided I want linux as my main OS I have my partition like this
30 gigs for linux 5 gigs for linux swap 220 gigs for windows vista.I want 220 gigs for linux 5 gigs linux swap and 30 gigs for vista.I dont think there is a way of not losing vista but how do I copy my current Linux Files to the 220 gig ntfs partition and change the mounting point.I need to format my current 30 gig partition to ntfs so i can install vista back on to it.

---

### Post by sam_delta on 2008-05-17
you just need to resize the partitions, you can do this, by booting into the live CD, and running a tool called "gparted" (click alt+F2 and type gksudo gparted) and there you can resize/move any partition to your desired size, ,, if your able to, its always good to backup any important data on the disks

tell us how it goes,
sam

---

### Post by FuturePilot on 2008-05-17
I would recommend the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php"). With that you can resize your current partitions. No need to reinstall or move files around. Although it's a good idea to back up your important data whenever playing around with partitions.

---

