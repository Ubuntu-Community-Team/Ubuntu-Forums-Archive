---
title: "Ubuntu secure remix 12.10 won't boot UEFI"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by linux4life01 on 2012-12-12
Hello! I am trying to install ubuntu on my new Hp 7229 laptop. It has UEFI  and windows 8. I turned secure boot off and set UEFI to boot from DVD, but the laptop just boots into windows 8 without even asking me if I want to boot from DVD. Any help would be great thank you!!. 
The laptop specs are:
AMD A10 2.3ghz quad
8GB ram
ATI 7660g graphics

---

### Post by oldfred on 2012-12-12
Welcome to the forums.

Have you turned off fast boot or quick boot also? Many have issues with that. Also does your system have the Intel SRT or a small SSD to speed up Windows?

Most find booting from USB flash drive installs faster. 
Are you sure you had a good download and burned at slowest speed possible. And is it a bootable disk not just the ISO copied to it?

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
Have you also backed up? Made a Windows recovery and a Vendor recovery set of disks? You always need a way to repair. And you need the repair disk for the current version of every system you have installed.

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07143&cc=us&dlc=en&lc=en&product=5309505](http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07143&cc=us&dlc=en&lc=en&product=5309505)

       Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
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
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
    
       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

            HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

---

### Post by linux4life01 on 2012-12-12
thank you for the fast reply. no my machine does not have a SSD. I have not burned any Backup cd/Dvd's but the machine does come with the HP restore partition. I do know a bit about BIOS, but UEFI is very confusing. also how do I disable windows 8 Fast boot? and after Ubuntu is installed will I be able to re-enable it?

---

### Post by oldfred on 2012-12-12
I am not 100% sure what fast boot is. It seems to be some that skips UEFI boot or causes UEFI just to jump to boot Windows. When installing a second system (even another Windows?) it then may make it very difficult to get back into UEFI menu to change settings. Most seem to suggest just to turn it off.

Not sure if other links to HP computers use an enough similar UEFI to help, hope so. They seemed to get dual boot to work.

---

### Post by pqwoerituytrueiwoq on 2012-12-12
there shuold be a key (F2/F8/Del) to access a boot menu, also there is the boot priority in the bios you can change

---

### Post by linux4life01 on 2012-12-12
I did find a way to disable fast boot. Made sure I was buring the ISO and not just copying to the disk. Set boot priority to Cd/DVD drive. And it still boot windows only. No boot from cd option ever appears.

---

### Post by oldfred on 2012-12-12
With UEFI you have to go into UEFI and choose the boot device from a UEFI menu. Not sure if they still have the one time boot key like I have with BIOS (f12) that lets you just this once boot some other device.

Most now use flash drives as it installs quicker and then is reusable for something else.

Someone post this from their system. But every brand is different.

---

### Post by linux4life01 on 2012-12-13
I changed the boot prioirty with F10, from the looks of the image you posted that would be the way to allow legacy mode. Or BIOS emulator I can't do that because I would like to have a dual boot system.

---

### Post by oldfred on 2012-12-13
Some of the UEFI are very confusing or maybe all are.

There is a secure boot setting. 

There are settings to allow legacy boot meaning BIOS. Some call it legacy, AHCI, or just BIOS.

Some require a setting to allow UEFI boot which really means you can boot without secure boot but not legacy boot. And some seem to make setting sound opposite of what it should mean.

---

### Post by linux4life01 on 2012-12-13
I purchased a USB drive and was able to install Via USB. I am unsure if I should mark this as solved since DVD install does not work. If it should be marked as solved please let me know. Thanks for your help in this matter. I will continue to research this matter.

---

