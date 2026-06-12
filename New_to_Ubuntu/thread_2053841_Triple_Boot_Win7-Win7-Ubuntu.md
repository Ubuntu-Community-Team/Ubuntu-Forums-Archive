---
title: "Triple Boot Win7-Win7-Ubuntu"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by orion785 on 2012-09-06
Hi to everyone, i'm here because i need a little support to install ubuntu on my laptop.
Actually i have two installation or Windows7:
- one for everyday use (internet, music/video, web design)
- one for music production (it's an optimized version of Win7)
To delete all problem to the second installation, i've install the two copy on hidden partitions. So my everyday copy don't see my music copy. To do so, i use MasterBooter to select what windows version boot up from the hidden partitions.
Now i want to insert a copy of ubuntu 12.04 and make a triple boot.
How i can do it? Can anyone help me?
Actually my hdd have this two partitions:
- Win 7 Everyday (hidden) NTFS 150 gb
- Win 7 Music (hidden) NTFS 85 gb
I think i have to change and make another 2 partitions line this:
- Win7 Everyday (hidden) NTFS 150 Gb
- Win7 Music (hidden) NTFS 50gb
-  Extended Partition 
- - Ubuntu EXT3 30 Gb
- - Ubuntu Swap 4 Gb (i've 4 gb RAM, 4 gb swap it's ok or it's better more?)
It's right?
After do this, how i can setuo grub2 to start the two installation of Windows7???
Thanks to everyone can help me!!!!

---

### Post by Mark Phelps on 2012-09-06
One thing you need to seriously consider BEFORE you start down this path is that, by default, Linux distros make ALL the partitions in your PC not only visible, but also, read/write.

While you CAN change that, there is a LOT of work involved.

If you decide you want to go ahead anyway, before you install Ubuntu, you should use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will allow you to repair the Win7 boot loader -- should you need to do so as part of the Ubuntu dual-boot setup.

---

### Post by oldfred on 2012-09-06
Do not know about your current boot loader and your hidden. But I think that is the same as moving boot flag (active partition in Windows), so each install has all its boot files. Normally a second install of Windows moves its boot files into the first install and cannot be separately booted. Not sure how to switch the hidden with grub2, there used to be a setting in grub legacy, but I have not paid attention with grub2.

Details (Window 7 works the same as Vista):
To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

If that is the case, you can just install Ubuntu and grub2's os-prober will find both installs and give you the option to boot either one. You can download Grub Customizer and change the label so one is called Windows -Music if you want.

Be sure to have good backups and make a Windows repair disk just in case.
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

If resizing one of your Windows partitions use Windows to shrink the Windows partition, but do not create partitions in Windows. It may convert to dynamic which does not work with Linux nor some Windows repair tools.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I like to have a shared NTFS data partition to have any data that I might want in all systems easily available.

---

### Post by orion785 on 2012-09-06
Unfortunately I need that the first windows (and possibly also ubuntu) can not see in any way the "music Windows" to avoid any problem of stability of this particular installation ... Have to work and you have to stop because windows crashes is a bad thing ... Because at the moment my "music windows" is very stable and has never crashed believe that the best choice is to install ubuntu in a virtual machine on the first OS ...
It's not the best but it seems the only opportunity to have all the OS installed without problems ...
Anyway thanks for your support!

---

