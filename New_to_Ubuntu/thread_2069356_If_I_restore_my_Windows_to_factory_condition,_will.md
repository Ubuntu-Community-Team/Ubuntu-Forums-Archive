---
title: "If I restore my Windows to factory condition, will that delete/change Linux partition"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by hanzj on 2012-10-10
Hello,

My computer came with Windows 7 preinstalled. I later installed Linux (yeah!) on  a separate partition. 


If I restore the Windows to how it was when I first got it (back to factory condition), will my Linux partition be deleted or affected in any way?

Thank you.

---

### Post by CharlesA on 2012-10-10
Usually it will wipe out the area Windows is installed and reinstall, so yes, it will probably wipe out anything else on that drive.

Backup first.

---

### Post by oldfred on 2012-10-10
That is an image of the drive as purchased. So yes it will restore to as new, but delete all the changes in Windows and reformat drive to 'like' new. But that will also erase other partitions including Linux.

Someone may know if there is a workaround, but since NTFS partitions have inside them the partition size info, the restore just about has to be to the same size as the original.

When you first repartitioned it would have been good to do an image backup of Windows, then you do not have to redo all of the Windows changes and can restore to the existing smaller partition.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by TheFu on 2012-10-10
Most factory re-installs will repartition the entire HDD as the first step in the restore process. This ensures that any non-MBR hidden Windows rootkits are probably wiped at the same time. Of course, for other OSes, it means they are wiped too.

Check out partimage or clonezilla for a partition-level backup, like CharlesA suggests.

---

### Post by Lars Noodén on 2012-10-10
You might also consider running Windows inside a virtual machine.  They support [snapshots](http://ryantrotz.com/2011/12/virtualbox-snapshots-and-vmis/), so you could take a snapshot of a pristine installation and then roll back to that whenever you want with two clicks.

---

### Post by hanzj on 2012-10-10
Thank you, Lars, TheFu, oldfred, CharlesA, for your input.

---

