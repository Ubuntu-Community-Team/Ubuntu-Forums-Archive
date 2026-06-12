---
title: "Guide for Installing Ubuntu"
date: 2014-01-12
forum: New to Ubuntu
---

### Post by just_me76570 on 2014-01-12
[FONT=century gothic]Hello Im, Windows user and i want to switch into Ubuntu without Removing Windows ,I want to Install Ubuntu in my made partition but i Don't know how todo that :confused:  I wand to install Ubuntu in "L: "Drive i see some Tutorial about installing ubuntu but im still confused about that , can someone guide me installing ubuntu. and what is ```
"SWAP" , "/" and "Exp4" 
``` [/FONT]:confused:[FONT=century gothic]

```
L: Drive Free Space "243GB" 
BIOS MODE: UEFI 
```
[/FONT]

---

### Post by nilla78ro on 2014-01-12
i think easier way is to delete the "L:" partition an install the ubuntu into a free space.
more details : [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by 3rdalbum on 2014-01-12
> **just_me76570 said:**
> [FONT=century gothic]Hello Im, Windows user and i want to switch into Ubuntu without Removing Windows ,I want to Install Ubuntu in my made partition but i Don't know how todo that :confused:  I wand to install Ubuntu in "L: "Drive i see some Tutorial about installing ubuntu but im still confused about that , can someone guide me installing ubuntu. and what is ```
"SWAP" , "/" and "Exp4" 
``` [/FONT]:confused:[FONT=century gothic]

```
L: Drive Free Space "243GB" 
BIOS MODE: UEFI 
```
[/FONT]

When it asks you how you want to install Ubuntu (erase Windows, install side-by-side, etc) choose the option at the bottom of the list: "Something Else".

Delete the partition that you created for Ubuntu (Windows calls it L: but Ubuntu calls it something different, you'll be able to tell it by the size and where it is on the disk though).

If you have less than 2 GiB of RAM, create a 2 GiB partition in the newly-freed space and use it as SWAP. If your main memory starts getting low, the system can "swap" things between disk and main memory. Basically, it allows you to use more RAM than you actually have.

In the remaining free space (or in the whole free space, if you have 2 GiB of RAM or more), create one partition. Its mount point should be "/" (this is where Ubuntu will be installed to) and its filesystem type should be "Ext4".

You can now proceed with the installation.

---

### Post by just_me76570 on 2014-01-12
> **3rdalbum said:**
> When it asks you how you want to install Ubuntu (erase Windows, install side-by-side, etc) choose the option at the bottom of the list: "Something Else".

Delete the partition that you created for Ubuntu (Windows calls it L: but Ubuntu calls it something different, you'll be able to tell it by the size and where it is on the disk though).

If you have less than 2 GiB of RAM, create a 2 GiB partition in the newly-freed space and use it as SWAP. If your main memory starts getting low, the system can "swap" things between disk and main memory. Basically, it allows you to use more RAM than you actually have.

In the remaining free space (or in the whole free space, if you have 2 GiB of RAM or more), create one partition. Its mount point should be "/" (this is where Ubuntu will be installed to) and its filesystem type should be "Ext4".

You can now proceed with the installation.
[FONT=century gothic]

Thank you, BTW How can i Delete my partition that i created For Ubuntu? can you post a picture or tutorial on how to delete it (Sorry sir i don't know how to do that [/FONT]](*,))

---

### Post by nilla78ro on 2014-01-12
[COLOR=#454545][FONT=WOL_Reg][B]you can delte it fom windows:
To delete a partition[/B]


[LIST]
[*]Open Computer Management by clicking the [FONT=WOL_Bold]**Start**[/FONT] button [IMG]http://res2.windows.microsoft.com/resbox/en/windows%207/main/4f6cbd09-148c-4dd8-b1f2-48f232a2fd33_818.jpg[/IMG], clicking [FONT=WOL_Bold]**Control Panel**[/FONT], clicking [FONT=WOL_Bold]**System and Security**[/FONT], clicking [FONT=WOL_Bold]**Administrative Tools**[/FONT], and then double-clicking [FONT=WOL_Bold]**Computer Management**[/FONT].* [IMG]http://res2.windows.microsoft.com/resbox/en/windows%207/main/18abb370-ac1e-4b6b-b663-e028a75bf05b_48.jpg[/IMG] If you're prompted for an administrator password or confirmation, type the password or provide confirmation.
[*]In the left pane, under [FONT=WOL_Bold]**Storage**[/FONT], click [FONT=WOL_Bold]**Disk Management**[/FONT].
[*]Right-click the volume, such as a partition or logical drive, that you want to delete, and then click [FONT=WOL_Bold]**Delete Volume**[/FONT].
[*]Click [FONT=WOL_Bold]**Yes**[/FONT] to delete the volume.
[/LIST]

[/FONT][/COLOR]

---

### Post by Impavidus on 2014-01-12
When you install Ubuntu (and select the "something else" option), you'll get to a screen where you can change the partitioning of the drive. It's pretty much self explanatory. Just make sure you only delete the partition that you had reserved for Ubuntu and create the new partitions.

There is even a safer and easier way. Using the Windows partitioning tool (I don't know how it is called), you can delete the L partition, leaving unallocated disk space. The Windows partitioning tool doesn't know how to create ext4 or swap partitions, so you'll leave that to the Ubuntu installer. Next boot from the live dvd/usb and run the installer. It should detect the unallocated space and if you choose to install alongside Windows it should install there, creating the partitions you need for Ubuntu. The installer does a quite decent job when creating partitions.

---

### Post by just_me76570 on 2014-01-13
if i choose Install ubuntu along side in Windows but i have a UEFI Bios it's will Work even i dont Create a Partition for UEFI? and if i Choose the Install Ubuntu along side W/ windows , and if i Boot windows Can windows can see the files from Ubuntu?



(Sorry for my english im not good in english)

---

### Post by oldfred on 2014-01-13
Even if hardware is UEFI, is Windows installed in UEFI mode or BIOS boot mode? You need to install Ubuntu in same boot mode. 
If BIOS you also then have MBR(msdos) partitioning and the 4 primary partition limit. 
If UEFI then no limit on partitions, but UEFI is relatively new. 
What system and what version of Windows?

Post this to see partitions. If you have a 100MB sys and main Windows that probably is BIOS. If you have a FAT32 boot partition that is probably UEFI.
sudo parted -l

---

### Post by just_me76570 on 2014-01-17
This is my Disk management :p  BTW what is the difference of "Install Along side and Something Else?"

1.and if i Choose Install Along side windows, If i Boot windows can windows access/view my file in from Ubuntu?

2.and if i  Choose Something Else, If i Boot windows can windows access or view my file in from Ubuntu?

3. and if i Choose Along side windows, Should i Create a EFI Partition or not? but i have a EFI partition :D

4. and if i Choose Something Else, Should i Create a EFI Partition or not? but i have a EFI partition or i will use the EFI partition from Windows  ;)


(Sorry for crazy question)
[CENTER]

[IMG]https://fbcdn-sphotos-c-a.akamaihd.net/hphotos-ak-prn1/t1/1535512_276559745834081_515475264_n.jpg[/IMG][/CENTER]

---

### Post by oldfred on 2014-01-17
The auto install options just create / (root) and swap with automatic sizes based on the unallocated space you have. Something Else or manual install,  installs the same system, but you have to create (or choose if manually created with gparted before) partition, choose its format like ext4 and choose mount point or /, /home etc. Swap has no format.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Windows will not read Linux formatted partitions and all system partitions including /home must be Linux formatted. But Linux reads NTFS formatted partitions, but usually best not to write into Windows system partition. So create a shared NTFS data partition for read/write.

You must have the always on hibernation or fast boot off, better to have secure boot off.
Make a Windows repair flash drive and backup all of Windows and efi partition. You can only have one efi partition per hard drive.
More details (too much but not all applies to all systems) in link in my signature.

---

