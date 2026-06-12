---
title: "Ubuntu and Windows on different drives"
date: 2020-02-12
forum: New to Ubuntu
---

### Post by thirstywater on 2020-02-12
Hello everyone!

I am extremely new to Ubuntu and other operating systems in general. I was having a hard time understanding a lot of the coding and other answers I've found online to questions similar to the one I have so I was hoping someone would be able to help me in a very dumbed down way. I was able to install Ubuntu on a separate disk than my Windows 10 disk, and I also set it as first in the boot order. I don't know how to edit GRUB files accordingly so that my Windows 10 disk will also show up on the GRUB. I only know that the main problem is that they're on different drives, which causes os-prober not to be able to detect Windows 10.

I ran boot-repair to have a fresh GRUB and came up with this (afterwards, I set GRUB to show the menu instead of hidden, if that isn't already explained in the link below)
[http://paste.ubuntu.com/p/kcVBdgp3G4/](http://paste.ubuntu.com/p/kcVBdgp3G4/)

If anyone can help me in the simplest way possible, or even a convoluted way but explain to me the computer logic and meanings behind it, I'd much appreciate it!

Edit: My Windows 10 is installed on /dev/sdd

---

### Post by mastablasta on 2020-02-12
make sure both OS are installed in same mode. Windows 10 is probably using UEFI, so Ubuntu also has to be installed in UEFI mode and not MBR (legacy).
more here:
[https://forums.linuxmint.com/viewtopic.php?t=213504](https://forums.linuxmint.com/viewtopic.php?t=213504)

---

### Post by oldfred on 2020-02-12
It looks like you did not have them in same boot mode, so os-prober would never find Windows.
But then it looks like you installed/re-installed to have the BIOS boot version which has grub in MBR.

But Boot-Repair puts grub in MBR of every drive. You really only want grub in MBR of Ubuntu drive if using BIOS/MBR configuration. And you  want Windows boot loader in MBR of Windows drive.
You can use Boot-Repair's advanced mode when booted in BIOS mode to add a Windows type boot loader to MBR of sdd your Windows drive.  And make sure Windows boots. If Windows 10 you must also have Windows fast start up off, or os-prober cannot find and Ubuntu will not mount the NTFS partitions as they are hibernated.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

Better to have Windows repair disk to make repairs to Windows. Boot-Repair is primarily for Linux systems.
Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)


Since newer UEFI system and Microsoft has required vendors to install in UEFI mode since Windows 8 released in 2012, you may want to reinstall Windows in UEFI boot mode. You can use Boot-Repair to convert an Ubuntu install from BIOS to UEFI if on gpt partitioned drive, but Windows is very difficult to convert.

---

