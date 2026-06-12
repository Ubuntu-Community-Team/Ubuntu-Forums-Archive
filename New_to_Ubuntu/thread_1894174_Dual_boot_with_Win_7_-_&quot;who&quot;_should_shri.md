---
title: "Dual boot with Win 7 - &quot;who&quot; should shrink partition?"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by anewguy on 2011-12-11
On my laptop I run Win 7 with ubuntu 11.10 in a VM.  This weekend I decided to upgrade my desktop from XP to Win 7.  I also decided I would just blow away my ubuntu install since I was having problems with flash nobody could help with so I wanted to try 1 more clean install.  So, I did like I would have if I was starting with XP:  used the entire disk for Win 7.

I was ready to install ubuntu for dual-boot when a question came to mind, and it's 1 I'd prefer an answer for rather than find out the hard way, because I don't know how forgiving Microsoft is on re-installs on Win 7.

Do I let ubuntu reduce the size of my Win 7 install just as I would for XP, or is there another tool I have to use instead?  I'd like to make sure my Win 7 install still boots when I'm done ;)

Thanks in advance!
Dave ;)

---

### Post by oldfred on 2011-12-12
With Windows 7 you want to use its partition tools to shrink its own partition, do not create new partitions as it may convert to dynamic from basic and create all sorts of major problems. Reboot into Windows so it can run chkdsk and make whatever repairs it wants to make on the partition resize. The PBR - partition boot sector has internal data that has to match its new size & chkdsk usually fixes that. A defrag before shrinking may help, even on a new install.

Then you can use gparted to create new partitions in the free space.

Always good to have a liveCD or repair CD of the current version of every system installed, but I have used my Windows 7 repair USB to run chkdsk on  XP:

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by anewguy on 2011-12-12
Thanks Oldfred - it's exactly what I needed!


EDIT:  Worked great!  I was trying to remember what I had read on the forum about partitioning with Windows 7, so I sure am glad you knew all this!!

Thanks again!

END-EDIT

Thanks!

Dave ;)

---

### Post by daemondign on 2011-12-12
Definitely use Windows tools!!

---

