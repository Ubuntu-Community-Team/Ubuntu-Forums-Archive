---
title: "Windows 7 not found by 13.10 installer"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by bertmung on 2013-12-08
I had erroneously created two wubi 12.04s.
I uninstalled 12.04.
The wubi boot still lists one of them, but it isn't active.
Now I'm trying to install 13.10 from a bootable pen drive.

Early in the boot a message about not being able to find something appears. It doesn't persist long enough for me to figure out what. After that the system boots into 13.10 from the pen drive with no other apparent problems.

The installer doesn't detect windows 7. "This computer currently has no detected operating systems."

Here's what I've done so far to solve the problem.

I've resized the partition containing windows 7. I now have unused space on the drive.

Ran chkdsk on the windows system by checking for and fixing errors from the control panel. While doing the check during the next windows start I briefly see a message confirming that an NTFS file system was checked.

Ran boot-repair. The log of this is at [http://paste.ubuntu.com/6542627/](http://paste.ubuntu.com/6542627/)

I'm tempted to have the installer use the unused space in the hard drive to install 13.10. I'm afraid I'd end up losing windows 7.

---

### Post by oldfred on 2013-12-09
Have you used all 4 primary partitions?
Post this:
sudo parted -l

Some common issues
 BIOS settings to disable "Boot Sector Virus Protection" or called Security or locked down Boot sector, Bitlocker
Though my drive was appearing in the bios and working for install it was actually "disabled"! 
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize, so reboot before install.
Raid meta data on drive - even if one drive (Vendor happend to set it on) or Intel SRT on Ultrabook
Old gpt data on drive where Windows installed in BIOS/MBR mode

---

### Post by fantab on 2013-12-09
[QUOTE= from BootInfo Summary]parted -l:

Model: ATA TOSHIBA MK3265GS (scsi)
Disk /dev/sda: **320GB**
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     **Size**    Type     File system  Flags
1      1049kB  1574MB  **1573MB**  primary  ntfs         boot
2      1574MB  169GB **  167GB**   primary  ntfs
3      310GB   320GB   **10.5GB**  primary  ntfs[/QUOTE]

To install Ubuntu installer needs to see either a Partition with Linux filesystem, like Ext4, or it should see some 'unallocated space'. You have neither.
However there is about 140Gb of spaces unaccounted from the above information.

Post a Screen-Shot of your HDD with its partitions from 'Windows Disk Management'... that should tell us where that space is and how to proceed.

---

### Post by oldfred on 2013-12-09
Was I totally asleep, I missed Boot info report.

It does look like you booted Boot-Repair in UEFI mode. But you Windows is BIOS with MBR partitions, so you need to always boot in BIOS mode. How you boot installer is how it installs, BIOS or UEFI.
You want the BIOS screen not the UEFI grub menu.
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by bertmung on 2013-12-10
In UEFI mode the live thumb drive boots, but doesn't see Windows 7.

Trying to boot the live thumb drive in "legacy" mode results in a black screen with a short white line flashing in the upper left corner of the display.

---

### Post by bertmung on 2013-12-10
Here's my best effort at getting one of the requested screenshots posted.

[IMG]C:\Users\Bert\UbuntuOne\2013\Screenshots\Capture.png[/IMG]

Looks like I need help with entering URL's for images too.

---

### Post by bertmung on 2013-12-10
Sorry to be so scattered.

Windows is only visible in legacy mode (BIOS?) and 13.10 is only visible in UEFI. Looks like I need to convert the Windows partition to gpt. (or make a 13.10 install medium that can boot in legacy?)  I see various ways posted to convert partions to gpt. What's recommended? Doing a totally new install of Windows 7 isn't a problem. I store nothing of value on the Windows partition.

If I could post an image it would show that I have 131.31 GB of unallocated space on the hard drive.

---

### Post by oldfred on 2013-12-10
Windows 7 DVD will not install in UEFI mode. But supposedly you can convert it to flash drive and do some updates to make it UEFI capable. Drive then has to be gpt partitioned not MBR(msdos).

What video card/chip do you have. Often boot parameters needed to boot.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

    

 You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

   Convert Windows BIOS to UEFI - Also command line install of files to efi partition
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

---

### Post by bertmung on 2013-12-10
I orginally thought that the flashing white line meant that the install was stalled. I waited a little longer and sure enough the live pen drive boots in what my motherboard calls "legacy" mode. From there installation of 13.10 was as painless as usual. 

UEFI is a big improvement in speed. Booting that way spoiled me. Just turns out it's useless for my current situation. It would come in handy if I didn't need to keep Windows for a printer that doesn't support Linux at one of my work locations.

Thanks oldfred and fantab!

---

