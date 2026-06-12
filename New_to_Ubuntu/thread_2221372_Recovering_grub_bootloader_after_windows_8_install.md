---
title: "Recovering grub bootloader after windows 8 install"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by storm5 on 2014-05-01
hey guys,
I'm new here, and I'm a new ubuntu user as well. 

I have split my SSD into two partitions, installed ubuntu on one and then windows 8 on the other.  Ubuntu was good and working before the windows install.  Now it boots directly to windows, with no grub menu.  I tried reinstalling grub directly

```
sudo grub-install /dev/sda
```
```
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
```

Then I tried using boot-repair a few times, which didnt work. My most recent summary is located here:

[http://paste.ubuntu.com/7376238/](http://paste.ubuntu.com/7376238/)

I even tried reinstalling ubuntu entirely to no avail

Any ideas on what to try next?
When I installed ubuntu, I used '/' as the mount point, could this be a problem?
I can reinstall ubuntu from scratch, but I'd like to avoid reinstalling windows.

---

### Post by PapaNerd on 2014-05-01
Windoze is well known for not respecting other operating systems.  Therefore, when setting up a dual boot system, one needs to install Windoze first and then Linux.  Completely reinstalling Ubuntu should solve your problem.

---

### Post by oldfred on 2014-05-01
Your have two drives, one with MBR, so Windows only boots with BIOS. And  one with gpt partitioning so Windows only boots with UEFI.
Both Ubuntu & Windows only boot from MBR(msdos) drives with BIOS boot mode.
Windows will only boot from gpt with UEFI.
Ubuntu can boot from gpt with either UEFI or BIOS if correct supporting partitions are on drive.

UEFI and BIOS are not compatible, so from grub menu you cannot boot another in the different boot mode.
Only from UEFI/BIOS menu can you then boot systems installed in  different modes. And some systems require you to turn on/off BIOS or  UEFI.

And even if Widows 8 is in BIOS boot mode, you still need to remove the always on hibernation or fast boot.

It looks like SSD is the BIOS drive.

---

### Post by storm5 on 2014-05-02
yea, the SSD is split between an NTFS parittion for windows and and EXT4 partition for ubuntu.  The other drive is unbootable, so seems irrelevant to me (is it?).
ok, I tried fiddling with the setting on boot repair and now my windows boot isn't working.  The windows logo shows up, but triggers some error and wont open up all the way.
the up to date paste is now 
[URL="http://paste.ubuntu.com/7376238/"]http://paste.ubuntu.com/7377367/
[/URL]
I partially understand what your saying, but I don't get what to do next based on your info.

Edit: windows did have fast-boot disabled
I tried reinstalling ubuntu fresh and it didn't fix the issue.  I added a 100mb partition for the bootloader (/sda1) . I'm not really clear on what I should be using for mount points.  I mounted the 100mb partition at /boot, and the main partition at /.  Is that correct?
And when the installer asks which device to put the bootloader, should I be sending that to /sda or /sda1?

---

### Post by mansonfan78 on 2014-05-02
Well, you don't really need a separate boot partition (it's just a holdover from years ago when it was necessary).  The bootloader should be installed on sda (the mbr of the drive).  There are many issues with dual booting with Windows 8, it doesn't work for a lot of people.  You might be better off trying to install Ubuntu to a completely different drive than windows, instead of a partition on the same drive.

---

### Post by Gone fishing on 2014-05-02
Is the set up to boot MBR legacy mode or EFI? In system BIOS what happens if you force it to boot legacy MBR

---

### Post by oldfred on 2014-05-02
I think your hard drive may be bootable with UEFI turned on.

But your SSD is BIOS mode, unless you want to reinstall Windows. Once drive is partitioned to MBR, both Windows and Ubuntu can only boot in BIOS mode.
How you boot install media for both Windows & Ubuntu either UEFI or BIOS is how it installs. From UEFI menu your flash drive should be shown twice, once UEFI device and once just as device. Labels are not always easy to understand.

Some have confusion between what is a boot partition and gparted added to that.

In BIOS Windows uses a boot flag (active partition) to know which MBR partition has more boot code. Windows 7 and later normally creates a Boot partition (with boot flag) that is about 100MB. It has boot files & recovery (repair) code and is hidden. Windows does that so you can encrypt main install as boot files cannot be encrypted.
Grub does not use boot flag, but a few BIOS need to see a boot flag to even let anything boot, so we still suggest one on a primary partition.

In UEFI gparted used  the boot flag to assign the GUID to the FAT32 formatted partition that is the efi partition. If you use other tools like gdisk you do not assign a boot flag but give it a code of ef00, but that still is to assign a very long GUID code to that partition.
All systems with UEFI have boot code in the efi partition and each creates its own folder with its boot code. Somewhat like having multiple MBRs, one for each installed system.

With Ubuntu you can create a boot partition, but most desktops do not need one. Some servers or server type installs with RAID or LVM and particularly full drive encryption need a boot partition. 

You have to set in UEFI/BIOS to boot in BIOS mode from SSD drive. Right now you only have Windows in MBR so that is all that will boot. You may need to use f8 to run repairs.

It looks like you have converted Ubuntu in BIOS mode to UEFI. I have only seen one other configured like you have and thought it would not work. But I guess once you boot in UEFI from gpt drive it must not matter that Ubuntu is in a MBR partition. You must have booted Boot-Repair in UEFI mode so it converted install to UEFI boot from efi partition on hard drive. It also run its 'buggy' UEFI fix that renames the Windows efi file in the efi partition. Best to undo that and then you Windows on hard drive may work from UEFI menu.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

You also should use Boot-Repair to convert Ubuntu install from UEFI back to BIOS boot. And after you get Windows booting in BIOS mode from SSD reinstall grub to MBR of SSD and set it as first in boot order.
But grub only boots working Windows, so you need to make Windows repairs first.

It really is better and less confusing if both drives are BIOS/MBR or both drives UEFI/gpt. Then you can set system in one mode. BIOS is the old better understood system, UEFI is new and all pre-installed Windows 8 systems are UEFI. Eventually new hardware may not have BIOS based drivers and you will have to use UEFI, but most if not everything currently still works in BIOS mode.

---

### Post by storm5 on 2014-05-02
Ok, I'm trying that now.  My HDD is unbootable because it is in an ODD slot on the motherboard, and for some reason my BIOS does not recognize anything there (mounts fine once the OS is booted).  Can the GPT partition on this different disk really affect the boot sequence?

---

### Post by oldfred on 2014-05-02
I do not know your system, whats an ODD slot.
Some computers boot from just about anything you can plug in. Others are more limited.
I only have BIOS, but have used gpt partitioning on my 160GB drive since 10.10 and on my SSD since 12.04.

Newer Windows read gpt partitions from BIOS boot, but only boot from gpt with UEFI.
Old XP will not even read a gpt partitioned drive.

---

### Post by storm5 on 2014-05-02
ODD is the optical drive, I removed the optical drive to make room. My computer will not boot from that slot.  

i couldn't fix windows so I wiped everything and did a clean install, windows and then ubuntu without using the separate boot partition.  The grub menu loaded, and I could enter ubuntu.  But when I selected the windows option, it just hanged there and never booted. I ran boot repair, and now the grub menu fails to open.  It throws an error, /boot/grub/i386-PC/normal.mod not found.  I ran boot repair again disabling the "backup and rename" option, and the status is the same.  My current paste is:
paste.ubuntu.com/7383325
I noticed at the end of the boot-repair sequence it said to make sure the bios boots from:
sdb2/EFI/ubuntu/shimx64.efi

which makes no sense, because the sdb drive is not bootable.  I'm going to try deleting all the old windows partitions on /sdb/ and running boot repair again.

---

### Post by oldfred on 2014-05-02
Your new installs in sda are BIOS boot with MBR(msdos) partitioning.
But your install in sdb is UEFI.
So you booted Boot-Repair in UEFI mode and it converted the Ubuntu install in sda, to UEFI booting from the efi partition in sdb. It now has the efi partition refered to in fstab.

If you boot Boot-Repair in BIOS mode, uninstall grub-efi and install grub-pc and install grub2's boot loader to the MBR of sda, it should work.
You also show a grub installed to the PBR or partition boot sector of sda1. That will not boot anything, but is otherwise unused space so not an issue if grub is correctly installed to MBR of sda.

---

