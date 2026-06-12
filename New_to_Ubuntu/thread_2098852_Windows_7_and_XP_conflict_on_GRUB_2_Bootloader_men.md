---
title: "Windows 7 and XP conflict on GRUB 2 Bootloader menu."
date: 2012-12-27
forum: New to Ubuntu
---

### Post by Billy1988 on 2012-12-27
Hi all.

I was wondering if anybody could offer me advice on a little dilemma I have?

I have a 500GB HDD and have partitioned it and have the following OS's installed as follows: 400 ish GB for Windows 7 64 Bit, 60GB for Ubuntu 11.10 and 20GB for Windows XP 32 Bit.

XP was the last OS I installed. This somehow wiped out the GRUB 2 Bootloader. 

I managed to re-install GRUB 2 and then edit it through the Terminal, so that it now displays "Windows XP" in the GRUB 2 menu upon bootup. 

Upon bootup the menu illustrates: Ubuntu 11.10, Windows XP and Windows 7 as the 3 available OS's (Windows 7 showing as in partition "SDA1"). XP is installed on partition "SDA5".

The problem is that, whichever Windows I select from the GRUB 2 bootloader menu, XP is the only one to load up. 

Why is this so? And is there anything I can do to get Windows 7 to boot up again?

Many thanks! Bill.

---

### Post by audiomick on 2012-12-27
This can certainly be fixed. It might be as simple as booting into ubuntu and running
```
sudo update-grub
```

If that doesn't do it, go here

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

follow the instructions about boot info and post that here so people can see the state of your system. From there, someone will on doubt be able to help you get things sorted.

---

### Post by oldfred on 2012-12-28
Windows only knows how to boot from one primary NTFS partition. So a second install writes its boot files into the same partition that has the boot flag. 

When you install Windows 7 over XP, Windows 7 will add an entry into its BCD to also boot XP. But XP never new about 7 and cannot add an entry to its boot.ini.

If XP is also a primary partition, you should be able to move boot files for each system to each system. Move boot file to one system and run that systems repairs, then move boot flag to the other system and run repairs. Then the sudo update-grub will find both systems.

If XP is in an extended partition you really only can boot thru Windows 7. I have seen some work arounds if you really want to experiment.

       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

    
Make sure you have both XP and & repairCD or flash drives.
       Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

            Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

