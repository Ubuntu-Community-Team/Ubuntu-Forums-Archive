---
title: "AC adapter source not supported after installing ubuntu"
date: 2020-09-01
forum: New to Ubuntu
---

### Post by rajan222 on 2020-09-01
Help, I have installed ubuntu but just after installing.
It is saying 'AC adaptar power source not supported' while booting. Help, 
It started saying 'estimating'  when i plugin power source.
This didnt happened before in windows 10. 
Please help

---

### Post by Autodave on 2020-09-01
Please give us some info on your equipment: make and model and if the AC adapter is a factory unit or aftermarket.  Also, what version of 'buntu did you install?

---

### Post by rajan222 on 2020-09-01
I am getting other problem also. 
I am running intel i7 10 gen , dell inspiron 3593 . That problem just vanishes , and other problem came. Please help, i am new to ubuntu and new laptop.

When i am booting ubuntu , it says 
"You need to load kernel first" , when i click enter and shows ubuntu option as usual but it didnt click and goes back to same 'load kernel first' thing,
after rebooting again shows 'initrms unpacking fail' then luckily it booted and came here. 
Please help, 
Dmidcode shows following information , 

# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.1 present.

Handle 0x0400, DMI type 4, 48 bytes
Processor Information
        Socket Designation: CPU 1
        Type: Central Processor
        Family: Core i7
        Manufacturer: Intel(R) Corporation
        ID: E5 06 07 00 FF FB EB BF
        Signature: Type 0, Family 6, Model 126, Stepping 5
        Flags:
                FPU (Floating-point unit on-chip)
                VME (Virtual mode extension)
                DE (Debugging extension)
                PSE (Page size extension)
                TSC (Time stamp counter)
                MSR (Model specific registers)
                PAE (Physical address extension)
                MCE (Machine check exception)
                CX8 (CMPXCHG8 instruction supported)
                APIC (On-chip APIC hardware supported)
                SEP (Fast system call)
                MTRR (Memory type range registers)
                PGE (Page global enable)
                MCA (Machine check architecture)
                CMOV (Conditional move instruction supported)
                PAT (Page attribute table)
                PSE-36 (36-bit page size extension)
                CLFSH (CLFLUSH instruction supported)
                DS (Debug store)
                ACPI (ACPI supported)
                MMX (MMX technology supported)
                FXSR (FXSAVE and FXSTOR instructions supported)
                SSE (Streaming SIMD extensions)
                SSE2 (Streaming SIMD extensions 2)
                SS (Self-snoop)
                HTT (Multi-threading)
                TM (Thermal monitor supported)
                PBE (Pending break enabled)
        Version: Intel(R) Core(TM) i7-1065G7 CPU @ 1.30GHz
        Voltage: 0.7 V
        External Clock: 100 MHz
        Max Speed: 1500 MHz
        Current Speed: 1500 MHz
        Status: Populated, Enabled
        Upgrade: Other
        L1 Cache Handle: 0x0701
        L2 Cache Handle: 0x0702
        L3 Cache Handle: 0x0703
        Serial Number: To Be Filled By O.E.M.
        Asset Tag: To Be Filled By O.E.M.
        Part Number: To Be Filled By O.E.M.
        Core Count: 4
:
        Core Enabled: 4
        Thread Count: 8
        Characteristics:
                64-bit capable
                Multi-Core
                Hardware Thread
                Execute Protection
                Enhanced Virtualization
                Power/Performance Control

Help!!

---

### Post by rajan222 on 2020-09-01
I am using latest 20.04 ubuntu.

---

### Post by rajan222 on 2020-09-01
for 'You need to load kernel first' I found this answer, 

  
          
                       If you get to a grub prompt, it means that grub can't find the boot files that it expects. The sequence of commands to load the files and boot when grub doesn't do that for you goes something like this. First, find all partitions that grub sees:
  grub> ls
(hd0) (hd0,msdos2) (hd0,msdos1)  This lists disks and partitions on the disks. One of these partitions holds your Linux system. Say it is (hd0,1). Then do:
  grub> set root=(hd0,1)
grub> linux /boot/vmlinuz-4.15.0-45-generic root=/dev/sda1  Replace (hd0,1), the version number and the partition (/dev/sda1) by what is valid for your system. In the case of vmlinuz you can just type vmlinuz- and press Tab.
  grub> initrd /boot/initrd.img-3.13.0-29-generic  The version string should be identical to the one for vmlinuz.
  grub> boot



also sir, when i was installing i had important files in another partition which i untouched it, while installing. But when i open that partition from ubuntu, I can only see, and command line says it is read only drive. Help how can i get rid. I have very important files in these. 

please could you tell how can i do that on my machine, 
before installing i had choosen  (root, home, ntfs(untouched), swap, efi ) partition,

---

### Post by CelticWarrior on 2020-09-01
Welcome.

For a proper dual-boot configuration in a modern computer alongside Windows 10 there are a few things you need to know before installing Ubuntu. Not knowing the basics is not an option, otherwise regrets, potential loss of data and unbootable OS/OSes ensues.

1. Things to do in Windows: Shrink one or more Windows partitions to make room for Ubuntu (unallocated space); install Windows updates and after that disable Fast Startup.
2. If you need to share files between OSes then PREFERABLY do it from a additional, NTFS formatted, data partition, NOT from the Windows system partition. With Fast Startup enabled NTFS (and other) partitions can only be mounted read-only because "Fast Startup" is actually hibernation and if hibernated Ubuntu cannot mount those partitions in a clean state, with write permissions. This is one of the reasons why disabling Fast Startup in Windows is always recommended and a must for multi-booting.
3. Any computer since 2012 at least, with Windows 8 or newer preinstalled, has the original OS in UEFI mode and GPT drives. Ubuntu should be installed in the same mode. Often better to just disable Legacy/CSM/"BIOS" mode in UEFI ("BIOS") settings. Make sure the USB installation media can boot in UEFI mode. Anything made by an exact copy from the ISO file (using DD) will boot either BIOS or UEFI; media made with Rufus in Windows depends on the Rufus' settings, you need to change the default to "UEFI/GPT" before burning the ISO.
4. In UEFI settings disable Secure Boot and Fast Boot (if applicable).

Now, in your previous post, the solution you say you have found isn't applicable to UEFI mode. First of all do the aforementioned changes in Windows and then open UEFI settings > Boot menu and make sure to select "Ubuntu" instead "Windows bootloader manager" ("Windows..." is the option you use if you want to boot Windows directly) so you boot to the Grub menu from where the default boot option will be Ubuntu but you can select Windows to boot Windows instead.

---

### Post by CelticWarrior on 2020-09-01
> [COLOR=#000000][INDENT]before installing i had choosen (root, home, ntfs(untouched), swap, efi ) partition,[/INDENT]


[/COLOR]


I would do a proper installation from scratch taking into account all I previously discussed, for better results. If you have partitions already, including a separated /home) you will have to choose "something else" during installation and manually select the partitions. Choose EFI as EFI partition, the root partition (/) and format it (backup any personal files you might have there already before re-installing Ubuntu, of course) and the /home partiton. Do NOT select any NTFS partition at this point!!! The existing NFTS partitions will be mounted like any other removable media in the installed Ubuntu in a normal session, they are NOT to be used in any way, shape or form, during the Ubuntu installation.

Also make sure you have the power supply connected before re-installing. You may also need to update UEFI and SSD firmware even if the computer is new off the shelf.

---

### Post by rajan222 on 2020-09-01
Hi @cleticwarrior, thank you for your idea. 
Sir, I have copied all  my files from that ntfs to root(/) disk, and can i format it using disks  from ubuntu , do this solve problem.
I have brand new laptop, which says it  fully support ubuntu, I havent installed windows along side with ubuntu ever, 

While  installing ubuntu had said to used secure boot , which was enabled in  bios  by default, and i used password to make secure boot. 
I have installed only ubuntu not any thing , only not touchong that another drive ntfs folder. 
My  uefi is already updated in latest version, just 2 days ago i had bought  this laptop, bios also seems like cool mouse and things.
Uefi is  already activated in it, I had looked before in diskpart in w10 that GPT  was enabled, then i seen tutorial to install and installed,

can i format NTFS partition,  would it solve my problem?
Help, Please help

---

### Post by CelticWarrior on 2020-09-01
If you don't want to keep Windows then you certainly can remove all NTFS partitions in any way it can be done. Then you may move and resize Ubuntu partitions, of course.

I wouldn't do it though. I would, if necessary, copy the personal files to external media and reinstall from scratch Ubuntu with the automatic "Erase and install..." option or manually with "something else" as described above.

---

### Post by rajan222 on 2020-09-01
Thank you. I have remove formatted ntfs to ext4 without reinstalling  ubuntu again because i have huge files and no external backup.

sir i have another last question, 

my disks partitions are

* filesystem partition 1 490mb fat -efi
* filesystem partition2 ext4 /
* filesystem partition3 ext4 /home
* filesystem partition5 ext4  mounted at /media/...
* filesystem partition4 Swap
* 3.7 gb free space,



can i extend swap area of that partition 4 to include 3.7gb, 
also could my problem would go in future, because my partition seems fine and perfect as usual partition?

Thank you for helping. :)

---

### Post by Impavidus on 2020-09-01
> **rajan222 said:**
> ... because i have huge files and no external backup.

Then don't be surprised when (not if) you lose your files. Without backups, you will lose your files one day. You know, hard drives fail, computers get stolen, people accidentally delete the wrong files or format the wrong partition, encryption keys get lost/forgotten etc.

As for your problem, we don't know much about it yet.

---

### Post by grahammechanical on 2020-09-01
> I have copied all  my files from that ntfs to root(/) disk

How did you do that if the NTFS partition was read only? I have a second question. Why do you keep changing the question you are asking for help for. If you have other questions it is best to put them in another post. To open another "thread" with a suitable title. We also like people to mark threads as "solved" if a solution is found. In this way we do not spend time reading through a thread only to find out that help is no longer needed.

Regarding NTFS formatted partitions and Ubuntu there is this

> For those using a desktop version of Ubuntu, or one  of its offical derivatives, the easiest and quickest way of mounting  NTFS or FAT32 partitions is from the file manager: Nautilus in Ubuntu,  Thunar in Xubuntu, Dolphin in Kubuntu and PCManFM in Lubuntu. Simply  look in the left pane of the file manager for the partition you wish to  mount and click on it - it will be mounted and its contents will show up  in the main pane. Partitions show with their labels if labelled, or  their size if not. 
Unless  you require your Windows partition - or a NTFS/FAT32 partition for data  shared with Windows - mounted every time you boot up for one of the  reasons given below, mounting from the file manager in this way should  suffice.

The source of this information is a little old

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

To answer another question. Ubuntu 20.04 does not use a swap partition but a swap file instead. This change happened with Ubuntu 17.04

[https://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files](https://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files)

Regards

---

