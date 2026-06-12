---
title: "How to access raid array files on Iomega 2 TB EZ Media &amp; Backup Center"
date: 2016-07-17
forum: New to Ubuntu
---

### Post by homer1956 on 2016-07-17
I'm new to Ubuntu and Linux and I was directed to use Ubuntu to access the lost files on my failed Iomega 2 TB EZ Media & Backup Center hard drive. The NAS hardware failed after performing a required firmware update and now I can't access the 1+ TB files I have stored on it.I purchased an external USB 3 enclosure and when I plug it into my USB 3 port I can't see it in Ubuntu File Manager. I know it's there because the disk manager recognizes it so I captured a couple of screen shots with the info I can get. Any help would be great. Thanks.

[ATTACH]270151[/ATTACH]
[ATTACH]270152[/ATTACH]

---

### Post by Incarnadine on 2016-07-17
Do you know which RAID configuration you were using? RAID 0, RAID 1, etc. Let us know, as this bit of information is crucial.

---

### Post by homer1956 on 2016-07-21
Sorry for the delayed reply but was busy watching the RNC. I cannot get enough info from the drive other than what I screenshotted. The partitions are not the same size so I'm pretty sure it's not striped so what would that make it? Is there somewhere else I can look to get the info on the drive structure? Thanks for responding.

---

### Post by Incarnadine on 2016-07-21
The screen shots don't tell me much, other than the fact that the drive you have plugged in is in fact a "Linux RAID Member," so the drive definitely belongs to a RAID.

My first point of troubleshooting would be to log into the RAID box, but I'm assume that your RAID box is toast and completely unresponsive, since it failed a firmware update and you're resorting to taking the drives out for recovery.

OK, considering that the RAID box is indeed completely dead, you're on the right track, but it's important to plug in all drives from the RAID in order to start recovery. If you had the RAID running in RAID 1, then you could simply break the RAID on a single drive and try to access the information, but I doubt this is the case, so all drives have to be plugged in. Hopefully you have a full ATX case to install these drives in.

Once all the drives are installed, open your "Disks" app in Ubuntu and see what options it gives you. It should recognize that you have a complete RAID setup plugged in and you should be able to initialize the RAID and mount the drives.

Keep us posted on any updates :guitar:

---

