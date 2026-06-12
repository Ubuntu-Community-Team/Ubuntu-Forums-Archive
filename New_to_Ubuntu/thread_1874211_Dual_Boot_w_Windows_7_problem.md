---
title: "Dual Boot w/ Windows 7 problem"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by pyropulse on 2011-11-02
I had a Windows 7 64-bit install and decided to get Ubuntu 11.10. When I installed Ubuntu I used the auto partition and gave Ubuntu 80GB.

Now for the problem. When I try and boot Windows 7 it takes two 'tries' to boot. I will make it all the way to the desktop and about 5 seconds in my computer immediately restarts. It goes back to the boot menu, I select Windows 7, and then I get the standard "Windows failed to shut down properly" message. I just start Windows as normal and it successfully boots. It does this every time. As for Ubuntu, it succeeds to boot the first time, every time.

Any help for fixing my Windows 7 boot would be appreciated. I don't know what information you would need to fix it, but just say and I'll get it.

---

### Post by oldfred on 2011-11-02
Are you using Ubuntu to write into the Windows NTFS partition?
Are you hibernating in Windows.?
Have you run chkdsk until there are no errors in Windows?

I would make a Windows repairCD before anything else, if you have not. And of course, backups are always a good idea.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by darkomano on 2011-11-03
My opinion is that when dual booting Windows 7 with Ubuntu the Windows boot environment
(Windows MBR, PBR, bootmanager) should be in control of the booting.
 
Why - Windows is ignoring other OS as well when installing as well as running.
It is better to leave Windows boot environment be in control because repairing is easier than.
 
Ubuntu and Linux in general can be installed on primary and logical partitions - Windows only on primary. Linux can read and write to NTFS - Windows does not recognize ext3,4 partitions.
 
To place Windows boot environment in control and do the startup repairs use the "Repair CD". It should be run several times if errors are reported (up to 3 times with rebooting after each run).
 
Later add a boot entry for booting Ubuntu over Windows boot manager by:
Create "Boot sector" loader - give it as parameter the file "boot.img" from Ubuntu /boot/grub directory. (Copy boot.img to Windows \boot folder or folder of your choice but it should be hidden and protected from normal users)
 
You could use also the "Dual-boot Repair" tool that comes with Visual BCD Editor from [http://boyans.my3gb.com](http://boyans.my3gb.com). It does the writing of MBR, PBR and repairs bootmgr and BCD.
Than do a system files check:
sfc /scannow
To add boot menu entry for Ubuntu - Visual BCD Editor -> Click "Create Boot sector loader" and amend for boot.img.
 
That would be all.

---

