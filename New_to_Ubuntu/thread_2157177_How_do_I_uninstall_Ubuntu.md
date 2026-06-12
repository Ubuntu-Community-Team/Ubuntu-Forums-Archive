---
title: "How do I uninstall Ubuntu"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by doddie on 2013-06-24
Hi
I previously posted this error message:
[COLOR=#000000]
Error mounting /dev/sda2 at/media/bill/583242D33242B5B2: Command-line `mount -t "ntfs"-o"uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,d mask=0077,fmask=0177""/dev/sda2" "/media/bill/583242D33242B5B2"'exited with non-zero exit status 14: Windows is hibernated, refusedto mount. [/COLOR]
[COLOR=#000000]Failed to mount '/dev/sda2': Operationnot permitted [/COLOR]
[COLOR=#000000]The NTFS partition is in an unsafestate. Please resume and shutdown [/COLOR]
[COLOR=#000000]Windows fully (no hibernation or fastrestarting), or mount the volume [/COLOR]
[COLOR=#000000]read-only with the 'ro' mount option. [/COLOR]
[COLOR=#000000]As far as I can tell Windows is fully shutdown (used " Shutdown /s /t/0").[/COLOR]
I did not receive any useful advice so have decided to remove Ubuntu and start again (maybe!)
I am unable to view the partition on the HD drive either from Widows 8 or Ubuntu. Any ideas on how I should proceed, please?
Windows disk management reports:Disk 0 Basic 232.88GB Online 
System Reserved 350 MB NTFS Healthy (System Active Primary Partition  
(C:) 23254 GB NTFS. Healthy (Boot Page File Crash Dump Primary Partition)
  
   doddie

---

### Post by oldfred on 2013-06-24
Windows will not see Linux formatted partitions.
Windows 8 is always hibernated for fast boot.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

If you just want to uninstall.

 An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

But if re-installing you can use manual or Something Else and choose to put / (root) in the existing ext4 partition. It should auto find swap. If you created a separate /home then also mount that but DO NOT check the format box.
Best with Windows to also have a separate NTFS data partition, but with Windows 8 you have to be careful not to have anything open in even that partition when booting Ubuntu as then it may also be hibernated.

---

### Post by doddie on 2013-06-24
Thanks oldfred
I will read your refs and hopefully decide what to do!

---

