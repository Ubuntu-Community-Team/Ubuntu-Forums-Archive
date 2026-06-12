---
title: "Ntfsfix"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by mysweetgrace on 2013-02-03
I have a question about the ntfsfix command.  

I am using a live USB install of Ubuntu (the latest download) to try and get to files on a Windows HD that will not boot.  I cannot get into Windows through safe mode, nor the repair disc or startup repair.  The drive would not mount, and I suspect that Windows is severely corrupted.  

I tried the ntfsfix command and got a result similar to this:

ntfsfix /dev/sdg1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdg1 was processed successfully.

However, I can no longer even see the drive.  While the drive was visible before, listed "Gateway" in the side panel, now nothing is there.  Tried booting into Windows again unsuccessfully.  

Where is my drive? How do I go about locating it since I cannot see it?  It was my understanding that ntfsfix would attempt to fix the corrupted files so that Windows could boot normally.  

Thanks for any help, from a very inexperienced Ubuntu user.  :(

---

### Post by Mark Phelps on 2013-02-04
NTFSFix is only able to fix the most trivial of NTFS problems.  IT's not a substitute for CHKDSK.  You need to hook up the drive to a Windows PC and attempt to run CHKDSK on it.

---

### Post by oldfred on 2013-02-04
NTFSfix also sets the chkdsk flag, you when you reboot Windows it will run chkdsk. 
But the NTFS driver does not mount drives with the chkdsk flag set to prevent further damage that then chkdsk may not be able to fix.

You can use a Windows repairCD or flash drive to fix.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

            Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You can use any Windows repairCD to run chkdsk, but maybe not other repairs.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

