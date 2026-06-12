---
title: "ubuntu on lenovo y500"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by bisharat on 2013-06-30
hello, i just bought my lenovo y500 and although i was a user of ubuntu a few years back, right now because of windows 8's arrival, im kinda lost on how to install ubuntu with windows 8. i used to do it with wubi, but now i read that windows 8 has a new EFI system which prevents booting up from usb.  I dont wanna lose windows 8 now! I've just booted up from a liveusb and I clicked on Install Ubuntu 13.04 and i saw Install alongside Windows 8. But right now Im a bit hesitant. My question are
1) By continuing this, will i be able to remove ubuntu in the future from Windows 8 Programs and Features?
2) Will any of my windows 8 files be affected?
3) Will there be any bootloader problems? previously with windows 7, windows 7 bootloader used to take over....

PLS DO REPLY ASAP. Thanks!!!!

---

### Post by oldfred on 2013-06-30
Make a Windows repair flash drive and a full backup of Windows and the efi partition. You can use Windows own tools or third party backup tools.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

      
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Only use Windows Disk tools to shrink the Windows NTFS partition and reboot so it can run chkdsk and make repairs due to its new size.
Turn off Secure boot and fast boot.
Does your Windows still boot with Secure boot off. Some do and others do not.

      
 Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

---

