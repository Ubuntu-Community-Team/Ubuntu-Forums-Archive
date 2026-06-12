---
title: "When installing Ubuntu, it does not recognize that Win 8.1 is already installed"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by doco2 on 2014-04-21
I purchased a new Acer Laptop, with Windows 8.1 on it. I would like to now install Ubuntu 14.04.
Until I get confident with Linux I would prefer to keep Windows on my computer and install Ubuntu as Dual Boot.

During the Installation Process, Ubuntu tells me that it did not recognize any other operating system and suggests to use the entire disk for Ubuntu.
What could I do that Ubuntu is recognizing Windows and installs alongside it?

doco

---

### Post by kc1di on 2014-04-21
Here is[ a page]("http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html") that will explain what you need to do.

there are others on the web that describe how to do it also.

---

### Post by WoodenWalker on 2014-04-21
I would follow most of that article, however, do not switch your boot options to "Secure Boot=off" and do not change from UEFI boot to legacy. The newest Ubuntu releases support both secure and UEFI boot. However, Win8 may not want to boot if you change those settings. Just a word of warning. And definitely backup your system prior to attempting this.

---

### Post by oldfred on 2014-04-22
Best to make good backup of Windows and the efi partition and also make a Windows 8 repair flash drive. You should do these even if not installing another system.

Make sure fast boot or the always on hibernation is off in Windows. Ubuntu cannot see NTFS partitions with the hibernation flag or chkdsk flag set.
Best to use Windows own partition tools to shrink the Windows NTFS partition to make space for Ubuntu. And reboot immediately into Windows as it does need to run chkdsk or make other repairs. Double check that fast boot is still off as Windows keeps auto reseting to its defaults on any maintenance or updates.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by doco2 on 2014-04-22
Many thanks for your help so far, but I think I will give up.

When reading all this, then I am really getting discouraged. Although I created a back-up (using the software Acer delivered), I have the feeling that there is a high chance to destroy my computer and I am not really sure if I know how to use this back-up to restore everything (I miss the good old times when you enter a CD and click on install, without caring about uefi).

Although I am not really happy with Windows, I think it is better for me to keep it, as it simply works fine and I really don't want to spend hours and hours to work around something that I don't really understand and where the outcome is questionable.

---

### Post by oldfred on 2014-04-22
You are not the only one, but it is another success story for Microsoft. 
Make it so difficult to install anything else that users will continue to use Windows. 
And Windows is 'good' enough for many users.

---

