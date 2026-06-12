---
title: "Ubuntu 12.10 x64 Fails To Detect Other OSes During Install"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by The Enigma on 2012-12-02
OK, i realize this question has probably already been asked on this forum already, and i've done a little reading, but couldnt find an answer that seemed logical. so first i will start by explaining my situation:

What i want is a triple boot system (laptop), which will consist of Win8Prox64, WinServer2012x64, and Ubuntu 12.10 x64. Earlier today i completely formatted my HDD. I then proceeded to install Win8. after that i logged in, shrank the C drive, and then created 2 new partitions, one for Server 2012, and another for Ubuntu. The Server partition is of course NTFS and is approximately 50 gigs. I allocated 20 gigs for the Ubuntu partition. I performed no other app installs or configurations etc during this time. i then immediately rebooted and proceeded to install Server 2012. after that i logged into Server and then immediately rebooted, again with no modifications made. then i proceeded to start the Ubuntu install. but near the beginning it gets to a screen that says no other OSes can be detected, with the only option being to wipe my drive and give all of it to Linux. Obviously, i dont want that, or i wouldnt be here, and i would have simply continued the install.

So...........what can be causing this error? i really do not want to spend alot of time figuring this out, because i'm a busy person with alot of constraints on my time. but if i can find a solution within the next day or so, then great. if not, i'll just continue using Windows as i always have. Linux has been something i've messed around with here and there, and Ubuntu in particular, but i never delved too deeply into it and when i did install it it never stayed on my system for more than a few weeks. I'd like to change that.

Well, thanks for any help!

EDIT: dont think this will help out much, but forgot to say that i didnt format the 20 gigs i allocated for Ubuntu, so it doesnt have a filesystem on it, and presumbly is in RAW data mode (whatever that means i have no idea, it's just what i saw when doing the partitioning in Disk Management in Windows 8).

---

### Post by Bashing-om on 2012-12-02
The Enigma; Hi !

With the advent of newer technologies, installations are no longer a simple matter.
Windows 8 I presume incorporates UEFI booting and or GPT partitioning. ubuntu can cope with these but, one has to be aware of how the machine is set up and install ubuntu accordingly. 
Here are relevant links to help you get installed triple booting.
[http://ubuntuforums.org/showthread.php?t=2059640](http://ubuntuforums.org/showthread.php?t=2059640)
[http://ubuntuforums.org/showthread.php?t=1974392](http://ubuntuforums.org/showthread.php?t=1974392)
[http://ubuntuforums.org/showthread.php?t=2076602](http://ubuntuforums.org/showthread.php?t=2076602)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[INDENT][INDENT]I do hope this helps <== BDQ

[/INDENT][/INDENT]

---

### Post by The Enigma on 2012-12-03
Bashing-Om, thanks for the reply.

I suspected that the issue may have something to do with MS's new UEFI secure boot in 8 and Server 2012, but have no way to confirm it. but regardless, if there is a workaround, then UEFI is no limitation, if it is indeed the true cause of the issue. I'm now posting in the following thread alongside a user who is having pretty much the same issue as me. there seems to be more discussion on this there. a user in that thread has also suggested that windows is taking up all the primary partition slots, and suggests that is the cause. in addition to UEFI, that also seems to be a plausible explanation, especially when taking into consideration the fact that my windows partitions are unmodified in any way, except for the disk repartitioning.

Link:

[http://ubuntuforums.org/showthread.php?p=12384721#post12384721](http://ubuntuforums.org/showthread.php?p=12384721#post12384721)

And if anyone is interested in knowing, my laptop model is an ASUS G75VW. I also mention this because i had a major issue when atempting to install Ubuntu 12.04 alongside Windows a few months ago. the issue was that the scrolling text screen (or whatever it is) would freeze before reaching the install phase. it seems the issue was due to ACPI, so i used the acpi=off switch, but then i was able to make it to the install screen/live cd desktop and the mouse (cursor) didnt work. so i gave up. this seems to be fixed in the 12.10 installer, and i'm giving it another go, but now i have the unforeseen issue described in my post above. 

Well, thanks for the links, i'll be sure to read them thoroughly.

---

### Post by oldfred on 2012-12-03
Are you UEFI or BIOS as that makes huge difference on how you install.

If UEFI this was another model but often vendors use the same UEFI/BIOS.
       Windows 8 & Ubuntu  ASUS K55A 
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

    
       Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
    
If BIOS you have to install each Windows in primary partitions with the boot flag on that partition as you install. Then grub can separately boot each. Otherwise Windows moves all boot files and configurations from second install to first install that has boot flag. Boot flag in Windows is active partition.

---

### Post by The Enigma on 2012-12-03
oldfred, you have me more confused than ever. all PCs have a BIOS, i would think, and i'm pretty sure that both Win 8 and Win Server 2012 are installed with UEFI enabled by default. but can an OS use both?

Simply put, i have no idea whether i'm UEFI or BIOS or both.

I used the non-UEFI option when booting from my live usb to install ubuntu since i figured the install process would be the same for both.

---

### Post by Bashing-om on 2012-12-03
oldfred is the "authority" on booting, I abandoned window long ago thus my assistance is second hand info. I have this to  determine  how  Windows is booting; in BIOS mode or in EFI mode? You can find out by typing "bcdedit" in a Windows Administrator Command Prompt window and looking for the "path" line in the "Windows Boot Loader" section. If this line refers to winload.efi, then you're booted in EFI mode; if it refers to winload.exe, then you've booted in BIOS mode.

Hope this helps to clear things up a bit. <== BDQ

---

### Post by oldfred on 2012-12-03
I have abandoned Windows mostly. Laptop still is dual boot, but I only use laptop on vacation or just to have a XP Windows available.

Almost all very new system are UEFI, but have a BIOS or legacy boot mode. But if Windows is installed in UEFI, then Ubuntu has to be UEFI for them to dual boot. 

Boot-Repair can convert a BIOS Ubuntu install by uninstalling grub-pc and installing grub-efi. You also need Boot-Repair to create a correct chain load entry for Windows as grub2's os-prober only knows BIOS and that does not work with efi.

Post this if you have not installed.
       sudo parted /dev/sda unit s print
    
If you have installed Ubuntu download this into your Ubuntu liveCD/DVD/Flash drive and post the link. Only the 64 bit version of Ubuntu 12.10 is compatible with pre-installed Windows 8 that has secure boot. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

