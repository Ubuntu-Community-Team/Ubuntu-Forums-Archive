---
title: "Formatted Dell Factory Reset partition as swap partition"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by vandanaj on 2013-02-12
Hi,

Today I received my new dell laptop. While trying to install ubuntu I disabled UFEI and by mistake formatted Dell Factory Reset partition as swap partition. Unfortunately that too before making any backup of Dell Factory Reset partition. I just started ubuntu once and again logged in to windows when I realized mistake. Can I recover partition in any way? I just started and shut down ubuntu. Is there any chance that swap partition was used and changes were made to Dell Factory Reset partition in unrecoverable way?

---

### Post by diablo75 on 2013-02-12
That partition is screwed, however, since your laptop is likely new enough to still be covered under warranty you can request a free set of reinstall discs from Dell here:

[http://support.dell.com/support/topics/global.aspx/support/dellcare/en/backupcd_form?c=us&cs=19&l=en&s=dhs&redirect=1&DoNotRedirect=y](http://support.dell.com/support/topics/global.aspx/support/dellcare/en/backupcd_form?c=us&cs=19&l=en&s=dhs&redirect=1&DoNotRedirect=y)

You'll fill out the request form at the bottom and wait for a representative to email you.  If you've already registered your system with them they'll probably have no questions for you and mail the discs outright.  If it's out of warranty you'll still be offered the option to purchase replacement discs for about $18 I think.  You probably don't need them right now but it's best to have a set on hand in case you ever do, especially if they're free.

---

### Post by aka-John99 on 2013-02-12
Another thought is that Windows lets you create sytem backup disks on to CDs or DVDs, so as long as the Laptop has an internal drive you could create your own system image.

See [http://windows.microsoft.com/is-IS/windows7/Back-up-and-restore-frequently-asked-questions](http://windows.microsoft.com/is-IS/windows7/Back-up-and-restore-frequently-asked-questions)
>                                        Windows Backup provides you with the ability to create a system image, which is an exact image of a drive. A system image includes Windows  and your system settings, programs, and files. You can use a system  image to restore the contents of your computer if your hard drive or  computer ever stops working. ....

---

### Post by oldfred on 2013-02-13
If you have a lot of RAM, swap may not have been used. But most liveCD's do use swap when booting to speed things up. You may be able to change the partition back from swap to NTFS, but I am not sure if I would trust the recovery. And you have to find a liveCD version that does not mount swap. Ubuntu's installer automounts swap.

Best to order DVD set.

But the DVD recovery is really only useful if you want to restore to as purchased. Maybe if you sell computer several years from now.  Better to have a full backup of Windows (and efi partition).

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
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

