---
title: "Dual boot, getting Windows back"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by zawadleon on 2014-02-22
i installed ubuntu 12.04lts today alongside windows7x64 using divider option.after completetion i found grub & tried to load win7 from grub i pressed enter but grub said no such device.now what to do? i need windows. plz help me its important.

---

### Post by cogier2 on 2014-02-22
Have a look at this advice. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2014-02-22
> using divider option...

Unfortunately, allowing the installer to shrink Win7 sometimes results in Windows filesystem corruption -- which will stop it from booting.

Boot-repair might fix this.  But if it doesn't, you'll have to do repairs to Win7 to get it booting again.

The problem is that now, you can't use Win7 to make a Repair CD; so instead, you have to purchase the ISO image from a website, download it to a PC, burn it to CD, and boot from that --running Startup Repair at least three times.  Link to the website: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by zawadleon on 2014-02-22
i tried to repair windows by cd but nothing happen

---

### Post by oldfred on 2014-02-22
So we can suggest what issue may be we need to see details.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by zawadleon on 2014-02-22
i am very new to linux.so plz guide me step by step.i am not understanding anything what to do

---

### Post by Murasaki_san on 2014-02-22
The step-by-step guide is on the link provided by oldfred and is quite straightforward. But anyway, if you need a "digest" of what's in there: 

1- Boot your computer from the liveCd or liveUSB you used to install Ubuntu. Once the session has started and you are on the desktop, connect to internet.
2- Open the Terminal (Ctrl+Alt+T) and type:
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update [FONT=arial]*(press enter ==> this will make available the package needed in order to run Boot-Repair. Wait until the work is done and you are able to type again)*[/FONT]
sudo apt-get install -y boot-repair && boot-repair [I][FONT=arial](press enter ==> this will install Boot-Repair. Again, wait until is done)

[/FONT][/I][FONT=arial]OK, I think from here you can just follow from step 3 on the help guide ([https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)) : run Boot-Repair, click on **Create a Boot Info summary** button. When the program is done, you are going to be given an URL that you must copy and paste here in this thread. That will give the forum members the information needed to tell you how to fix your problem.
Just be patient, is not as difficult as it seems at first sight ;)[/FONT]

---

### Post by Mark Phelps on 2014-02-22
> **zawadleon said:**
> i tried to repair windows by cd but nothing happen

According to what you said, you only ran it twice.  It needs to be run THREE times to fix boot loader problems.  Twice is not enough.

---

### Post by zawadleon on 2014-02-23
here is the boot info summery

[http://paste.ubuntu.com/6980653/](http://paste.ubuntu.com/6980653/)

---

### Post by oldfred on 2014-02-23
Once you install grub into the NTFS partition Windows will not even reconize it to make repair. Windows has to have its own boot info in the PBR - partition boot sector or sda1.
```
  sda1: ________________________________

       File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 327353304 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos8)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


```

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

You may have actually been booting with the Windows boot loader in the MBR and grub in PBR. A Windows boot loader just jumps to find more boot code in the PBR that has boot flag. That is for Windows. Grub does not use boot flag. And installing grub to a PBR forces it to convert to block lists which is not recommended and often requires updates.

After fixing PBR, you may want to boot Windows to confirm it works. Then use Boot-Repair to install grub to MBR of drive sda  not PBR like sda1. Grub really can only boot working Windows.

Best to also have a Windows repair tool as Boot-Repair only can make minor fixes to Windows. 
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by zawadleon on 2014-02-23
ok, thnx 4 help guys.i hav at last find nothing to do & formatted c drive & setup win7 again :(

---

