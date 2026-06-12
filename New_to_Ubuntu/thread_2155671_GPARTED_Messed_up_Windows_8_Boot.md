---
title: "GPARTED Messed up Windows 8 Boot"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by eklypze on 2013-06-19
Hi all,

I am currently dual-booting Windows 7/8 and was going to wipe out my Windows 7 partition completely to make room for Ubuntu 13.04. I deleted the Windows 7 partition and moved my Windows 8 to the left and resized it to cover all unallocated space. The problem is now my Windows 8 is stuck in a boot loop which says "Preparing Automatic Repair", "Diagnosing your PC" and then states that it is unable to automatically repair my PC. I am assuming I messed up the boot somehow and did not save a log, screenshot or anything so I'm feeling really hopeless now that I wasn't careful before resizing/moving my partitions. When loading up the live CD, I notice that all my files from Windows 8 still seem to be intact, is there any way I can fix my boot problems without reformatting the system?

I have tried using the Windows 8 disk, however I cannot "chkdsk" as it says it cannot lock the disk, the disk is write protected.

If it matters, the current layout of my disk is:
/dev/sda1 ntfs Recovery 14.84GB diag
unallocated 1MB
/dev/sda2 ntfs System Reserved 100MB boot
/dev/sda4 ntfs 683.69GB
unallocated 2.87MB

Thanks in advance.

---

### Post by MidnightGrey on 2013-06-19
Hi eklypze,

It looks like you haven't installed ubuntu yet, and are still using the Windows MBR (Master Boot Record).

I want to say going ahead and installing ubuntu will override the MBR with GRUB which will recognise your new Windows 8 location and this should solve your problem. But I dont have enough experience with Windows 8 to say that with certainty.

---

### Post by eklypze on 2013-06-19
Thank you for your prompt reply.

I have not yet installed Ubuntu, as I was afraid that doing so would further complicate issues and make my data unrecoverable. I have, however, tried using Boot Disk Repair to attempt to solve any boot/MBR issues. Unfortunately, it brought me back to the same boot loop and seems like it had no effect.

---

### Post by MidnightGrey on 2013-06-19
you can try using [boot repair](https://help.ubuntu.com/community/Boot-Repair) but again this will just replace MBR with GRUB.

---

### Post by eklypze on 2013-06-19
I have tried the boot repair tool with recommended settings, and here is the paste link I received if it helps at all:
[http://paste.ubuntu.com/5779447/](http://paste.ubuntu.com/5779447/)

---

### Post by MidnightGrey on 2013-06-19
but did it fix the boot issue?

---

### Post by eklypze on 2013-06-19
No, it seems to be doing the same thing. "Preparing Automatic Repair", "Diagnosing your PC" and then states that it is unable to automatically repair my PC.

---

### Post by westie457 on 2013-06-19
After the automatic repair has not worked are you given the option to try other ways to fix Windows?

You need to get to a Command Prompt. Once there the first command to run is chkdsk /f wait for it to finish.

This is necessary because the start point of the partition is not in the right place.

After the chkdsk has run be aware that it still might not boot. Am researching whether the Windows 7 fixboot commands will work with Windows 8

Had a look and found this. [http://www.techspot.com/guides/630-windows-8-boot-fix/](http://www.techspot.com/guides/630-windows-8-boot-fix/)

A guide to fixing the Boot record for Windows 8.

---

### Post by eklypze on 2013-06-19
After the automatic repair, it allows me to access Advanced Options, however it seems to be the Windows 7 recovery partition (which may not work with Windows 8). Thus I tried to use the Windows 8 CD instead, and going to Automatic Repair gives an error stating that you cannot use this function with the current OS (detected as Windows 8 Pro with Media Center). I have tried chkdsk /f, however it says it cannot lock the disk and that it is write protected. I then tried chkdsk C: /f which fixed a bunch of errors but still didn't boot, then chkdsk D: /f which ran in a matter of seconds with no issues.

I have tried the steps in the link you have just posted but /scanos and /rebuildbcd have detected 0 Windows installations now. Following the article to using "bcdedit", it appears that my list of items do not match as described in the text.

I also noticed that after Automatic Repair fails from the Windows 7 recovery partition, I can go to "Continue into another operating system" and select "Windows 7" and it will load up until the login screen of Windows 8 (without images or special effects). However, after attempting to log in the system will be stuck in a loading loop and never actually advance into the actual operating system (maybe it thinks we're still in Windows 7?).

---

### Post by westie457 on 2013-06-19
Which Windows OS was installed first, 7 or 8?

Are you 100% sure you deleted the Windows 7 partition?

Windows install disks will only repair the version that is installed. That is Windows 7 for 7 and Windows 8 for 8 as far as I know.

Now would be a good time to back up your personal data to an external drive if you have not already done a back up.

Regardless of which partition got deleted the problems are 1: the partition got resized which should cause Windows to force its own chkdsk

and 2: possibly the start point of a partition got changed which is causing the Boot loop.

Double check which version is installed and repair that particular one using the correct install disk.

---

### Post by newb85 on 2013-06-19
> **westie457 said:**
> and 2: possibly the start point of a partition got changed which is causing the Boot loop.

Yup, the OP stated that they moved the Win8 partition to the left after deleting the Win7 partition.  (Which probably means Win7 was installed first.  ;))

---

### Post by eklypze on 2013-06-19
> **westie457 said:**
> Which Windows OS was installed first, 7 or 8?

Are you 100% sure you deleted the Windows 7 partition?

Windows install disks will only repair the version that is installed. That is Windows 7 for 7 and Windows 8 for 8 as far as I know.

Now would be a good time to back up your personal data to an external drive if you have not already done a back up.

Regardless of which partition got deleted the problems are 1: the partition got resized which should cause Windows to force its own chkdsk

and 2: possibly the start point of a partition got changed which is causing the Boot loop.

Double check which version is installed and repair that particular one using the correct install disk.

Windows 7 was installed first, I already have my files backed up but if possible I'd like to resolve this without a reformat (unless absolutely necessary of course). I am sure that I deleted the Windows 7 partition, however it seems that I left the Windows 7 recovery partition intact. I tried deleting the recovery partition as well, so that I would only be left with the "System Reserved" (100MB) partition, which I assume is for booting Windows 8. I then tried the "chkdsk /f" on the Windows 8 CD, then Automatic Repair.

I figured I would have tried MidnightGrey's suggestions of installing Ubuntu to detect the Windows 8 partition, however now I am faced upon an error in GParted stating that my entire hard disk "/dev/sda" is unallocated, with the error "Can't have overlapping partitions".

Any ideas? :confused:

---

### Post by oldfred on 2013-06-19
I think you have two issues.

One is that all boot files for multiple installs of Windows are in the first install. Or Windows 8 copied its boot files to the partition with the boot flag or your Windows 7 and took over booting but from your Windows 7 partition. And now your Windows 8 has no boot files.
You also may need to add boot flag to the Windows 8 partition so repairs can be made, but you need a Windows 8 repairCD.

Also Windows 8 is always hibernated, so it need hibernation turned off before any major system change. And resizing a NTFS partition requires chkdsk to reset NTFS partition boot sector which must have same start and size info as partition table.

Is Windows 8 in a primary partition. Windows only boots from primary partitions.

While Vista, still the same for all Windows with BIOS & MBR partitioning - not for UEFI.
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

