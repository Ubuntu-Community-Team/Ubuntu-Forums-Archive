---
title: "Help install ubuntu (dual boot with windows 7)"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by rocktheartsm4l on 2013-03-08
Hi I have been browsing forums and all of the ubuntu menus people are posting are slightly different from what I'm seeing.

Im trying to create the correct partition to go with my 64 bit windows 7.. I got to this point of the install
[IMG]https://mail.google.com/mail/u/0/?ui=2&ik=43d5872307&view=att&th=13d4b7033ebce272&attid=0.1&disp=thd&realattid=1428968156043411456-1&zw[/IMG]

I chose SDA2 and clicked change. This is were all forums say i need to choose a size to free for creating ubuntu partitions. but my menu is different.
[IMG]https://mail.google.com/mail/u/0/?ui=2&ik=43d5872307&view=att&th=13d4b7019e270bd3&attid=0.1&disp=thd&zw[/IMG]

Any advice would be appreciated I don't want to mess up my w7 partitions. Thanks in advance

---

### Post by oldfred on 2013-03-08
You shrink the Windows 7 NTFS partition using Windows 7's Disk tools, but do not create any new partitions as it may convert to dynamic partitions from basic partitions. Dynamic does not work with Linux.

Almost all Windows 7 systems have all 4 primary partitions used, so you have to delete one. 
Make the recovery set of DVDs and a Windows repairCD from its repair console.

Then you have to decide what to delete. Often vendors have a small Windows tools partition which can be copied into Windows or easily backed up. Or you can delete the recovery as you have a full set of DVDs.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

 Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

 Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

