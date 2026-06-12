---
title: "Can't boot, no partition, grub rescue"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by Jarema on 2014-07-26
Hi all,

I really hope that someone will be able to help me.

I had dual boot on my Asus U36SD - Windows 8.1 and Ubuntu 14. I didn't like Ubuntu so I wanted to delete it. Now what I did is:

I deleted the partitions of Ubuntu, I had Free Space (about 80gb), I wanted to extend main partition. Computer restarted and it doesn't work anymore... I can only see the screen saying:
 
error: no such partition
Entering rescue mode...
grub rescue>

I am able to access BIOS (the laptop had preinstalled Windows 7, but I had Windows 8). What can I do with that now? I can lose all the data,  I just want to use my computer. With Windows, no Ubuntu. 

I will just add that I cannot access Windows recovery too. 

I would really apprecite any help, becuse I'm beginning to be really scared.

---

### Post by kansasnoob on 2014-07-26
You could try Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You didn't mention what version of Ubuntu you have ................ I assume you have a Trusty Live DVD/USB :confused:

---

### Post by kira-yamato-2008 on 2014-07-26
He said Ubuntu 14 in his post so Ubuntu 14.04 or 14.04.1 most likely I'd guess.

---

### Post by Jarema on 2014-07-26
It was Ubuntu 14.04 LTS. I don't have live USB, but I can create one as soon as I have access to the computer.

---

### Post by kira-yamato-2008 on 2014-07-26
Did you install from a DVD?

---

### Post by Jarema on 2014-07-26
No, from USB. My computer has no CD rom.

I'm just going to my friend to create a bootable USB with Ubuntu. Do you think that it will start?

---

### Post by ajgreeny on 2014-07-26
It doesn't matter which ubuntu it was as it has now gone and the OP does not want it back; all he wants is to boot to Windows which at the moment is not possible as all the configuration files needed for grub were on the ubuntu partition, now non-existent.

Boot-Repair was able to repair the bootloader of earlier versions of windows but I'm not sure about Win8, however it must be worth trying unless you have a DVD for your Windows OS which you can use to repair the bootloader.  Install boot-repair on the live DVD/USB that you will need to get first as you no longer have one, and then run it immediately; do not reboot the live OS as you will then lose boot-repair and have to install it again.

See [http://askubuntu.com/questions/149674/how-to-create-or-recover-windows-bootloader-after-deleting-ubuntu-boot-drive](http://askubuntu.com/questions/149674/how-to-create-or-recover-windows-bootloader-after-deleting-ubuntu-boot-drive)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader#Windows_Vista_or_7_or_8](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader#Windows_Vista_or_7_or_8)
which may also help you get windows back again.

---

### Post by kansasnoob on 2014-07-26
I only thought to mention the version of Ubuntu because Boot Repair is available for older versions of Ubuntu:

[https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)

But the instructions for installing it in Ubuntu currently assume it'll be installed in Trusty (installs Saucy version in Trusty).

I've found that the Recommended Repair works at least 90% of the time:

[https://help.ubuntu.com/community/Boot-Repair#Recommended_repair](https://help.ubuntu.com/community/Boot-Repair#Recommended_repair)

And the instructions for that are self explanatory ;)

---

### Post by Jarema on 2014-08-01
Hi again. I've finally managed to create a live USB. I installed Ubuntu again, so the problem is partly solved. I am able to use Windows, but again I have two systems.

Can you advise me on how to uninstall Ubuntu, recover the Windows boot loader and last but not least, to add the space that Linux is now using from the hard drive to my Windows partitions?

Thank you in advance!

---

### Post by oldfred on 2014-08-01
You did not have to install Ubuntu.
Just install the Windows boot loader to the MBR using Boot-Repair from the Live Installer.
In advanced mode you can choose which operating system and which drive to install boot loader into.

If you can boot Windows create a Windows repairCD or flash drive now. Not sure which set of instructions may be better for a BIOS install of Windows 8.
       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Then you can use Windows to fix Windows if necessary.
      
 [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

---

### Post by yancek on 2014-08-01
> Can you advise me on how to uninstall Ubuntu, recover the Windows boot  loader and last but not least, to add the space that Linux is now using  from the hard drive to my Windows partitions?

The first thing you need to do is to be able to boot windows from the mbr or efi partition.  Don't know which you are using?  Maybe the Boot Repair will work.  Usually the standard method with windows is to use the installation medium.  If you don't have that , it limits your options.  A Recovery CD/DVD could also be used if you have one.  But you need to boot from windows first or you will be in the same situation you were before.  You were booting with Grub and almost all the Grub files were on the Ubuntu partition you deleted so do things in the correct order this time.

---

### Post by yuu2 on 2014-10-19
help...
same problem
i boot usb using cmd

diskpart
list disk
select disk x(usb)
clean
create partition primary
select partition 1
active
format fs=fat32 quick
assign
put setup windows to usb

still cant boot my usb, blank after i choose boot that

---

### Post by oldfred on 2014-10-20
@yuu2
Please do not highjack another's thread with a different issue. Those are all Windows commands and it looks like you are trying to create a USB flash drive with Windows. This is an Ubuntu forum, but some may know enough to help you. But then your thread should be in the Other OS sub-forum.
Maybe better to check with Windows forums.
       [http://www.eightforums.com/](http://www.eightforums.com/)
[URL="http://www.sevenforums.com/"]http://www.sevenforums.com/


[/URL]

---

