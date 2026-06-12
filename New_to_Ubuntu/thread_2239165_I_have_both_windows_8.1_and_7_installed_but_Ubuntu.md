---
title: "I have both windows 8.1 and 7 installed but Ubuntu cant see them on install"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by Simon_Porter on 2014-08-12
I have tried to install 14.04 and 12.04 and both when it comes to 'something else' I go to install on the free space on the HDD and it says my HDD is empty.  is there a reason for this

---

### Post by oldfred on 2014-08-12
Windows 8 must do something as it is a consistent issue with Windows 8 systems.

Is your system BIOS or UEFI?

 And if BIOS are both Windows installed in primary partitions?
Make sure fast boot is off in Windows 8 as that is always on hibernation and can even cause issues dual booting two Windows. All your boot files with BIOS are in the first install which has the boot flag or is seen as the active partition.

If you created partitions you may have converted to dynamic partitions which does not work with Linux.
Post this from Ubuntu live installer.
sudo parted -l

Generally best then to manually create partitions with gparted and use Something Else to mount & format / (root), swap and optionally /home or NTFS shared data partition.

       WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

---

### Post by Simon_Porter on 2014-08-18
Problem Solved.  I think I had a dynamicly formatted harddrive so I simply formatted it with gparted to msdos and was able to install both windows 8.1 and Ubuntu 14.04 lts

---

