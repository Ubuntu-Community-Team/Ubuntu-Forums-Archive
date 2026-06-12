---
title: "Installation seems broken..."
date: 2008-11-01
forum: New to Ubuntu
---

### Post by gemmala on 2008-11-01
Hi,

A while ago my Ubuntu installation went wrong (posted [http://ubuntuforums.org/showthread.php?t=921814](http://ubuntuforums.org/showthread.php?t=921814)). After a while I gave up, used partition editor in Windows to remove the Ubuntu partition completely. This had the result of screwing up Grub, but I had created an 8.04 bootable CD and was able to reinstall Ubuntu, which gave me a working Grub that was able to access Windows and Ubuntu.

But then I didn't boot Ubuntu for a while, and now when I do the problem has returned - it boots normally, I enter my username and password, but then I'm left with a blank desktop. It recognises if I have flash memory plugged in, or a CD in the drive, but no toolbars appear, leaving me with rather limited functionality! Right-clicking gives me the usual options to create a new file, new folder etc, which I can do (and then open).

The options available from Grub are:

Ubuntu 8.04.1, kernel 2.6.24-21-generic
Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86+
Windows XP

I can still boot into Windows fine, I've run the memtest and it tells me nothing is wrong, similarly I'm not told of anything when I run recovery modes.

Any advice? If this is going to happen every month or so with Ubuntu I can see myself getting rather tired of it....

---

### Post by bumanie on 2008-11-01
Try > sudo apt-get install ubuntu-desktop from console mode, which it sounds as though you are in. Then hit crtl-alt-F7 or reboot and see if it helps.

---

### Post by gemmala on 2008-11-01
Where can I type that in? There's no console that I can see - just the desktop picture. After logging in my screen looks like this (with the addition of a pointer) [http://blogs.technet.com/blogfiles/seanearp/WindowsLiveWriter/InstallingUb.04HardyHeroninVirtualPC2007_129D5/hardy_heron_thumb.jpg](http://blogs.technet.com/blogfiles/seanearp/WindowsLiveWriter/InstallingUb.04HardyHeroninVirtualPC2007_129D5/hardy_heron_thumb.jpg)

---

### Post by gemmala on 2008-11-13
Any further ideas on this? If my installation keeps breaking like this I'm going to have to just get rid of it - no use having an Ubuntu that I need to reinstall every month or so!

---

### Post by bumanie on 2008-11-13
have you tried booting into recovery mode? Otherwise crtl-alt-F1 then type > sudo apt-get install ubuntu-desktopYou will be asked for password etc. Wait for download to finish and then try ctrl-alt-F7 and see if the desktop has returned.

---

