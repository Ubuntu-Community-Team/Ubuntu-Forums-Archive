---
title: "How do I turn Win7 laptop into dual booting win7/Ubuntu?"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by Garnett on 2014-05-13
Hi there,

I have a work laptop with Win7 that I use at home to remote-login to my PC at work.

I'd like to install Ubuntu alongside so that I can choose at boot whether to boot into Win7 or Ubuntu.

I must not screw up the settings in Win7 that allow me to log into the work VPN.

I was thinking of buying a new hard drive to experiment on, just so the work SSD is preserved for emergencies.

I seem to recall that the Ubuntu LiveCD gives an option to "install ubuntu alongside existing OS".

I was thinking of buying a new SSD, copying the content of the old SSD across, checking the new one runs just like the existing one, and then trying to use the "install alongside" option.

Does this sound sensible? Does the "install alongside" option still exist and function without problems?

Thanks for any help.

---

### Post by oldfred on 2014-05-13
Do you have permission from work to do this? Many companies do not allow users to modify system.
And many have locked UEFI/BIOS so you cannot make changes.

Always backup Windows.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
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

If resizing Windows, only use Windows own partition tools to shrink the NTFS partition to make unallocated space. Are all 4 primary partitions used. Most Windows 7 systems do use all 4 and you have to reconfigure to have one available primary partition to be an extended partition which then can have many logical partitions inside it.

But since a company computer better to have an external drive. Not sure that a SSD as an external adds much as USB port is also a bottleneck. Hard drive works in most cases, and flash drives with settings to reduce writes are very functional if not speedy. Especially compared to your Windows in SSD.

      
 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)


 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
      
 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by stalkingwolf on 2014-05-13
I second the advice given. 1 get permission from employer and to cya get it in writing.  Then talk to your IT people at work they may have special instructions for you.

---

### Post by Mark Phelps on 2014-05-13
The "install alongside" option is risky because if it shrinks down the Win7 OS partition to make room, you risk corrupting the Win7 filesystem -- rendering the laptop unbootable.

I've used "company issued" laptops over the years, and without exception, they were locked down so no changes could be made to them.

I would also strongly suggest you get permission BEFORE you try this, as more than one place I worked treated this kind of thing with TERMINATION -- as it was considered a form of "hacking".

---

