---
title: "Partitioned drive: trouble between Ubuntu 8.04 &amp; Windows XP"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Photonaut on 2008-06-06
partitioned laptop drive & did an alternate 8.04 install, all went well for a couple of days. Accessed a lot of files in "My Docs" in Windows XP partition, created shortcuts (launchers?) for them on Ubuntu desktop. Suddenly, booting up into Ubuntu, desktop shortcuts all "crossed out"; launchers on the task bar & wallpaper disappeared.

Have been told it sounds like the Windows partition has been unmounted - Linux refuses to load NTFS partitions if they're "dirty" in case it damages them. 

How to fix this??

---

### Post by _sphinx_ on 2008-06-06
I guess you didn't have clean shutdown of Windows. And also this problem can occur if you have hibernated the windows.

---

### Post by Paqman on 2008-06-06
> **Photonaut said:**
> 
How to fix this??

Boot into Windows and shutdown. Boot into Ubuntu and you should be good to go.

---

### Post by Photonaut on 2008-06-06
Have rebooted both XP & Ubuntu several times, no change at all in status.

---

### Post by Duck2006 on 2008-06-06
Did you boot in to win xp, and boot out of it, then boot in to ubuntu and see if it will mount your ntfs partition?

Some info on mounting ntfs partitions.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

