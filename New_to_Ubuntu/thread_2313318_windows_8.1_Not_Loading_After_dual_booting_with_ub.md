---
title: "windows 8.1 Not Loading After dual booting with ubuntu 15.04"
date: 2016-02-11
forum: New to Ubuntu
---

### Post by Vinamer on 2016-02-11
Hi, I am a new ubuntu user. I dual booted my laptop having windows 8.1 with ubuntu 15.04. Now my Windows is not loading. Please help me
The log file is [http://paste.ubuntu.com/15016571/](http://paste.ubuntu.com/15016571/)

---

### Post by oldfred on 2016-02-11
I do not see anything specific.

Did you turn off fast start up in Windows which is really always on hibernation? (And Windows may turn it back on during updates).
Does Windows need chkdsk?

Grub only boots working Windows that is not hibernated nor needs chkdsk. Best to have Windows repairCD or flash drive to make Windows repairs. And alternative is to temporarily install a Windows type boot loader with Boot-Repair and see if you can use f8 to get into internal repair console. Once fixed or settings corrected, use Boot-Repair to restore grub to MBR.

       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold
[/URL]
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold"]
[/URL]

---

### Post by ajgreeny on 2016-02-11
This is not specifically related to your problem but are you aware that 15.04 has very recently gone EOL so has no more updates.  The repos will soon be moved, if not already gone, so you will find it difficult to install any packages and impossible to update any further.

---

