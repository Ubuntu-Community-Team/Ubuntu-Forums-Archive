---
title: "Repartitioning a dual boot"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by gopaleen on 2012-10-22
OK, I´ve attached a screenshot of my current system which is a dual boot Windows 7 and Ubuntu 10.04.

I would like to remove the Windows 7 drive. Make a separate partition for my home folder and install Ubuntu 12.04. So that I just have one partition for Ubuntu and a separate partition for my home directory. Any help/advice would be greatly appreciated.

---

### Post by oldfred on 2012-10-22
We get many users who fully convert but then find they still have one application/game they want to run in Windows. Best to make a full backup of Windows.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And backup /home, /etc and a list of installed applications if you have added a lot and want them in your new install.

discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

Also many users seem to have issues with the major changes to 12.04 and even more with 12.10. You could shrink your current sda5 by 10 to 20GB and install 12.04 just as a test. Then if you works ok you can from the liveCD delete everything with gparted and partition how ever you want.

---

### Post by gopaleen on 2012-10-29
Thanks for the advice!

---

