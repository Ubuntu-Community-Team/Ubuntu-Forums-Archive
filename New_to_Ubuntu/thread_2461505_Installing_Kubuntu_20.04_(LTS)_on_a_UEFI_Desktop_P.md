---
title: "Installing Kubuntu 20.04 (LTS) on a UEFI Desktop PC"
date: 2021-05-01
forum: New to Ubuntu
---

### Post by martinjdz on 2021-05-01
I have been using Ubuntu 20.04 (LTS) with the KDE Desktop Environment on an older desktop PC that supports only **BIOS**.

I already understand how to partition the hard drive and install the Linux OS on a **BIOS** machine:


[LIST=1]
[*]Create a 500M-byte FAT32 **Primary** partition at the beginning of the drive.
[*]Create an extended partition for **SWAP**, **HOME**, and **ROOT**.
[*]Install the **GRUB** boot loader at the beginning of **ROOT**.
[/LIST]

Now, I am about to install Kubuntu on a newer PC supporting **UEFI**, and my hard drive will be formatted as **GPT**. I understand that there are no **Primary** and **Logical** partition types on a **GPT**-formatted drive. Therefore, I am uncertain about how to proceed. Please explain to me, briefly, how I should prepare the hard drive.


[LIST]
[*]Do I need another 500M-byte FAT32 partition at the beginning of the drive?
[*]Will **SWAP**, **HOME**, and **ROOT** each be a separate **GPT** partition?
[*]Will the boot loader still go onto **ROOT**?
[/LIST]

Thanks for you help.

---

### Post by CelticWarrior on 2021-05-01
> **martinjdz said:**
> 
I already understand how to partition the hard drive and install the Linux OS on a **BIOS** machine:


[LIST=1]
[*]Create a 500M-byte FAT32 **Primary** partition at the beginning of the drive.
[*]Create an extended partition for **SWAP**, **HOME**, and **ROOT**.
[*]Install the **GRUB** boot loader at the beginning of **ROOT**.
[/LIST]


Unfortunately no, you don't understand. Pretty much everything is wrong.
(1) A small FAT32 partition is required for UEFI, not BIOS. And the mention of "primary" makes sense only in "msdos" (or "dos" AKA "MBR") partitioning table which is somewhat associated with BIOS (and mandatory if dual-booting with Windows in BIOS mode; if installing Ubuntu or other Linux alone then there's no such restriction). 

(2) Again, "extended" points to MBR which has a limit of 4 primary partitions (or 3 primary partitions and 1 extended partition containing several logical partitions inside, if needed). Root (/) is obviously mandatory but a separated /home is optional. A separated swap is no longer needed either because Ubuntu uses a swapfile by default now. You would need to do a manual installation with "something else" in order to force the use of a swap partition.

(3) No, in BIOS/Legacy mode and MBR (the most typical setup), Grub is installed in the MBR!! If installing in BIOS/Legacy mode in a GPT drive then you would need a small (~1-2MB) unformatted "bios_grub" partition at the beginning of the drive and Grub would be installed there automatically. NEVER in a system partition!


For UEFI everything is so much simpler... Start with a GPT drive. You can use GParted in a live session, select the target drive and at the Devices menu > Create a new partition table... Select "GPT". Then make sure the installer was booted in UEFI mode - it's generally recommended to disable "Legacy"/CSM in the UEFI settings - and install as usual, either automatically where the installer creates the ESP (EFI System Partition, the small FAT32 partition at the beginning of the drive which has NOTHING to do with BIOS) and root, nothing else, or use something else to manually install with the required partitions and a separated /home if you so wish.

---

### Post by oldfred on 2021-05-01
How you boot install media UEFI or BIOS is then how it installs. So just be sure to boot in UEFI mode.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See install steps & lots of UEFI info in link in my signature. Much of it is for special cases which you can skip over.

---

### Post by martinjdz on 2021-05-02
In my BIOS/MBR installation, I let Kubuntu grab the whole drive and make most of the decisions. Kubuntu automatically created a 500M-byte Primary Partition and an extended partition. Since the OS install did this automatically, I assumed that this must be the correct procedure.

Regarding the installation of Grub, I told Kubuntu to install it on the MBR (as you recommend). However, according to **Grub Customizer**, the information is actually on the **ROOT**. I don't understand why. Anyway, I agree with you on this installation issue.

I understand most of what you said in you reply. However, there is still one issue that is still not clear to me. Should there be separate GPT partitions for different parts of the Kubuntu Linux OS (**HOME** and **ROOT)**? Or, does everything go into a single partition? That's what has me a little confused.

Thanks again.

---

### Post by tea for one on 2021-05-02
> **martinjdz said:**
>  However, there is still one issue that is still not clear to me. Should there be separate GPT partitions for different parts of the Kubuntu Linux OS (**HOME** and **ROOT)**? Or, does everything go into a single partition? That's what has me a little confused.

A separate partition for **home** is a [COLOR="#0000FF"]user[/COLOR] choice.

Having booted the live session in UEFI mode and after you have created a GPT partition table on your target drive, the installer will create automatically two partitions - EFI and Root (your home directories will be within root).

If you choose [COLOR="#0000FF"]something else[/COLOR] at the partitioning stage, then you can create 3 partitions - EFI, Root and a separate Home.

---

### Post by oldfred on 2021-05-02
Gpt is not a partition but how a drive is partitioned.
All partitions are either MBR or gpt.
But gpt does have what is called a protective MBR or one gpt partition entry in the MBR, just so old partition tools see the drive is partitioned and do not try to redo it without at least some warning.

MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record) & 
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012 and release of Windows 8. But it does allow a user to install in BIOS boot mode, but only to MBR partitioned drives.
Ubuntu will let you install in UEFI mode to MBR drives, but probably should not, or at least suggest gpt.

---

### Post by grahammechanical on 2021-05-02
> However, according to **Grub Customizer**, the information is actually on the **ROOT**. I don't understand why.

It is years since I last used Grub Customizer. So, I am guessing that Grub Customizer is referring to Grub configuration files and Grub utilities. They can be found at /boot/grub/. Think about the process that takes place.

We switch on. The motherboard goes through some Power On System Tests (POST) then the BIOS/UEFI system setting utility gives information as to what drive to look at to find a computer operating system. It finds a boot loader (Grub) which in turn loads the OS. Or, puts up a menu giving the user the option to load an OS of choice. If the Grub boot loader were in root the motherboard could not load Grub because it does not know where root is.

Grub looks to /boot/grub/ for its configuration files which it uses to build the boot menu and for the knowledge of where to find the Linux kernel.

I have a BIOS motherboard with both a MBR partitioned drive and a GPT partitioned drive.

On the MBR drive there is 2.1 MB of free space. That is where the working part of Grub goes. The GPT drive has 1 MB first partition labelled BIOS Boot. And that is where the working part of Grub goes when I install Linux on the GPT drive.

 A GPT drive on a UEFI motherboard would not have that BIOS Boot partition but one labelled EFI system partition. And the working part of Grub is put there. Unless, of course, the user installs in Legacy mode.

Regards

---

