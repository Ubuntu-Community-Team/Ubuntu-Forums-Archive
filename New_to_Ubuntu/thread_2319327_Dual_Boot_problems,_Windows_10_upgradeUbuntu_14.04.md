---
title: "Dual Boot problems, Windows 10 upgrade/Ubuntu 14.04"
date: 2016-04-03
forum: New to Ubuntu
---

### Post by Andrew F in Australia on 2016-04-03
Hi all,

Have successfully run a laptop on dual boot for a number of years.   Windows 7/Ubuntu 14.04 was seamless.

Upgraded from Windows 7 to Windows 10 (need it for work software that won't run inside WINE)

Now, whenever I shut down Windows 10, it brings up errors with drives still being needed by Windows 10 on Ubuntu startup.

I need to manually run boot-repair in Ubuntu to fix the error, then reboot into windows, shut down again, and then boot Ubuntu to get things working successfully.  Next time I go into Windows 10, same problem occurs.

Pastebin of error here:
[http://paste.ubuntu.com/15596538/](http://paste.ubuntu.com/15596538/)

Pastebin of error repair here:
[http://paste.ubuntu.com/15596582/](http://paste.ubuntu.com/15596582/)

Can anyone shed light on how to fix this problem?

With many thanks in advance.

Andrew F

---

### Post by yancek on 2016-04-03
> Now, whenever I shut down Windows 10, it brings up errors with drives still being needed by Windows 10 on Ubuntu startup.

What?  If you are booting Ubuntu, you do not need anything on windows.  If you look at the boot repair output under the section Additional Information the problem is spelled out specifically.  Windows is in an unsafe state, you have windows hibernated and I am not aware of any Linux system that will mount a hibernated ntfs partition.  If you want to access a windows partition from Ubuntu, turn off the default hibernation, fast boot, etc or you will continue to have this problem.  Windows 8 and later use hibernation by default.

---

### Post by oldfred on 2016-04-03
Boot-Repair cannot fix most Windows issues.
If you need Windows repairs then you need your Windows repair flash drive.

       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---

### Post by Andrew F in Australia on 2016-04-03
Thanks Fred and Yancek (yannubuntu?)

Yes, I was aware that boot-repair only fixed the Grub menu.  It did let me boot back in each time.

The problem was indeed the 'fast startup' you both mentioned.  Disabled that and dual-boot works perfectly.

With many thanks and best regards,

Andrew F

---

