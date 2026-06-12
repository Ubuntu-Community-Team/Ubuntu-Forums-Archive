---
title: "Reinstall windows XP"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by srikrishnan on 2008-10-02
Hi All,

I have Dual OS in my computer. Ubuntu and windows xp. Now my windows xp crashed. I want to reinstall it. Is it possible to reinstall windows xp without affecting ubuntu? Please explain me.
Regards,
Srikrishnan

---

### Post by Idefix82 on 2008-10-02
Windows will wipe out your current boot manager and you will not be able to boot the Ubuntu installation anymore. To recover GRUB after that, you can use this guide:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by louieb on 2008-10-02
The short of it is when you reinstall XP it will replace the boot loader **GRUB **with its own boot loader **ntldr**.

The easy fix is after reinstalling XP is to get yourself a [Super Grub Disk.]("http://forjamari.linex.org/projects/supergrub/")
boot to it and let it put  GRUB back as your boot loader.  [IDBS on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by Idefix82 on 2008-10-02
> **louieb said:**
> The short of it is when you reinstall XP it will replace the boot loader **GRUB **with its own boot loader **ntldr**.

The easy fix is after reinstalling XP is to get yourself a [Super Grub Disk.]("http://forjamari.linex.org/projects/supergrub/")
boot to it and let it put  GRUB back as your boot loader.  [IDBS on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

Well, the easiest fix I can think of is not to bother with XP at all :) I remember last time I installed Windows on top of Linux, I hadn't been warned and wasn't on the forums so I ended up spending about two hours restoring grub by following instructions in one rather hackish IT magazine. I have hated Windows ever since :) Much rather spend my time getting an open source OS to work properly than repairing the damage maliciously done by commercial software.

---

### Post by srikrishnan on 2008-10-02
Thanks for your suggestions. I wil try.

Thanks,
Srikrishnan

---

### Post by kansasnoob on 2008-10-02
This guide may also be somewhat helpful:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

And this:

[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by srikrishnan on 2008-11-02
Hi All,

Thanks for your help.

I have downloaded and burned "Super Grub" in a CD and try to create Grub file for Linux after reinstalling my corruped Windows XP.

But, now I got the following screen message and I am not able to get into Ubuntu:

"Booting 'Ubuntu 8.04.1, kernel 2.6.24-21-generic'
root (hd0,6)
File system type unknown, partition type 0x7
Kernel \boot\vmlinuz-2.6-24-21-generic root = UUID=e08acb7-e42c-411f-9a34-e56b995190a5 ro quiet splash
Error 17. Cannot mount selected partition"

Please anybody will help me. restore my Ubuntu linux version.

Regards,
Srikrishnan

---

### Post by bumanie on 2008-11-02
Grub error 17 can usually be fixed by reinstalling grub off a live cd. [Follow this]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by srikrishnan on 2009-01-12
Hi All,

I have tried both the options 1) super Grub Disk and 2) fixing boot loader file by using Live CD. But still, I am not able to get into my Ubuntu version.

But at the starting window it shows the two operating systems. But when I select "Ubuntu". Only the following Error appears:

"Error 17. Cannot mount selected partition"
Press any key to Continue . . .

Is it possible to solve this problem, or I have to reintall Ubuntu. Please anybody would help me?

Regards,
Srikrishnan

---

