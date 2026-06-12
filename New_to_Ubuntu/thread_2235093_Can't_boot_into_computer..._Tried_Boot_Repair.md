---
title: "Can't boot into computer... Tried Boot Repair"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by Davidson_Poole on 2014-07-18
All of a sudden, after installing some software updates, Ubuntu tells me to restart. I restart, load Ubuntu perfectly, then decide I want to use Windows to play a game. Restart, select Windows partition in Grub. The Toshiba logo comes up, as usual, but it doesn't boot into Windows. The scrolling wheel just keeps turning. I go to BIOS, and try enabling secure boot, to see if I can boot Windows like that. Same problem. Go to BIOS a second time, change the boot type to CSM instead of UEFI, to see if that will help. It comes up as a black screen "Failed to load media". I switch it back to UEFI and disable Secure Boot. Now all of a sudden, Grub doesn't come up, it just goes straight to loading Windows, but same problem. I ran Boot Repair from a live USB, didn't work. 

Here's my Boot Info: [http://paste.ubuntu.com/7816891/](http://paste.ubuntu.com/7816891/)

I have a Toshiba Satellite.

Thanks.

---

### Post by Bucky Ball on 2014-07-18
At the moment you have Grub installed to the MBR on sdb, which looks like a USB dongle or something else. You want it on sda unless you are going for an exotic setup you haven't mentioned.

Easiest as you can't boot into Ubuntu is to use Boot Repair, click 'Advanced Option', find the 'Install Grub' option and set it to install to /dev/sda. That's it. Reboot and report back. Perhaps something went wrong when you used Boot Repair before because the 'Recommended Repair' option would have put grub there. 

Good luck.

---

### Post by at_first_light on 2014-07-18
According to your paste there seems to be some complaints about your Windows partitions being in an unsafe state. This is could be an indication that fast-startup is enabled in Windows 8. Did you have it disabled before?

I would try leaving the computer running for a while, and then come back later and see if it's managed to load up the welcome screen, or sends you to an error screen.

---

### Post by at_first_light on 2014-07-18
EDIT: I've blanked this comment out as my brain wasn't working when I wrote it, and I can't figure out how to delete it.

---

### Post by Bucky Ball on 2014-07-18
Also, leave in UEFI if that is what you installed in. Changing it can have serious consequences, as it looks like you may have found out.

---

### Post by Davidson_Poole on 2014-07-18
Sorry but how do I change where Grub is installed? I don't see it anywhere in Boot Repair.

---

### Post by Davidson_Poole on 2014-07-18
It has been Normal Startup, not Fast

---

### Post by Bucky Ball on 2014-07-18
'Advanced Options'>Main Options>then Grub Location. 

[https://help.ubuntu.com/community/Boot-Repair#Advanced_options](https://help.ubuntu.com/community/Boot-Repair#Advanced_options)

The first screen there shows the advanced options Main Options. Set yours like that. Then the second screen, Grub Location tab, you should tick 'Place grub into' and set /dev/sda.

---

### Post by Davidson_Poole on 2014-07-18
I don't have all those options. My options are:

OS to boot by default: sdb7 (Ubuntu 14.04 LTS)
Seperate /boot partition: sdb8 [UNCHECKED]
Seperate /boot/efi partition: sdb2  [CHECKED]

---

### Post by Davidson_Poole on 2014-07-18
Ok, now the only item the dropdown menu for "Place Grub into:" gives me is "sdb"

---

### Post by Davidson_Poole on 2014-07-18
Do I have Ubuntu installed in the wrong place?

---

### Post by Bucky Ball on 2014-07-18
> **Davidson_Poole said:**
> Do I have Ubuntu installed in the wrong place?

No. Nothing to do with where it's installed, but you don't. From what I can see, you only have one internal hard drive, unless I'm wrong about sdb, which looks like a dongle or external USB drive or an optical disk.

Strange how there is only an option for sdb. If I am correct, and this is not an internal drive, disconnect whatever it is if you can and try again. You could attempt to 'Force grub to sda1' but at your own risk. I can't see anything untoward happening, but up to you. May just work also. Then maybe not. :-k

---

### Post by Davidson_Poole on 2014-07-18
It doesn't give me the option to force it. Tried boot repair again and same issue.

---

### Post by Bucky Ball on 2014-07-18
My mistake. This is an EFI issue so installing grub to sda is probably not applicable. ;) Just had another look at your bootinfoscript. Considering this, nothing is glaringly wrong, but no expert, although I do wonder what sda3 is. What is that 'unknown filesystem'?

You have this:

> sda2: __________________________________________________________________________

Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
**                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi **
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/OEM/Boot/bootmgfw.efi /EFI/OEM/Boot/bootmgr.efi 
                       /EFI/OEM/Boot/memtest.efi

... and this:

> sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS 
**    Boot files:        /boot/grub/grub.cfg /etc/fstab**

... and that looks normal. I'm wondering about the switch to CSM changing something. What is the state of play with fastboot, secureboot, and make sure you are in UEFI. Don't change that if you installed in that, which it looks like you did.

---

### Post by slooksterpsv on 2014-07-18
If you can get into Ubuntu, download my app in my signature called EFIBootOrder, change the boot order for Windows to be at the top. For some reason, like was stated before, your default boot is 0005 which is a USB 2.0 Flash Device. The boot parameter for Ubuntu is 0000 (odd?).

You said it's a **Toshiba**? Press F12 while the Toshiba logo is showing, select the hdd, and it should popup with what to boot from - Windows or Ubuntu.

---

### Post by Davidson_Poole on 2014-07-18
I changed the boot order to usb first so I can use a Ubuntu live USB, which I'm using now. When I restart I take the USB out.

---

### Post by LostFarmer on 2014-07-18
Grub is installed where it needs to be, in the EFI partition sda2.  You do NOT want it in sda or sda1.

The last time you was in Windows it was not shut down clean, that in it self should not keep it from booting but could cause a long delay in booting.  Boot into Win and wait for 5 min or so to be sure it is not fixing some problems.  When you forced it to shutdown it could have caused errors (scrolling wheel just keeps turning).

Want to verify , after installing linux , you were able to boot into Windows ?  Did you change any NTFS partition size (useing linux) between last time Windows worked and now ?

---

### Post by oldfred on 2014-07-18
Boot Windows directly from UEFI menu. Or as slooksterpsv suggests use f12.

Grub really only boots working Windows and the message in Boot-Repair indicates either fast boot was on or you resized outside Windows and it has to run chkdsk which can take a bit especially if drive is larger.

Also grub has a bug and you currently cannot boot Windows from grub menu if secure boot is on. Make sure that is off in UEFI settings.

---

### Post by Davidson_Poole on 2014-07-18
Yes, I was able to boot into Windows until today. No, I did not change any partition size.

---

### Post by Davidson_Poole on 2014-07-19
Ok, I rebooted, and tried waiting on Windows. 45 min. later, and it was still doing the scrolling wheel thing. Shut down computer, tried the F12 Boot menu, booted into Ubuntu successfully! As for Windows not starting, anyone have an idea on that?

---

### Post by oldfred on 2014-07-19
From f12, not grub boot Windows and see if you can get into repair console.

       f8 to get to repair install screen, I think 8 is similar:
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
 [http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)



 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by Davidson_Poole on 2014-07-19
Tried pressing F8, didn't open anything. Tried about every other key combination I found, none worked. The only way I can get into anything is by pressing F12 and going to Ubuntu.

---

### Post by slooksterpsv on 2014-07-19
Try my efibootorder in my link, I wonder if it has to do with Fastboot now. EFIBootOrder is an app that will allow you to graphically change the boot order for the system.

---

### Post by Davidson_Poole on 2014-07-19
Tried efibootorder. Made Ubuntu at the top of the list instead of Windows Boot Manager, saved, and restarted. It still goes to the Windows Boot Manager. Check efibootorder once I boot back into Ubuntu, and it shows Windows Boot Manager at the top of the list, even though I had previously changed it.

---

### Post by oldfred on 2014-07-19
Windows and/or many Vendors UEFI implementations keep resetting Windows to be first in boot order. 

Grub only boots working Windows, so you have to boot Windows and fix it for grub to have a chance to boot it. 

As long as Windows is in this state grub cannot do anything, directly boot Windows from UEFI menu and make sure fast boot is off:

> Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /mnt/boot-sav/sda4
The disk contains an unclean file system (0, 0).
metadata kept in Windows cache, refused to mount.


 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

---

### Post by Davidson_Poole on 2014-07-19
But how do I change it from the control panel if I can't boot into Windows?

---

### Post by oldfred on 2014-07-19
If booting directly from UEFI menu or one time key and immediately pressing f8 does not get you into Windows repairs you need your Windows repair flash drive. That you should make every time Windows updates so you have the most current version.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

If you did not make the repair flash drive and do not know anyone else with Windows 8 that could make one you can pay to get one.

 We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Some third party Windows tools may also help.
      
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

These folks know more about Windows issues.

 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by Davidson_Poole on 2014-07-20
UPDATE:

Windows is now working, however the only way I can get into Ubuntu is by pressing F12 and selecting it. No Grub. Tried Boot Repair again, [http://paste.ubuntu.com/7826303/](http://paste.ubuntu.com/7826303/).

SecureBoot disabled, FastBoot disabled. Boot mode UEFI.

---

### Post by at_first_light on 2014-07-20
So you're saying that right now if you turn on the computer it will automatically boot into Windows, but Windows gets stuck at the loading screen where it just has the circle spinning forever? You can get to Grub2 and boot Ubuntu, but only if you press F12 at system start-up to make the Grub2 boot manager appear so you can manually choose to boot Ubuntu rather than Windows? Correct? I'm a bit confused about this last part. What does F12 do on your system, as it seems it differs from mine which simply displays a quick-boot menu where I can select which device to boot from? Doesn't your computer only have 1 hard drive?

[HR][/HR]

What it sounds like to me is the Ubuntu updates you installed most likely included kernel updates to 3.13-32 which was released on July 16 2014.

> **"http://security.ubuntu.com/ubuntu/pool/main/l/linux/"]linux-headers-3.13.0-32_3.13.0-32.57_all.deb 16-Jul-2014 17:42 [/QUOTE]

[QUOTE="http://paste.ubuntu.com/7826303/"]
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ce547702-55a9-4830-839b-d45508af398c' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt7'
    if [ x$feature_platform_search_hint = xy ] said:**
> 

Installing this kernel update resulted in updates to your Grub2. Again I still don't quite follow what F12 does on your system, but it sounds like it somehow allows you to get the Grub2 menu to show which suggests to me that for some reason Grub2 to being hidden by default, or has really low time-out length? Your Grub2, and Windows boot mangers seem to be working functionally which is why Boot Repair isn't helping. You can unhide or adjust the time-out length of Grub2 by booting up Ubuntu and re-editing the timeout length. I haven't included instructions for that, because I'm not really sure how F12 is helping you with Grub2, and fear I may be misunderstanding.

As far as Windows goes, it is booting, but once it boots it's unhappy about something. This problem appears to be in Windows, and your best hope for fixing is will be running Windows in safe mode, doing a disk check, and then shutting down the computer. To boot Windows 8 in safe mode press shift + F8 _before_ you get to the loading screen (with the circle spinning). However I tried this on my machine and couldn't get it work. I know you've already tried using F8 with no luck. :(

[QUOTE="http://pcsupport.about.com/od/windows-8/ss/windows-8-safe-mode.htm"]
The amount of time that Windows 8 looks for SHIFT+F8 is so small on most Windows 8 devices and PCs that it borders on impossible to get it to work


If you're one of the lucky few in this world who owns a Windows 8 installation disc you could try the repair options present on it.

---

### Post by Davidson_Poole on 2014-07-20
When I turn my computer on, it boots Windows, without a hitch now. When I turn my computer on, however, it SHOULD boot Grub, so I can select Ubuntu or Windows. Pressing F12 gets me to this boot manager thing that looks similar to [http://www.vodusoft.com/blog/wp-content/uploads/2013/03/Boot-menu-options.jpg](http://www.vodusoft.com/blog/wp-content/uploads/2013/03/Boot-menu-options.jpg), only with different names. I want my computer to boot Grub first, so I don't have to go to the boot menu every time I want to use Ubuntu.

---

### Post by LostFarmer on 2014-07-20
```
efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder:** 0004**,0000,0001,2003,2001,2002
Boot0000* ubuntu    HD(2,c8800,96000,40caaa80-c6bc-440d-9f79-ceb97acaf9a3)File(EFIubuntushimx64.efi)
Boot0001* Ubuntu    HD(2,c8800,96000,40caaa80-c6bc-440d-9f79-ceb97acaf9a3)File(EFIubuntugrubx64.efi)RC
Boot0002* EFI Network 0 for IPv6 (00-8C-FA-2E-1B-A6)     ACPI(a0341d0,0)PCI(4,0)PCI(0,0)MAC
Boot0003* EFI Network 0 for IPv4 (00-8C-FA-2E-1B-A6)     ACPI(a0341d0,0)PCI(4,0)PCI(0,0)MAC
**Boot0004*** Windows Boot Manager    HD(2,c8800,96000,40caaa80-c6bc-440d-9f79-ceb97acaf9a3)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS...
```

From your boot-info.  The bios boot order is Windows first, you need to change it to 'ubuntu' first.  If you know the correct key to enter the bios would be the easiest, it should give just enough info on screen to do it.  If you do not know the correct key to press, boot into grub and select "**System setup' $menuentry_id_option 'uefi-firmware**".  the third option is use linux program "efibootmgr" but you will need to do a web search on it use.

Note: the above has not a thing to do with the grub boot menu order, but the computers bios/firmware boot order using  EFI .

If you could post a outline on steps used to fix you Win 8 problem, so we and other will know just what worked.

---

### Post by at_first_light on 2014-07-20
> **Davidson_Poole said:**
> Pressing F12 gets me to this boot manager thing that looks similar to [http://www.vodusoft.com/blog/wp-content/uploads/2013/03/Boot-menu-options.jpg](http://www.vodusoft.com/blog/wp-content/uploads/2013/03/Boot-menu-options.jpg), only with different names. I want my computer to boot Grub first, so I don't have to go to the boot menu every time I want to use Ubuntu.

Okay that is the quick-boot menu. I'm not sure why using it is yielding different results given you only have 1 hard drive, and 1 EFI System Partition. This is with the usb stick not plugged in?

---

### Post by Davidson_Poole on 2014-07-20
Ok. (Following the instructions of [www.eightforums.com](www.eightforums.com) of course) I made a recovery USB drive, then booted into it. Once I did that I opened up command prompt from it, and typed in "chkdsk c: /r", and it ran for about an hour. Then after that I restarted and Windows was fine! Also, efibootorder says that ubuntu is first.

---

### Post by Davidson_Poole on 2014-07-20
Yes. The usb is not plugged in. It only gives me the option of booting ubuntu/Ubuntu/Windows boot manager when I hit enter on HDD. Yes, it says Ubuntu and ubuntu. Don't see a difference in either one.

---

### Post by oldfred on 2014-07-20
One ubuntu is grub and the other shim.
 See details posted by LostFarmer above as it shows which file is used in detail. You can edit descriptions in UEFI menu if you want to know difference.

If you have secure boot on then only systems with signed boot files will be shown in UEFI menu. But grub has a bug and will not boot Windows from grub menu if secure boot is on. So booting with shim is not really required currently.

---

### Post by at_first_light on 2014-07-20
> **Davidson_Poole said:**
> I made a recovery USB drive, then booted into it. Once I did  that I opened up command prompt from it, and typed in "chkdsk c: /r",  and it ran for about an hour. Then after that I restarted and Windows  was fine! Also, efibootorder says that ubuntu is first.

I'm glad to hear you've got Windows working again :). 

[QUOTE=""]
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10

[/QUOTE]
As far as getting Grub2 to show, your paste shows Grub2 is set to give 10 seconds to pick which OS to boot as it should which rules out my theory about being set to hidden.

> 
efibootorder says that ubuntu is first.


It's weird that efibootmanager tells you Ubuntu is set to first, but boot-repair claims Windows is. I've no theories about that.

---

### Post by oldfred on 2014-07-20
Some UEFI systems just keep Windows first. 
And any maintenance in Windows makes Windows first in UEFI.

Some with HP or Sony have to rename files to make it boot Ubuntu first, but I thought Toshiba worked ok with Ubuntu, but have some other idiosyncrasies.

---

### Post by Davidson_Poole on 2014-07-20
Well it worked perfectly fine before this ordeal.

---

### Post by Davidson_Poole on 2014-07-20
Restarted computer just to see if anything would change. Went straight to Windows, no Grub. So I restarted again and booted Ubuntu, and went to efibootorder. Windows was back on top. Changed it to where Ubuntu was on top, restarted. Straight to Windows. Something in Windows is changing the boot order to only boot Windows, and I don't know what. I don't even see any Grub when I boot.

---

### Post by slooksterpsv on 2014-07-20
Ouch, yeah the efibootorder pulls the info and modifications from efibootmgr - the problem is like oldfred has stated numerous times, that there's no uniformity with uefi and every maker has their own implementation. On my Toshiba C75DA I press F12 to get into the boot options menu, select the HDD and it presents me with Windows, ubuntu, Manjaro, and Ubuntu. Yes Ubuntu twice. efibootmgr and efibootorder may not help in this situation, I'd check for a BIOS update to see if maybe it can fix some issues with the UEFI.

---

### Post by Davidson_Poole on 2014-07-20
OK. Thanks everyone for helping me!

---

### Post by Davidson_Poole on 2014-07-20
IM me if any of you figure out how to make Grub work.

---

### Post by slooksterpsv on 2014-07-20
The only way to make Grub work at this point is to do the following, read the cautionary note first!
**NOTE:** Doing so will make your Windows partition unbootable, as Windows is relying on UEFI to boot from and the following steps will require 1 of 2 things. 1) a reinstallation of Windows - a recovery DVD won't work as it generally requires UEFI (at least in my experience). OR 2) A way to rebuild the BCD, MBR, etc. to contain Windows 8 bootable files to boot from it (research, I haven't tried this, but in theory it is possible to do).

You would have to disable UEFI (SEE NOTE ABOVE) and change it to Legacy or CSM and essentially reinstall from there. That way UEFI isn't controlling boot status and it goes by MBR where you could have GRUB doing so.

The only way I get UEFI to work for me is the following:

1. Shrink my Windows install for Ubuntu (with Windows already being installed).
2. When installing Ubuntu choosing Something else and manually setting up the partitions like so:
let's say I allocated 100GB to Ubuntu. I'd use 96GB for Ubuntu (ext4) and 8GB for swap. Here I'll show you my partition setup and explain:
```

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  1075MB  1074MB  ntfs            Basic data partition  hidden, diag
 2      1075MB  1180MB  105MB   fat32           Basic data partition  boot
 3      1180MB  1314MB  134MB   ntfs            Basic data partition  msftres
 4      1314MB  613GB   612GB   ntfs            Basic data partition  msftdata
 8      613GB   655GB   41.9GB  ext4
 6      655GB   739GB   84.0GB  ext4
 7      739GB   741GB   2049MB  linux-swap(v1)
 5      741GB   750GB   8687MB  ntfs            Basic data partition  hidden, diag

```

1, 2, 3, 4, 5 are - Repair, EFI, MS Reserved (Q: in Win 7), C: (Windows installation), and my recovery drive.
6,7,8 are - Ubuntu, Swap, and Manjaro.

So I'd do a custom, put Ubuntu on /dev/sda6, my swap is /dev/sda7, and I install grub on /dev/sda6 **NOT** /dev/sda !!!

That's how it's worked for me luckily.

---

