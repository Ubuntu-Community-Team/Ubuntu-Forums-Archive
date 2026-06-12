---
title: "dual boot doesn't work - I tried boot repair (boot repair link is included)"
date: 2019-11-02
forum: New to Ubuntu
---

### Post by konte2 on 2019-11-02
Hello I am pretty new to ubuntu and I have installed ubuntu alongside win10.Ubuntu automatically boots when I open my computer but unfortunately I can't boot my win 10. I tried boot repair with my bootable-usb but it still doesn't work here is the link from boot repair [http://paste.ubuntu.com/p/ZZp7wwDBp8](http://paste.ubuntu.com/p/ZZp7wwDBp8) what can I do?

---

### Post by yancek on 2019-11-02
Your boot repair output shows "Disklabel type: dos" which is a Legacy install using the older MBR rather than UEFI.  You installed Ubuntu using UEFI and I don't believe an EFI install of Linux/Ubuntu will boot a dos install of windows.  Your boot repair output also shows grub boot code in the MBR which I expect is a result of running boot repair.  If your windows is a dos/Legacy install as shown by boot repair, then you need to install Ubuntu in the same manner.  I will say that it is unusual for windows 10 to be non-EFI.  I would suggest you read the Ubuntu doumentation on dual booting with windows 10 at the link below.  It explains the differencds and requrements for a Legacy and an EFI install and how you can tell which you are using on boot.  Read the entire page before trying another install.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-11-02
It looks like Boot-Repair converted install back to BIOS/MBR configuration.
You cannot have Windows in BIOS boot and Ubuntu in UEFI boot on same drive.  Windows in BIOS mode requires boot flag on its boot partition, your sda1. But UEFI requires boot flag on ESP - efi system partition.
Windows requires BIOS boot on MBR partitioned drives. And it requires UEFI boot on gpt partitioned drives.
Ubuntu lets you install in UEFI mode to MBR drives, but probably should not.

You need to use gparted or Windows to move boot flag from ESP to sda1.

Also grub only boots working Windows. And Windows 8 or 10 have fast start up which sets hibernation flag. So when Windows needs chkdsk or is hibernated, you have to directly boot Windows. With UEFI, you can just boot Windows entry in UEFI.
But with BIOS and only one drive you have to temporarily restore a Windows boot loader to MBR, fix Windows, then restore grub to MBR. Best to have boot Windows repair disk or installer with repair console and Ubuntu live installer handy all the time.

Boot-Repair's advanced mode may let you install a Windows type boot loader (syslinux). But if NTFS partition not seen, then only Windows repair disk will work.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

