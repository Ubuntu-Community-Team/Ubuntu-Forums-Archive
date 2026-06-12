---
title: "Windows 10 won't boot after installing Ubuntu alongside and doing boot repair"
date: 2016-08-04
forum: New to Ubuntu
---

### Post by mevans4 on 2016-08-04
I installed Ubuntu from a USB and selected to install it alongside Windows 10, which was already on my computer. Ubuntu boots fine but I cannot boot to Windows - it kept giving me an error that says to search online for "INACCESSIBLE_BOOT_DEVICE"
I have read several other threads about similar issues to no avail, so I hope having someone read through the pastebin link below will help me. Wondering if I'll need to reinstall Windows 10...

Boot info summary: [http://paste2.org/WnjZgaPt](http://paste2.org/WnjZgaPt)

Thank you for any help/advice you can offer!

---

### Post by oldfred on 2016-08-04
You have the newer NMVe drive. But I think your system looks normal. But Boot-Repair does not correctly show the new drives, so not all info there like normal.

Can you directly boot Windows from UEFI, not grub? UEFI boot menu is usually directly accessible with a one time boot key like f10 or f12. But if you let fast boot on in UEFI you may have trouble getting to it.

It also looks like you have Secure boot on in UEFI. Often better to turn that off. Grub will not boot Windows with it on. If you want it on, then you must boot from UEFI boot menu.

Or you may have Windows fast start up on. That is always on hibernation which prevents Linux NTFS driver from mounting and seeing that you have a Windows install.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

If you are getting grub menu as it is not even shown in report, the last line in grub is direct access to UEFI. 

```
 menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {

 fwsetup 
 }

```

---

### Post by Mark Phelps on 2016-08-06
You said "alongside" -- which means you used the Installer to shrink the Windows partitions to make room.

In the past, that has often resulted in corruption to the Windows filesystem, which will prevent it from booting -- making it really hard to fix.

---

### Post by mevans4 on 2016-08-08
Hi oldfred,

I disabled secure boot and was able to enter the UEFI boot menu and boot from there to Windows. Everything seems to be fine. Thank you very much for your help!

---

