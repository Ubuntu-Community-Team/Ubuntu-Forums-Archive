---
title: "Windows 8 / Ubuntu dual boot fun times!"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by matt57 on 2014-02-08
Hello,

I'm having a world of problems trying to get my Windows 8/Ubuntu dual boot working.

So, I installed Ubuntu on my existing Windows 8 system. Things worked fine, i.e. I could boot into both systems, although only through the GRUB interface. I tried to make the nice windows 8 type boot interface chooser work, but ended up somehow ?removing? my windows 8 boot options altogether.

[B]I can boot into Ubuntu no problem. I have tried a number of things after reading numerous other posts. I have just run boot-repair, but this hasn't solved the problem. Here is the link to the Pastebin text file:

[http://paste.ubuntu.com/6897414/](http://paste.ubuntu.com/6897414/)[/B]


Hope someone can help?? 

Thanks for you time chaps

Cheers
Matt

---

### Post by oldfred on 2014-02-08
Boot-Repair shows several thing.

Boot-Repair suggests the 'buggy' repair too often. Can you boot ubuntu entry from UEFI? The buggy repair is only for those systems that only boot the Windows entry from UEFI menu. Then you actually boot to grub from Windows entry.

better to always say no, until confirmed that after all fixes only Windows boots.
 buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes 
If you can boot the ubuntu entry in UEFI undo the backup & rename.
Boot000B* ubuntu	HD(2,fa800,fa000,a3fd87cd-7ab6-11e3-bee6-84a6c8471a16)File(EFIubuntugrubx64.efi)
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.
    
But it looks like you did not turn off the fast boot or always on hibernation.

 The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume

It also looks like UEFI removed Windows entry from its menu which is very unusual. But you have to fix hibernation issue and readd the Windows entry. UEFI should do that automatically as Microsoft files are in efi partition.

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

---

### Post by matt57 on 2014-02-08
Thanks for your reply oldfred, it is much appreciated.

I ran boot-repair again, this time selecting no for the 'buggy' repair question and also ticking the [COLOR=#000000]"Restore EFI backups" option of Boot-Repair. Here is the Pastebin
[/COLOR]
**[http://paste.ubuntu.com/6898023/](http://paste.ubuntu.com/6898023/)**

[B]In UEFI: There are only two boot options:
1. ubuntu
2. network boot.
[/B]
(before I ran boot-repair there was only network boot, i.e. no option for USB etc WEIRD!!?).


If I let the laptop boot up on its own, now it goes straight to the windows boot manager black screen saying "Windows failed to start A recent hardware or software change etc..."

I can choose ubuntu on the UEFI and get to grub and boot into ubuntu as before.


I wasn't sure from your post what you were telling me to do next?? Any help would be greatly appreciated.

Cheers
Matt

---

### Post by oldfred on 2014-02-08
You now are into Windows repair.

Since it shows the Microsoft directory with the boot files, I thought at least the UEFI would auto add them back into UEFI menu. We can manually add them with efibootmgr, if necessary, but fixing Windows will probably solve it first.

Grub can only boot working Windows so you are into Windows repairs which I only know a little about. Links above were about some repairs.
 [http://www.eightforums.com/](http://www.eightforums.com/)


Not sure why boot entries show recovery for boot of both sda1 & sda2. The sda1 looks like a Microsoft recovery/repair, but sda2 is the standard efi for normal boot. Often there is another vendor recovery so you can reinstall Windows but I do not see one.
Does the grub menu list for sda1 get you to a Windows repair?

You should have a Windows repair flash drive, but if you did not make one, you may is you know anyone else at work or school with Windows 8.
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by matt57 on 2014-02-10
Hi oldfred,

Thank you for your help. There seemed to be a lot of bizarre things going on, so I decided to completely wipe and reinstall Windows and then Ubuntu again.

Dual boot is working nicely now! Hoorah! Thanks again for your efforts

Cheers
Matt

---

