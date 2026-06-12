---
title: "[Solved] Ubuntu  / win 10 dual-boot set up issue. Not working after boot-repair"
date: 2017-11-28
forum: New to Ubuntu
---

### Post by timyitong on 2017-11-28
I need some help for how to fix my current UEFI / grub2 setups.

I installed ubuntu 16.04 after installing windows. At first, if I turn on my BIOS to accept UEFI only; I won't even see the UEFI bootable partition for Ubuntu. I followed the guides on [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and triggered "recommended repairs". The boot info is listed here: [http://paste.ubuntu.com/26062300/](http://paste.ubuntu.com/26062300/)

Now I can see the bootable partition from BIOS but then if I try to boot it I'll get the error message:
"... open \EFI\UBUNTU\grubx64.efi  - Not Found .....  " Any idea how to resolve the issue. Could the upper/lower cases matter? As I observed that in my boot info, the efi files are under "\EFI\ubuntu\" instead of "\EFI\UBUNTU" ?

Many thanks!

---

### Post by Dennis N on 2017-11-28
What I notice is that your disks all have MSDOS partitioning, so Ubuntu should be installed in BIOS mode, not UEFI. For UEFI systems, we use GPT partitioning for the disk.

---

### Post by yancek on 2017-11-28
Read the Ubuntu documentation at the link below.  You should have an option in the BIOS to select booting in Legacy or CSM mode as well as EFI and you need to select Legacy/CSM.  Scroll down to the section "Set up the firmware in UEFI or BIOS/CSM/Legacy mode".

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by timyitong on 2017-11-28
MRB format is indeed worrisome. But I'm suspecting my current issue is not directly caused by disk format; as my windows boot loader is in MRB format but loaded via UEFI only mode in BIOS which works fine.

I do notice one issue is that default "grub-install" or "boot-repair" will install the grub*.efi files to /dev/sda7 (which is an EPS created for Linux); but actually I'm having another EPS called /dev/sda1 which is the windows recovery disk and boot loader location. So if I manually copy the /EFI/ubuntu folder from /dev/sda7 to /dev/sda1, I am able to boot into Grub! But with one caveat: I only booted into grub> shell but not the grub menu.

grub> ls
will complain the current root ((hd0, msdos1)) as unknown filesystem but
grub> configfile (hd0, msdos5)/boot/grub/grub.cfg will successfully load the grub menu.

So this seems to suggest that there is some issue that prevents from the auto search cfg located at /EFI/ubuntu/grub.cfg from loading (as if it's loaded successfully, root / prefix should switch to (hd0, msdos5) instead). I even manually typed the commands in the shell and verified that those commands are working properly. So the weird thing now is that EFI is able to load grubx64.efi properly but somehow cannot read grub.cfg? Any idea what could be a quick fix instead of going back to migrating disk formats?

---

### Post by oldfred on 2017-11-28
Best not to mix UEFI & BIOS.
And then follow standard UEFI with gpt and BIOS with MBR.
You can use UEFI with MBR but uncommon (except many installers are MBR but boot in either BIOS or UEFI mode).

UEFI & BIOS are not compatible, once you start booting in one mode you cannot switch to other mode, just reboot. And then if you really want the 35 year old BIOS/MBR configuration always boot in BIOS mode including flash drives or installers.

Since you elected to install Windows in BIOS mode on newer UEFI system, better to install Ubuntu in BIOS boot mode. Or reinstall Windows in UEFI boot mode.

Did you install Windows in UEFI mode before, or was system originally UEFI? You show a Windows UEFI boot entry  and all sorts of gpt issues. Windows if installed in BIOS mode incorrectly converts a gpt disk to MBR.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by timyitong on 2017-11-29
Hi Oldfred, thanks a lot for the info. I guess I hit into a BIOS compatible windows with an UEFI boot drive majorly because I did not disable BIOS compatible mode when installing windows; causing windows itself to create an NTFS MBR formatted ESP partition that becomes really painful to work out:
- BIOS boot mode will cause other painful issues rooted from my motherboard, making windows reboot going into system recover partition randomly. (Generating 0x000000f error)
- UEFI only mode does not allow Ubuntu to be installed into the same ESP, forcing me to create another ESP for Ubuntu.
- But then I ran into grub2 issue that it cannot properly load its default .cfg file in NTFS system. And my BIOS seems to have another bug that it keeps overriding my dual ESP configurations into one single ESP, causing [COLOR=#000000]"... open \EFI\UBUNTU\grubx64.efi - Not Found ..... "[/COLOR] issue originally described in this thread.

I ended installing rEFInd via manually copying its EFI directly into windows ESP. Manually added EFI boot entry via efibootmgr commands.

Then leverage rEFInd's powerful ability of auto scanning out all bootable .efi and linux kernels during boot time. In the end I basically gave up grub2 and use rEFInd as the primary glue to boot both Windows and Ubuntu. So far it works great and it even has a great advantage that as long as I keep the original windows ESP as is; it can detect any additional newly installed OSes seamlessly.

---

### Post by timyitong on 2017-11-29
Highly recommend using rEFInd:  [http://www.rodsbooks.com/efi-bootloaders/refind.html](http://www.rodsbooks.com/efi-bootloaders/refind.html) if dual booting partitions and efi boot entry configurations become messy.

---

### Post by oldfred on 2017-11-29
Just for the record what brand/model system.
Some do require a lot of work arounds, and rEFInd is one of the solutions. Been intending to try it but never got around to it yet.

---

### Post by timyitong on 2017-12-14
For info sharing, my motherboard: MSI X370 Gaming Plus, CPU: AMD Ryzen 7 1700, using dual disks: 1TB Samsung 850 EVO and 2TB Seagate FireCuda. Lots of issues feel to be related with the fact that I am having two disks while installing initial OS and the motherboard has lots of catch-you moments.

---

