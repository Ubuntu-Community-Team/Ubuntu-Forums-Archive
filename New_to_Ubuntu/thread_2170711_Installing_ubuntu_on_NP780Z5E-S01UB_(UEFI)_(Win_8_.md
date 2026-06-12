---
title: "Installing ubuntu on NP780Z5E-S01UB (UEFI) (Win 8 pre-installed)"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by DRatJr on 2013-08-27
I have posted before about installing Ubuntu on my NP780Z5E-S01UB. I will give a quick recap of my previous problem below:

I installed Ubuntu 12.04 64 bit with really no problems on my laptop. I had it installed in UEFI mode with secure boot on. When I went to uninstall to install 13.04 I encountered my problem. Ubuntu was stuck on the boot menu in the UEFI settings. It was something like UEFI: ubuntu[...]. I could not get the entry off for anything. If I selected the entry, it went to a grub menu and said it couldn't start or something. I could boot into Windows 8 just fine, but the extra entry was annoying me. I had wiped my laptop and everything but still no dice. FINALLY after MONTHS of talking to customer support and googling, I got a BIOS updater tool which allowed me to reinstall my current BIOS version, which fixed the problem. Which brings me to my new concerns.

After dealing with that I learned that Ubuntu may brick certain samsung laptops with UEFI. I haven't found my exact model number on any of the numerous articles/forum posts I've read, but you never know. I read that it has only been known to affect 2012 samsung laptops. So now, I have a whole new batch of questions before I do ANYTHING with Ubuntu on my laptop, as I can not risk bricking this. 

My questions:
1. Is it possible to install Ubuntu in CSM/Legacy mode even though my Windows 8 was preinstalled in UEFI mode?
1.5. Would I have to switch UEFI mode ON if I wanted to boot back into windows IF I CAN install in CSM/legacy?
2. Could installing it in UEFI mode cause a brick if not possible?
3. Are there any precautions anyone knows of that I should know before attempting any Ubuntu installation?
4. Are there any more problems that have come to light about Samsung laptops and/or MY specific model?

---

### Post by mastablasta on 2013-08-27
how can it brick the laptop? it doesn't touch BIOS on install. so if nothing else you should still be able to boot in windows.

---

### Post by Jonathan Precise on 2013-08-27
> **DRatJr said:**
> My questions:
1. Is it possible to install Ubuntu in CSM/Legacy mode even though my Windows 8 was preinstalled in UEFI mode?
1.5. Would I have to switch UEFI mode ON if I wanted to boot back into windows IF I CAN install in CSM/legacy?

If your BIOS supports that tool, then yes it can. _**ALTHOUGH YOU WILL LOSE THE ABILITY TO BOOT WINDOWS UNTIL YOU TURN THIS TOOL OFF**_, yes you can.

When you turn on your computer, press a special key (like F10, F2, ESC, or others) to enter BIOS setup utility. Under CSM or LEGACY, set it to enabled (or in some cases, set BOOT MODE to LEGACY or CSM).

Set CSM or LEGACY to disabled (or in some cases, set BOOT MODE to UEFI) to boot Windows 8

> **DRatJr said:**
> 2. Could installing it in UEFI mode cause a brick if not possible?

> **mastablasta said:**
> how can it brick the laptop? it doesn't touch BIOS on install. so if nothing else you should still be able to boot in windows.

I agree with mastablasta, but just to be on the safe side, **_MAKE A FULL SYSTEM _****_BACKUP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!_** I recommend using [Clonezilla]("http://sourceforge.net/projects/clonezilla/files/clonezilla_live_alternative/20130819-raring/clonezilla-live-20130819-raring-amd64.iso/download") (burn it to a DVD, make sure you turn off Secure-boot, also in BIOS setup)

> **DRatJr said:**
> 3. Are there any precautions anyone knows of that I should know before attempting any Ubuntu installation?

Once again, **_MAKE A FULL SYSTEM _****_BACKUP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!_** I recommend using [Clonezilla]("http://sourceforge.net/projects/clonezilla/files/clonezilla_live_alternative/20130819-raring/clonezilla-live-20130819-raring-amd64.iso/download") (burn it to a DVD, make sure you turn off Secure-boot, also in BIOS setup)

> **DRatJr said:**
> 4. Are there any more problems that have come to light about Samsung laptops and/or MY specific model?

Check my signature for UEFI help. They might have info.

---

### Post by DRatJr on 2013-08-29
Many people on Samsung laptops have reported full bricks due to Samsung's UEFI firmware. Where if you overwrite over 50% of the variables (or something) it bricks the laptop. Now why this isn't reported in the 2013 models, I just wanted to be ABSOLUTELY sure I could avoid any problems.

---

### Post by DRatJr on 2013-08-29
ALSO:

Going to the Ubuntu UEFI page, which I've used before, should I do what is described in "Installing Ubuntu via trial and error" or "Installing in EFI mode"? Not sure which is the better route to take.

---

### Post by oldfred on 2013-08-29
There were (maybe related) a couple of issues with some systems. 

One was that the only way to get into UEFI was from Windows. So if you installed another system and Windows did not boot, then there was no way to get into UEFI to boot from a repair DVD or flash drive or change UEFI settings. Same issue would occur once Windows breaks as there would be no way to boot an external device for repair. 

The other issue was found to relate to the % use of UEFI variables. 


Links to the issues, but they now are old info as fixes have been released and newer models, UEFI updates, or Linux kernel changes seem to have resolved them.
 [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

 UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.
[http://mjg59.dreamwidth.org/23554.html](http://mjg59.dreamwidth.org/23554.html)

   Protection against Samsung UEFI bug merged into Linux kernel
[http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html](http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html)
Since these patches have not yet been integrated into the installation media for these distributions, users should always use the UEFI firmware's 
UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)

---

### Post by DRatJr on 2013-08-29
> **oldfred said:**
> There were (maybe related) a couple of issues with some systems. 

One was that the only way to get into UEFI was from Windows. So if you installed another system and Windows did not boot, then there was no way to get into UEFI to boot from a repair DVD or flash drive or change UEFI settings. Same issue would occur once Windows breaks as there would be no way to boot an external device for repair. 

The other issue was found to relate to the % use of UEFI variables. 


Links to the issues, but they now are old info as fixes have been released and newer models, UEFI updates, or Linux kernel changes seem to have resolved them.
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.
[http://mjg59.dreamwidth.org/23554.html](http://mjg59.dreamwidth.org/23554.html)

Protection against Samsung UEFI bug merged into Linux kernel
[http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html](http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html)
Since these patches have not yet been integrated into the installation media for these distributions, users should always use the UEFI firmware's 
UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)

Ok, well I CAN boot into Ubuntu on my NP780Z5E-S01UB with nothing going wrong. I get the "UEFI: Ubuntu" when selecting to boot from USB drive. I have 13.04 amd64 iso installed on the USB. You are recommending I install Ubuntu via Legacy/BIOS correct? And if so how would I do this?

ALSO, does the 13.04 64bit iso contain these fixed that you have mentioned or no?

---

### Post by DRatJr on 2013-08-29
OH and hey oldfred :D. You were the one who guided me through my earlier problems haha.

UPDATE:

I have a mode in my UEFI settings that allows me to do CSM AND UEFI booting. When I select this option, I get:

1.Windows Boot Manager
2. UEFI: (my flash drive)
3. (my flash drive)

So I am guessing that option 3, which does not have the UEFI prefix, is my bootable USB in CSM mode, correct? And if so, should I boot from this, and then install Ubuntu that way?

---

### Post by oldfred on 2013-08-29
If you install Ubuntu in BIOS/CSM mode you cannot easily dual boot. You would have to go into UEFI and turn that on and boot Windows or go into UEFI and turn on CSM and boot Ubuntu. But UEFI and BIOS write hardware data to drive for system to boot from differently and cannot be dual booted from grub menu.

Best to install Ubuntu in UEFI mode. But some systems only let you install in BIOS mode and then you can use Boot-Repair. It will convert to UEFI by uninstalling grub-pc and installing grub-efi. You will need Boot-Repair anyway to fix the os-prober bug.

---

### Post by DRatJr on 2013-08-29
So I should just install Ubuntu in EFI mode, and use the boot repair link in your sig?

---

### Post by DRatJr on 2013-08-29
Also, a few questions:

1. Do I turn secure boot off when trying to install 13.04?
2. Is there a guide for the boot repair tool?
3. After installing 13.04, and running the boot repair tool, will there be anything else I need to do to get ubuntu working?

Thanks!

---

### Post by DRatJr on 2013-08-29
AND my system WILL let me install it in UEFI mode. I had it installed before.

---

### Post by oldfred on 2013-08-29
I believe that secure boot is not currently required. But it is up to you. Ubuntu should install either way and Boot-Repair can convert from one to another, or you can do what Boot-Repair does manually.

Boot-Repair should fix boot issues, but right after boot may be video issues and you then need nomodeset as a boot parameter or other boot parameters. Boot-Repair can add nomodeset but not others. Easier I think just to add it on first boot if needed and then install proprietary drivers for Video. 

Then you may with new systems have specific issues with certain hardware. Varies a lot by vendor or specificy chips used.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by DRatJr on 2013-08-29
So you would recommend I use the LinuxSecureRemix INSTEAD of the official ISO correct?

Also, will I NEED to run boot repair? If so, what commands? And how will I know if I NEED to run it or not?

---

### Post by oldfred on 2013-08-30
If you want 13.04 the Secure Remix has the advantage of Boot-Repair built in. All others you can just add it. But with a live installer it is not normally saved or you download each time you may want it.
It automates the bug fix issues on os-prober and if you have other issues it may help. Just another tool that is good to know about and have available and hopefully not normally need.

Boot-Repair has an auto fix setting that almost always works. The only one I do not like is with auto fix it will install grub to every hard drive if you have more than one drive. I prefer to have a different boot loader on every drive to boot the install I have on that drive. Boot-Repair can do that also, but you have to uncheck auto and check update MBR and in Advanced choose what system to install to what drive. With UEFI it just installs grub to the efi partition, but it also will work with multiple drives and UEFI.

---

### Post by DRatJr on 2013-08-30
> **oldfred said:**
> If you want 13.04 the Secure Remix has the advantage of Boot-Repair built in. All others you can just add it. But with a live installer it is not normally saved or you download each time you may want it.
It automates the bug fix issues on os-prober and if you have other issues it may help. Just another tool that is good to know about and have available and hopefully not normally need.

Boot-Repair has an auto fix setting that almost always works. The only one I do not like is with auto fix it will install grub to every hard drive if you have more than one drive. I prefer to have a different boot loader on every drive to boot the install I have on that drive. Boot-Repair can do that also, but you have to uncheck auto and check update MBR and in Advanced choose what system to install to what drive. With UEFI it just installs grub to the efi partition, but it also will work with multiple drives and UEFI.


So, does the secure remix also get updates and such as the original 13.04 gets updates?

Also, all of this talk about multiple drives, does that pertain to partitions as well? Because I have 2 backup partitions, as well as my windows partition. Now, I will have four when I install ubuntu, so are you saying it will install grub to all 4?

And so if I do run boot repair, I should choose update MBR, advanced > and what do I select after that?

And also, how will I know if I NEED to run boot repair? Will Windows not boot or what?

---

### Post by Jonathan Precise on 2013-08-30
**_DO NOT CHOOSE UPDATE __MBR IF YOU INSTALLED IN UEFI MODE!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!_** Just run the recommended boot-repair. If you do not run boot repair (if you installed in UEFI mode), then you will not be able to boot windows (os-prober bug, os-prober uses legacy entries. Boot-repair adds UEFI entries).

In legacy, you do not need boot-repair unless ubuntu can't boot. To switch to windows, change 'CSM/Legacy/BIOS-mode' (in the BIOS setup utility) to 'UEFI'

---

### Post by oldfred on 2013-08-30
As Jonathan Precise strongly suggests, you want to be in UEFI mode not BIOS and with UEFI you do not use MBR, boot loader is in efi partition.

The secure remix is 13.04. It just is that Boot-Repair has been included in the ISO so you do not have to separately download it.

---

### Post by DRatJr on 2013-08-31
> **oldfred said:**
> As Jonathan Precise strongly suggests, you want to be in UEFI mode not BIOS and with UEFI you do not use MBR, boot loader is in efi partition.

The secure remix is 13.04. It just is that Boot-Repair has been included in the ISO so you do not have to separately download it.

OK so just install secure remix alongside windows in UEFI mode, and run recommended repair and that's it?

---

### Post by oldfred on 2013-08-31
Many users seem to be able to do that, but here in forum we get all the one's that have added issues so I have no idea how many work without issue.

---

### Post by DRatJr on 2013-08-31
Oh Fred. You never give me a straight answer. Lol.

---

### Post by oldfred on 2013-08-31
That is correct. :)

---

### Post by DRatJr on 2013-08-31
But seriously, install secure remix in UEFI mode, run recommended repair, right?

---

### Post by oldfred on 2013-09-01
That is correct.

---

### Post by DRatJr on 2013-09-02
When I ran boot repair, I got this message, so what do I do to fix this?:

[IMG]https://dl.dropboxusercontent.com/u/40868833/IMG_20130901_162136.jpg[/IMG]

And now my boot up screen looks like this: (Only Ubuntu and Windows Boot UEFI Loader take me to the two OSes)

[IMG]https://dl.dropboxusercontent.com/u/40868833/IMG_20130901_162541.jpg[/IMG]

---

### Post by oldfred on 2013-09-02
If those two work then you are good.

Grub2 has a bug in its os-prober and the last two Windows entries will never work.
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

You can turn off os-prober at least until grub bug is fixed. Instructions on cleaning up menus are in link in my signature.

I see you ran the rename function. Does your system only boot Windows. That is the few systems that modify UEFI to only boot Windows efi file which is not the UEFI standard.

It looks like you did this. The only disadvantage of the rename is that you cannot directly boot Windows from UEFI menu, but if your system is one that only boots bootmgfw.efi then you have to have the rename.


 Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
It does this:
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by DRatJr on 2013-09-02
Well "Windows Boot UEFI loader" and "Ubuntu" work and boot the correct OS. So I CAN boot Ubuntu and Win 8. 

And it prompted me if I wanted to backup and rename some files whilst running boot repair. I hit YES.

SO, please be a little clearer. What should I do next? You give a LOT of info, but I'm not sure what I SHOULD do and whatnot. Could you please give me maybe some steps and be a little clearer? Thanks.

---

### Post by DRatJr on 2013-09-02
UPDATE:

Ubuntu will NOT BOOT NOW. I turned my computer off and went to work, and now when I try to boot into ubuntu it just hangs at a purple screen. So what should I do now?

---

### Post by oldfred on 2013-09-02
When you first booted into Ubuntu did it run updates? And what video card/chip do you have. 
You may need nomodeset to get into Ubuntu and then install proprietary video drivers.

At grub menu press e, scroll down to linux line & replace quiet splash with nomodeset.

Examples, see second part on after install. First part is BIOS install screens.
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by DRatJr on 2013-09-02
Yes I did run updates in Ubuntu when I first got into it. So should I still press e in grub and replace quiet splash with nomodeset?

---

### Post by oldfred on 2013-09-03
What video chip/card do you have? 
Nomodeset usually works and you need to try it first. But some may need different boot options or additional boot options.

What other Samsung users with similar models did.
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

### Post by DRatJr on 2013-09-03
I have the [COLOR=#000000][FONT=helvetica]AMD Radeon&#8482; HD 8770M Graphics. So what should I do?[/FONT][/COLOR]

---

### Post by DRatJr on 2013-09-03
nvm this. That is my gfx chip. What should I do?

---

### Post by DRatJr on 2013-09-03
nvm this

---

### Post by oldfred on 2013-09-03
Still try nomodeset.
That is a newer AMD chip, but I do not know the latest with AMD.

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by DRatJr on 2013-09-03
Actually Oldfred, could you please tell me how to COMPLETELY REMOVE ubuntu and everything associated with it?

I know that JUST deleting the Ubuntu partition WILL NOT do it because I cannot boot Windows when I do this. So how can I remove Ubuntu, and still be able to boot into Windows?

---

### Post by Jonathan Precise on 2013-09-03
> **DRatJr said:**
> Actually Oldfred, could you please tell me how to COMPLETELY REMOVE ubuntu and everything associated with it?

I know that JUST deleting the Ubuntu partition WILL NOT do it because I cannot boot Windows when I do this. So how can I remove Ubuntu, and still be able to boot into Windows?

Use OS-Uninstaller from [Linux Secure Remix]("http://sourceforge.net/projects/linux-secure/files/?source=navbar"). That might leave you still with a Grub Menu, with which you select windows.

---

### Post by oldfred on 2013-09-03
Os-Uninstaller is a good choice.

But with UEFI you do not have to re-install any boot loaders as they all co-exist in the efi partition. You just change UEFI t to directly boot Windows.
I think you did the file rename and need to undo that.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

To totally remove it, you may have to not only delete the Linux & swap partitions, but delete the ubuntu folder in the efi partition and use your UEFI or UEFI shell commands to delete the ubuntu entry from the UEFI as UEFI also saves those entries.

 [http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)

---

### Post by DRatJr on 2013-09-03
Well I previously deleted the ubuntu partition, and had to REINSTALL ubuntu to be able to boot back into windows. Will the rename efi files work since I did this?

---

### Post by oldfred on 2013-09-03
It should.

You also have a backup of the original Windows efi file which you can copy into the efi partition and then UEFI should boot Windows directly.

       Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

And Boot-Repair normally copies backups, but they may have been in Ubuntu partition.

---

### Post by DRatJr on 2013-09-03
So I should run boot repair, and select rename EFI files? And then restart the ocmputer? I think I hit the option to backup and rename AGAIN after I reinstalled ubuntu after deleting the partition. Is what I asked correct?

---

### Post by oldfred on 2013-09-04
You should only use the rename if your system only Boots Windows. Some have modified UEFI to only boot Windows efi file so then rename is required. If you can boot an ubuntu entry from UEFI menu then you do not need the rename.

See post #38 as the rename was explained in it.

Example of a system that only booted Windows and Redhat. A few others found so Boot-Repair created the rename work around so UEFI thinks it boots Windows when it really is the grub shim file.
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by DRatJr on 2013-09-04
CURRENTLY: My machine will ONLY boot Windows 8. I ran the updates and I think that broke ubuntu. I JUST WANT TO REMOVE UBUNTU. So what should I do?

---

### Post by oldfred on 2013-09-04
Are you booting Windows thru grub menu or directly from UEFI menu. 

If from UEFI menu, then you can follow the procedures posted above to remove Ubuntu from UEFI menu, from efi partition and then remove partitions.

---

### Post by DRatJr on 2013-09-04
Through grub.

---

### Post by oldfred on 2013-09-04
Either use Boot-Repair to undo the rename as posted above (post #26) or copy the backup Windows efi file (Post #40) and then boot from UEFI menu . 

Once that works then you can remove Ubuntu.

---

### Post by DRatJr on 2013-09-05
I have the bootmgfw.efi file in that directory from post 40. Where exactly do I need to copy it? And if I copy it over, will this boot windows directly?

---

### Post by oldfred on 2013-09-05
You can rename this or copy your current copy into same folder.
 /EFI/Microsoft/Boot/bkpbootmgfw.efi 
      
 /EFI/Microsoft/Boot/bootmgfw.efi 
If you have run the rename, then your real Windows boot file is the bkpbootmgrw.efi. And bootmgfw.efi is really grub2's shim file. You should probably just rename not outright delete just in case.

Mount point will depend on whether viewing from Ubuntu install, liveCD or from Windows. 
Ubuntu mounts at /boot/efi so it is this from Ubuntu.

 /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi

---

### Post by DRatJr on 2013-09-05
I AM IN THIS DIRECTORY:

C:\Windows\Boot\EFI

The ONLY files I see are (other than folders):

boot.stl
bootmgfw.efi
bootmgr.efi
memtest.efi

I DO NOT have the bkp file. So what should I do then?

---

### Post by oldfred on 2013-09-05
Then from UEFI you should be able to directly boot Windows. If not then you have Windows issues. Not related to grub nor Linux.

---

### Post by DRatJr on 2013-09-05
Ok here's something interesting:

I DON'T have the bkpbootmgfw.efi file in my EFI directory, BUT IN GRUB it says boot from that file, and it boots me into windows. Why can't I find the file though?

---

### Post by oldfred on 2013-09-05
Unless grub boot stanaza was updated but not the description of what file you are actually using to boot with that would not work.
But can you boot from UEFI menu directly to Windows not thru grub. As that is the real test. Everything does not matter if you want to remove grub.

You can post another link to BootInfo report to see what files you have and what files grub is ac tally specifying to use to boot with.

---

### Post by DRatJr on 2013-09-05
I go into my UEFI and select Windows Boot Manager to boot from, and there are 2 entries for this, and they both boot me into grub.

ALSO: I can NOT boot into ubuntu. I added nomodeset and it booted, but it asks me for login and password. I put my username i chose and pw but it always says login incorrect. Should I just boot my USB and run a boot info summary?

---

### Post by oldfred on 2013-09-06
If you get to login and have password issues you have forgotten name or password.

Often if just a new install it may be easier to reinstall.
Otherwise you can reset.
       [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

Post new link to bootinfo report.

From live installer or  Ubuntu if you can get into it.


 sudo efibootmgr -v

---

### Post by DRatJr on 2013-09-07
Here it is:

[http://paste.ubuntu.com/6073538/](http://paste.ubuntu.com/6073538/)

---

### Post by oldfred on 2013-09-07
Boot-Repair will not fix your password issues.

You still show this.
 /EFI/Microsoft/Boot/bkpbootmgfw.efi 
/EFI/Microsoft/Boot/bootmgfw.efi 

I assume the bootmgrw.efi is really grub's shim and the bkp file is the real Windows boot file. As posted several times before you can use Boot-Repair to undo the rename or manually copy the original Windows file into the Microsoft efi folder.

---

### Post by DRatJr on 2013-09-07
And then I will boot Windows automatically?

---

### Post by oldfred on 2013-09-07
It should. Did you try it?

---

### Post by DRatJr on 2013-09-07
[http://paste.ubuntu.com/6077482/](http://paste.ubuntu.com/6077482/)

---

### Post by DRatJr on 2013-09-07
That is my boot info summary from restoring EFI backups. Thanks!!! It worked. Now I have another question:

I currently have FIVE entries in my UEFI boot menu:
Windows Boot Manager (...)
Windows Boot Manager (...)
Ubuntu (...)
Ubuntu(...)
Ubuntu(...)

I assume the three ubuntus are "Ubuntu" "Ubuntu.something.29.generic" and "Ubuntu.something.19.generic". BECAUSE I saw these in grub under "Ubuntu" and "Advanced options for Ubuntu". Now my question is this. How do I remove them? And how do I finish removing ubuntu? Should I boot from my Live USB and run OS uninstaller on Ubuntu?

---

### Post by oldfred on 2013-09-07
See post #38. UEFI has its own memory and you have to delete from either UEFI or with UEFI shell commands. Also delete from efi partition and delete Linux partitions.

---

### Post by DRatJr on 2013-09-08
I tried using the efibootmgr to remove the entries but it didn't work. BUT I did find the ubuntu folder in the SAMSUNG_REC partition which I can only see in ubuntu, its in EFI/Boot/Microsoft and its a folder called ubuntu. Should I delete that?

---

### Post by DRatJr on 2013-09-08
UPDATE:
Here is where the folder is. It is in my SAMSUNG_REC partition in EFI. Should I delete this folder?

[IMG]http://i.imgur.com/vkZ8u7s.png[/IMG]

---

### Post by DRatJr on 2013-09-09
So what should I do out of what I /think/ I should do?:

1. Use OS-Uninstaller to uninstall linux.
2. Delete the Ubuntu folder in my EFI folder on my SAMSUNG_REC partition.
3. Delete Ubuntu partition.

Should I do those three in that order or what?

---

### Post by oldfred on 2013-09-09
Your last BootInfo report showed the ubuntu folder in both the sda2 efi partition and sda9 Recovery partition.
I would delete from both. 
As with anything it is a good idea to have backups or ways to repair & recover your system.
And use Boot-Repair to uninstall, I would think it might remove those ubuntu partitions but do not know for sure.
Then you should be able to remove the Ubuntu partition. But I would make sure Windows boots after each step.

If you do not have this, make sure you do.
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Even after those deletions you may still have the entry in UEFI as it has its own memory. If you cannot delete from UEFI menu, you may have to boot Ubuntu liveCD and run this.
 [http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
      
 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). see #5 for example of delete.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by DRatJr on 2013-09-11
So where should the ubuntu folder be in the efi partition? It is NOT in Windows>Boot>EFI in my main C:/ drive. I only saw it in the recovery partition.

---

### Post by oldfred on 2013-09-11
All boot folders in the efi partition are at the same level. So if you have anther install it will be at the same level as Windows folder in the efi partition.
Installed Ubuntu mounts the efi partition as /boot/efi, so it depends on how you mounted it how you may see it. Both Ubuntu & Windows also create the folder /Boot which is access to shell.
 /boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/Boot/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi


Other files are also in each folder, just main boot file shown and you may have many more folders if you install many other systems.

---

### Post by DRatJr on 2013-09-15
> **oldfred said:**
> All boot folders in the efi partition are at the same level. So if you have anther install it will be at the same level as Windows folder in the efi partition.
Installed Ubuntu mounts the efi partition as /boot/efi, so it depends on how you mounted it how you may see it. Both Ubuntu & Windows also create the folder /Boot which is access to shell.
 /boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/Boot/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi


Other files are also in each folder, just main boot file shown and you may have many more folders if you install many other systems.


Ok what I am saying is:

C:/Windows/Boot/EFI has NO Ubuntu folder. Or at least I can NOT see it from within Windows. I have C:/Windows/Boot/EFI/ bootmgfw.efi and bootmgr.efi

BUT in the recovery partition, I DO have the Ubuntu folder in the location you stated. So what should I do? JUST delete it from the recovery one, or what?

---

### Post by oldfred on 2013-09-15
You can make a copy if you want, but you should just delete it.

---

### Post by Jonathan Precise on 2013-09-17
> **DRatJr said:**
> UPDATE:
Here is where the folder is. It is in my SAMSUNG_REC partition in EFI. Should I delete this folder?

[IMG]http://i.imgur.com/vkZ8u7s.png[/IMG]
No. Do not delete anything from the recovery partition, because if your computer gets damaged, then recovery might not restore it correctly if it was touched.

Instead, BACK UP EVERYTHING!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Then click on computer. Go to the folder called boot. Then efi. Then EFI. Then rename "ubuntu" to "ubuntu.old".
Afterwards, go to boot-repair and click on "Restore previous EFI files" or a similar option.

Then go to OS-uninstaller to uninstall ubuntu.

After everything above, go to GParted to erase the ubuntu partition.

Reboot into windows. Then go to the windows partitioning tool. Re-size the windows partition to fill the free space. Reboot.

Reboot again.

Reboot one last time for safety.

Tada!!!

PS. Try not to use the image tool. Instead, use attachments, so that people with slow internet can have the page load faster.

---

