---
title: "Running Live from 32GB Mem Stick"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by oserdavid on 2011-10-26
I'm running Oneiric i386 live from a large memory stick. Not mission critical. Rather than having a 4Gb persistence file within a 10Gb FAT32 partition I've got an ext3 partition on the remainder of the stick labelled 'casper-rw'. Works just fine - sorta. (I've even managed to install MSOffice 2000 - just for fun, using Wine. And that works too - although it is very fussy about what Office 2000 updates it takes).

However, problems occur when it comes to updating Ubuntu. Security updates (I think) take just fine. But 'Recommended' updates (or some of them) seem to break the Software Center - in particular - when it comes to updating the Software Catalog - they don't seem to be able to find a place to do that. And afterwards - bye, bye working Software Center. 'Completely' Uninstalling Software Center and reinstalling via Synaptic (yikes - thank goodness Ubuntu Desktop does reinstall because you cannot remove Software Center without removing Ubuntu Desktop, too)doesn't help at all.

This is no really big pain - because I have Synaptic installed, and that still seems to work well.

But I'm wondering if I am encountering an Oneiric bug - which I don't seem to be able to find - or it is just that I'm running a live version and certain elements are retained as unwritable on the FAT32 partition - in particular, the Software Catalog for Software Center? And, if so, is there any way round this? I mess about - but I'm really quite Linux-ignorant.
David

---

### Post by oldfred on 2011-10-26
The liveCD/USB with persistence is for testing. With a 32GB drive you should just do a full install. I installed Maverick to an 8GB partition and left 8GB for data on a 16GB flash drive. It really is just like any install to a second drive, except you make a few settings to reduce writes for improved (not great) speed. Should be better than liveUSB as with persistence you are reinstalling to the fixed Ubuntu install every time you use the persistence. Persistence is really just for your files while you test the live system.

Just be sure to install the grub2 boot loader to the MBR of the flash drive.

Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by oserdavid on 2011-10-26
Many thanks oldfred - I will explore these links. I was put off installing to my usb stick because of warnings (Unetbootin site) to 'disconnect' my laptop drives, to ensure that the installation, or part, did not go onto them. Disconnecting laptop drives is no easy matter. I wasn't sure how seriously to take the warning, but having accidentally installed Ubuntu to a drive I didn't intend to once before, a few years ago, I did not want to risk it again. Your advice to 'ensure to install the grub2 boot loader to the MBR of the flash drive' just makes me more anxious.... But we'll see

---

### Post by oldfred on 2011-10-26
It is just important to use manual install or Something Else or whatever they call it now, so you get the choice of where to install the boot loader. Otherwise it defaults to sda which is usually the internal drive.

You can easily repair boot loaders, but have to have a repair CD or USB. I suggest a repairCD or liveCD for every system you have installed. I actually install a bunch of ISOs directly on my flash drive and use grub to boot them. I even managed to get grub2 to boot a Windows repairCD so I could include other repair ISOs on same flash drive.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by oserdavid on 2011-10-27
That's very helpful oldfred. I have repaired my Windows bootloader before after I uninstalled the (malplaced) Ubuntu I had previously installed, though having only done that once I'd need to refresh my learning about how to do it. 
When I have the spare time to recover from any 'accidents' I'll have a go at doing a proper install on my usb stick.

---

