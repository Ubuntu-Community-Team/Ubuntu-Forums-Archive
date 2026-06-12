---
title: "ASRock X79 + UEFI = no boot"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by danielchambers on 2012-03-19
** Sorry for the huge pics. **

6-core i7-3930k @ 3.2GHz (3.8 Turbo)
16GB RAM
Zotac GTX 560 2GB
ASRock X79 Extreme 4-M motherboard
[http://www.asrock.com/mb/overview.asp?Model=X79%20Extreme4-M&cat=Specifications](http://www.asrock.com/mb/overview.asp?Model=X79%20Extreme4-M&cat=Specifications)
According to Windows' Device Manager, the 2TB drive is a "Hitachi HDS723020BLA642 ATA Device"
...
"Partition Style: Master Boot Record (MBR)"
...

I tried to install the 697MB ubuntu-11.10-desktop-amd64 iso 4 ways without success: 2 bootable USB attempts, and 2 DVD attempts.

Pendrive Bootable USB.
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
I reboot & hit F11 for the Boot Menu. This   gave me two USB boot options:
USB: SanDisk
UEFI: SanDisk
Both attempts froze at about 5 seconds into booting Ubuntu.
[IMG]http://i40.tinypic.com/2n01ppu.jpg[/IMG]

DVD.
Reboot, F11 for Boot Menu. Two DVD options -- AHCI or UEFI.
Like the USB attempts, both froze at the same point in time.
[IMG]http://i40.tinypic.com/s2a3nl.jpg[/IMG]

Freeze point.
[IMG]http://i40.tinypic.com/2gvuc05.jpg[/IMG]

The only difference in the 4 attempts was after choosing the  DVD with UEFI: ATAPI. Before the install options appeared, this  message flashed quickly:
error "prefix" is not set.
Then, a text boot screen (no GUI) and freeze.

I've read a few pages on (U)EFI, Hybrid EFI, but, *man*, I'm in the weeds.
Pointers to good information are appreciated. Thanks.

---

### Post by mastablasta on 2012-03-19
are you saying you didn't get the grub menu? 
if you got to the grub menu you could try some of the boot options.
 
is the iso good? did you check md5sum?
 
regarding UEFI have you read this: [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by danielchambers on 2012-03-19
I got to the install menu no matter which ASRock boot option I chose, but the freeze happened whether I chose to run the image live, or to install to disk.
I burned the DVD @ half speed with Verify checked in ImgBurn, without incident.
And, no, I hadn't read that page yet. Looks like it may have the answer! Thanks, I'll read it now. :)

EDIT: I did not check the md5sum. Will do.
EDIT: Checked. No miscompares or errors.

---

### Post by danielchambers on 2012-03-19
Unless I read this wrong, my first step

[https://help.ubuntu.com/community/UEFIBooting#Setting_up_GRUB2_.28U.29EFI](https://help.ubuntu.com/community/UEFIBooting#Setting_up_GRUB2_.28U.29EFI)

is to get the latest grub2,  but, "it is strongly recommended to use a Linux distribution to compile grub2-efi..."

If I can't get past the hardware detection phase to boot a live distro, to load grub 1.99... :confused: Would trying another version (like the larger DVD iso) make a difference? It loads the same as the 697MB iso, right?

If I could just get a command line I would mount that 100MB partition like a hot floozy, and get this show started.

---

### Post by tbhatia4 on 2012-03-19
check whether your image is fine or it has errors,
 in that case re download the image

---

### Post by danielchambers on 2012-03-19
Hi tbhatia4.
I burned the iso in ImgBurn with the Verify box ticked. No errors.
Tried the install 4 ways, it kept freezing, so I came back to Windows.
Posted here, was told to check the md5sum and disc for errors.
Opened the disc with ImgBurn and checked "Verify against image file." It returned no errors.
Doesn't that mean the md5sum is good? Am I missing something?
What else can I do besides downloading and burning another copy?

I appreciate the response. I ran my old pc to death & this is the only one I have. I'd rather use Windows for gaming only; Linux for everything else.

---

### Post by oldfred on 2012-03-19
With nVidia you also will need the nomodeset, but with UEFI I have not idea how to add that.

Are you installing Windows also? Windows will install in MBR with BIOS boot or UEFI only with gpt. Ubuntu may overwrite the efi partition if installed second so back up the files in the efi partition from Windows.

see also this thread on UEFI booting:
[http://ubuntuforums.org/showthread.php?t=1870135](http://ubuntuforums.org/showthread.php?t=1870135)

BIOS/MBR nomodeset info:
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by danielchambers on 2012-03-20
Thanks, oldfred. Once I get it working (a day or two) I'll post how it was resolved. :)

---

### Post by flurospar on 2012-03-20
I severely hope not, but might be "Secure boot" the culprit here?

[http://linux.slashdot.org/story/12/01/18/167257/will-secure-boot-cripple-linux-compatibility](http://linux.slashdot.org/story/12/01/18/167257/will-secure-boot-cripple-linux-compatibility)
[http://linux.slashdot.org/story/12/01/14/0236244/microsoft-taking-aggressive-steps-against-linux-on-arm](http://linux.slashdot.org/story/12/01/14/0236244/microsoft-taking-aggressive-steps-against-linux-on-arm)
[http://linux.slashdot.org/story/11/09/21/062231/how-microsoft-can-lock-linux-off-windows-8-pcs](http://linux.slashdot.org/story/11/09/21/062231/how-microsoft-can-lock-linux-off-windows-8-pcs)

---

### Post by danielchambers on 2012-04-17
Weeks later and still I can't bypass or get rid of that accursed secure boot. There's no obvious way to turn it off, and entering the Konami code does nothing. :)

When a solution comes around, I'll post it here. Thanks again for the help.

---

### Post by oldfred on 2012-04-17
I think you have the issues of BIOS(AHCI) or UEFI and video mode issues.

You first need to decide if booting in BIOS or UEFI and then add the nomodeset parameter.

Almost everyone that has gotten UEFI to work has partitioned in advance. And with the new versions no compiling of grub2 is required.

I do not think you have secure boot or else UEFI menu would not give you any choices, it would just boot Windows.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

