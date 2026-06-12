---
title: "New install won't boot and boot-repair won't run"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by apaw on 2012-04-14
Hi all.

        [LEFT]I just freed up space on a Win7 system to go for a dual boot Mythbuntu install. This is a 64 bit install.

[/LEFT]
        [LEFT]I've installed 3 times but it always boots to Win7. I tried several things and finally found boot-repair instructions at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). I can't get boot-repair to run (even sudo boot-repair). I just installed Xubuntu on a netbook and Linux Mint on an old desktop, but this one is being a major problem!

[/LEFT]
        [LEFT]Here is the url created by Boot Repair: [http://paste.ubuntu.com/930407/](http://paste.ubuntu.com/930407/)

[/LEFT]
        [LEFT]When I try to run the standard or advanced options boot repair, I get the message "Please close all your package managers (Software Center, Update Manager, Synaptic, ...). Then try again." But I'm not running any package managers!

[/LEFT]
        [LEFT]I'm running the boot-repair off of a Live USB of the Mytbuntu 11.10 64bit install iso.

[/LEFT]
        [LEFT]Any help on how to get dual booting working would be appreciated! I'd prefer to use GRUB as the boot loader, but if there's a way to add Linux to the Windows boot manager I'd be OK with that. Just want to get this thing up and running!

[/LEFT]
        [LEFT]Thanks in advance,[/LEFT]
    [LEFT]APaw[/LEFT]

---

### Post by abnordude on 2012-04-15
Well...
Yes, i have used boot-repair....and have got the same message as u got (package manager)......I dunno if it helps....but I used Grub4dos from puppy linux...
It works okay in mine....

---

### Post by westcoast01 on 2012-04-15
Silly question but is your system (cpu) 64bit? Are you running a X64 windows?

---

### Post by apaw on 2012-04-15
Yup, it's a 64-bit system running Win7 for 64bit.

---

### Post by apaw on 2012-04-15
I also tried boot-repair from ubuntu secured remix and still got the software package update running error.

I then tried this: [http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)

But it dumped to grub rescue.

Very frustrating...

---

### Post by apaw on 2012-04-15
After trying a lot of things, I finally went for a complete reformat with Ubuntu 11.10 from the recovery remix, and that gives errors at GRUB but boots. Could not get Mythbuntu to load. Hopefully installed MythTV won't be too much of a hassle.

---

### Post by oldfred on 2012-04-15
You have large drives with gpt partitioning. To boot with Windows you have to be booting with UEFI. Ubuntu/grub still has some issues but most are able to install, best to use newest version as then grub has a few more fixes.

But you also show a bios_grub partition which would be booting with BIOS mode, most new UEFI system will boot in either mode. If oboting with UEFI both Windows and grub put files in the efi partition to boot.

Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.

---

