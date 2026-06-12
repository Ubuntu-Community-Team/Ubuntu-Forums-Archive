---
title: "Chkdsk/fsck a Win XP from Ubuntu 13.04"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by zemega on 2013-05-02
Hi, I would like to do some diskchecking and defragmentation of a Windows XP partition using Ubuntu 13.04. Is this advisable? The harddisk is from 2005 something, so its pretty old and slow now. I read something about running fsck on the next reboot. The situation now is that I'm going to run Ubuntu 13.04 (full installation) from a thumbdrive. So, I might run into some trouble with the rebooting part.

---

### Post by Cheesemill on 2013-05-02
Ubuntu doesn't have any software that can fix problems with NTFS drives, you need to boot Windows and use its tools instead.

---

### Post by zemega on 2013-05-02
Well, that's that then. Nothing much can be done about it then.

---

### Post by Cheesemill on 2013-05-02
If your XP isn't booting then try plugging the drive into a different Windows machine to run chkdsk on it.

Or you could boot your current machine from your XP recovery disks, this will let you run chkdsk.

---

### Post by zemega on 2013-05-02
Yeah, I'm planning to do that. I only have laptops, so got to get a SATA to USB converter/casing first.

---

### Post by prodigy_ on 2013-05-02
> **Cheesemill said:**
> Ubuntu doesn't have any software that can fix problems with NTFS drives
Sure it does: **ntfsfix**. While ntfsfix is not a chkdsk, it can and will fix certain errors.

However, you probably want to start with something more fundamental like **smartctl -a** to check if your HDD is physically failing.

Also NTFS is always quite slow under Linux. Moreover, it gets slower over time because file system fragmentation increases. If you no longer use Windows, you should switch from NTFS to something more Linux-friendly (usually **ext4** if it's an internal HDD).

---

### Post by zemega on 2013-05-02
I'm listening. Its someone else laptop, and its aging, I'm just doing what I can to prolong the life of the laptop until April next year, when the person will either change to Windows 7 or Ubuntu depending on future situation, I mean change to a new laptop as well.

---

### Post by Mark Phelps on 2013-05-02
Regarding ntfsfix -- from their own website:

> ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.

What it basically does is flag the NTFS volume as "dirty" so that when you connect that to a Windows PC, it will automatically run CHKDSK against it.

---

### Post by AndyOpie150 on 2013-05-02
Hirens Boot CD also has some very useful utilities in the mini Windows XP

---

### Post by zemega on 2013-05-02
Thats interesting. I will look at it. Any chance you can install Mini Windows XP inside a laptop, and install some research utility programs in it? Its only until Microsooft axe Windows XP next April anyway.

---

### Post by oldfred on 2013-05-02
I have used a Windows 7 repair flash drive to run chkdsk on a XP partition. It worked better than the XP chkdsk.
But it converted NTFS PBR - partition boot sector from XP (use ntldr to boot) to Vista/7 (use bootmgr to boot) type with bootsec.exe.

I then used Windows 7 repair flash drive to fix PBR.
       Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx]("http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx")


 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

From any Windows 7 system.
      
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
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

