---
title: "[SOLVED] problem reducing windows partion size to dual boot with Ubuntu"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by pjvandehaar on 2008-07-06
I'm using a live cd on a 2000 gateway that came with xp. I tried to install Ubuntu 8.04, but whenever I get to the fourth step- creating partitions for Ubuntu, I run into trouble. If I choose "Guided- resize windows partition", then after five minutes of loading, it has an error resizing the partition. I've looked for help using manual but can't find what I'm looking for. I want to dual boot Ubuntu with xp, but would like to keep my xp files(though I don't care too much), and don't want to lose all my windows programs. Any help?
Also, when I open GPARTED, it shows the red triangle with an exclamation point symbol next to my windows partition.

---

### Post by sayakb on 2008-07-06
If has a NTFS filesystem, then you might **defrag it a couple of times** before resizing. NTFS has fragmented data all over the disk and you need to get the data pushed to one side in order to shrink it from the other end.

---

### Post by L Campbell on 2008-07-06
> **pjvandehaar said:**
> I'm using a live cd on a 2000 gateway that came with xp. I tried to install Ubuntu 8.04, but whenever I get to the fourth step- creating partitions for Ubuntu, I run into trouble. If I choose "Guided- resize windows partition", then after five minutes of loading, it has an error resizing the partition. I've looked for help using manual but can't find what I'm looking for. I want to dual boot Ubuntu with xp, but would like to keep my xp files(though I don't care too much), and don't want to lose all my windows programs. Any help?
Also, when I open GPARTED, it shows the red triangle with an exclamation point symbol next to my windows partition.

You may want to look at this:-

[http://wubi-installer.org/](http://wubi-installer.org/)

I installed it on my XP computer recently and the download and installation procedure was perfectly smooth and easy.

Hope this helps.

---

### Post by bumanie on 2008-07-06
Agree with linuxisinnovation. Also, I think if there is a red trinagle with an exclamation mark, when using gparted, that is telling you that the partition is mounted and thus cannot have changes made to it. If windows was not shutdown correctly, it will appear to linux as that it is still in use. Reboot windows ensure proper shutdown and try again - but defrag at least twice first.

---

### Post by sailor2001 on 2008-07-06
windows xp has it's own partition manager......rt. click "mycomputer" "manage/hard drives    Hope that's the right wording......haven't been in xp for a year. Then ti install..use "select largest freespace"

---

### Post by pjvandehaar on 2008-07-06
Thanks! I think fragmentation was the problem. It's in the middle of defragging right now. I'll try installing from the live cd next, and if I there are problems I think I'll try Wubi.

> **sailor2001 said:**
> windows xp has it's own partition manager......rt. click "mycomputer" "manage/hard drives    Hope that's the right wording......haven't been in xp for a year. Then ti install..use "select largest freespace"
I right clicked mycomputer, went to manage, then to storage/disk management, but didn't see a way to make a new partition.
I think I can get everything to work through gparted and the installer, though.

---

### Post by Kevbert on 2008-07-06
You may find you still have data towards the end of the disk.  This is the windows paging (swap) file which may be causing the problem. If this block of data has not been moved when you defrag the drive, you'll need to turn off this file. It can be found at Control Panel - System - Advanced Tab. Now click on Settings under Performance and select the Advance Tab. Now click on Change, the Virtual Memory paging file and select the No Paging File radio button. No click on Set, OK, OK, OK and close Control Panel.
Reboot the machine and then defrag the hard disk again. There should now be extra room at the end of the disk.
Don't forget to back everything up and turn on the paging in windows once you've sorted out Ubuntu.

---

### Post by pjvandehaar on 2008-07-06
I would prefer to not have to back everything up, since it would take 5 dvds. Will installing Ubuntu make me for sure lose everything? If its about a 50% chance I'll probably just go for it. And is their any/very much chance of me losing programs and xp itself, because I don't want to lose those.

---

### Post by Kevbert on 2008-07-06
It's unlikely that you'll loose anything, but occasionally something unexpected might happen.

---

### Post by pjvandehaar on 2008-07-07
I think I figured it out. The problem was fragmentation and my computer only had 11 GBs free. I was trying to take 10 of them for a new partition. I tried only 7 and (it took 4 hours) it worked.

---

