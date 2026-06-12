---
title: "Does Ubuntu detect my hard drive?"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by dewrondewron on 2012-01-17
Greetings.
I have just finished my first build. ASUS P8P67 mobo; i7-2600 cpu; GTX55 Ti graphics card; Seagate Barracuda Green ST2000DL003 2TB hdd; IHAS424-98 DVD+/-RW. Has a 550 w PSU.
I want to use Linux and only Linux as my OS. System fired up just fine, BIOS recognized drives, established boot order, etc. Set SATA configuration.
Tried installing 11.10 64 bit from a bootable USB. On the 'Insallation type' screen, all buttons are inactive, the bar for the 'device for boot loader installation:' reads /dev/sda' and cannot be changed. Upon pressing 'Install now' I receive the '[COLOR=Red]No root file system is defined. Please correct this from the partitioning menu[/COLOR]'. I've also made and attempted USB's for 10.04(LTS) and 11.10 32 bit with identical results. 
My ASUS support disk shows a HDD unlocking utility (for MS), can this be an issue. I'm sure not, I see plenty of threads from users running the Seagate in the forums, and I feel like it's just some boneheaded oversight on my part.
 P.S. I've gone through all SATA settings in BIOS- to no avail.
Let me know if more info is needed. Thanks for your attention.

---

### Post by Double.J on 2012-01-17
Hi there! Welcome to the forums! 

Can't say I've had this issue mystelf.. if you select "try" rather than "install" on the live usb, then press the windows key once you're in and then type "gparted" are you able to see and edit your partitions this way?

---

### Post by cortman on 2012-01-17
Why not try a live CD?

---

### Post by dewrondewron on 2012-01-17
This command is reading the usb drive that I am booting from; i.e.  
/dev/sda1  fat32 /cdrom   PENDRIVE      7.55 GiB     724.62MiB(used)   6.84 GiB(unused)  boot, lba

---

### Post by dewrondewron on 2012-01-17
I will burn a live CD and give it a shot

After burning live CD and booting up with it, I went to 'try' again, went to console and gave 'gparted' command. This time I got an all-hot-buttons-inactive dialog box with banner at the bottom which reads 'no devices detected". So now it's on from here...
Many thanks, gnu/minow and Cortman, I didn't know where to start

---

### Post by cortman on 2012-01-18
> **dewrondewron said:**
> I will burn a live CD and give it a shot

After burning live CD and booting up with it, I went to 'try' again, went to console and gave 'gparted' command. This time I got an all-hot-buttons-inactive dialog box with banner at the bottom which reads 'no devices detected". So now it's on from here...
Many thanks, gnu/minow and Cortman, I didn't know where to start

Hm... What is the nature of the "unlocking" utility?

---

### Post by oldfred on 2012-01-18
With manual partitioning you have to specify which partition is / (root) with a 2TB drive you should just create a 25GB or so / partition and then have a larger /home. There was a bug in grub that it would not boot from very large / partitions.

If you have a 2TB drive the auto installer will default to gpt not MBR. Also if you have an i7, your motherboard probably has UEFI/BIOS. Not sure how the installer knows if UEFI mode or not. But UEFI seems to look for the efi partition and if no boot files found then it uses MBR to try to boot.

If also booting Windows you need to boot with UEFI if partitions are gpt. 

Partitioning in advance is always better, but you will need to know if UEFI or BIOS. I prefer gpt but do not boot Windows on any gpt drive. 

IF in BIOS
If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition at the beginning of the drive. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

IF UEFI, your first partition must be the efi partition.

I do not have UEFi but on new drives I leave room for efi and bios_grub.
Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
To be safe, create both of these partitions, in addition to your regular Linux partitions. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

---

### Post by dewrondewron on 2012-01-19
Thanks very much, Fred. These are very encouraging. Two hard days at work, and I'll try this on Saturday

---

