---
title: "GParted resizing NTFS partition/adding new partiton, GParted appears to be frozen"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by bashhimup on 2013-04-02
I'm on Ubuntu 12.10. I just ran GParted and shrunk my Windows Vista (NTFS) partition, and added a new ext4 partition, so I can install Arch Linux. A couple of minutes later, only the desktop background is on the screen, and GParted appears to be frozen. It's been more than half an hour. Is this normal? Thanks.

---

### Post by ManamiVixen on 2013-04-02
Gparted cannot handle NTFS properly, you have to use windows to resize it. There is a possibility now that you wreaked the Hard Drive.

---

### Post by bashhimup on 2013-04-02
> **ManamiVixen said:**
> Gparted cannot handle NTFS properly, you have to use windows to resize it. There is a possibility now that you wreaked the Hard Drive.
Oh.. God. This isn't good.

---

### Post by bashhimup on 2013-04-02
Did I really mess up the hard drive? I am so scared right now. So scared.

---

### Post by ManamiVixen on 2013-04-02
No, it will still work, but you may have lost windows and possibly the master boot record. Reboot to see what happens. It might still work, but hours isn't common for a resize.

Otherwise, reinstalling Windows and Linux is still possible with the drive.

---

### Post by bashhimup on 2013-04-02
Ah, okay. I might wait a little bit more, and then I'll reboot. Hopefully it will.

I really hope I didn't lose Windows.

---

### Post by ManamiVixen on 2013-04-02
If there are issues, there is a FAQ from GParted that can help if issues arise. 

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by bashhimup on 2013-04-02
Thanks for the link.

---

### Post by oldfred on 2013-04-02
Do not force shutdown. Remember the elephants if using any Linux.
 Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)



Often it needs chkdsk. But you need a Windows repairCD or flash drive to run chkdsk. You cannot run chkdsk from Linux.

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I have used a Windows 7 repair flash to run chkdsk on my XP, it actually worked better for chkdsk, but caused other issues and I had to repair PBR - partition boot sector as it converted it from XP to Vista/7. 
But if repairCD/Flash is not exactly same version you will not be able to run auto repairs and you may not be able to do much beyond chkdsk.

---

### Post by bashhimup on 2013-04-02
> **oldfred said:**
> Do not force shutdown. Remember the elephants if using any Linux.
 Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)



Often it needs chkdsk. But you need a Windows repairCD or flash drive to run chkdsk. You cannot run chkdsk from Linux.

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I have used a Windows 7 repair flash to run chkdsk on my XP, it actually worked better for chkdsk, but caused other issues and I had to repair PBR - partition boot sector as it converted it from XP to Vista/7. 
But if repairCD/Flash is not exactly same version you will not be able to run auto repairs and you may not be able to do much beyond chkdsk.

Oh, sorry. I force shutdown. Vista automatically ran chkdisk when I booted in to it, and it works fine. Man, am I lucky. Thanks for the advice, though! :)

---

### Post by ManamiVixen on 2013-04-02
bashhimup, sorry to scare you so much. I was just putting out there what likely happened. Cause you know something bad happens when the desktop goes missing and locks up.

---

### Post by bashhimup on 2013-04-02
> **ManamiVixen said:**
> bashhimup, sorry to scare you so much. I was just putting out there what likely happened. Cause you know something bad happens when the desktop goes missing and locks up.
It's okay. Thanks for the help! :)

---

