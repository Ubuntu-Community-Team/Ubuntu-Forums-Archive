---
title: "problems during install of ubuntu 18.10"
date: 2018-11-17
forum: New to Ubuntu
---

### Post by jehtblack on 2018-11-17
Hi all,

I'm trying to install ubuntu but I keep running into issues when creating a new partition table.

I'm going through the typical install wizard style setup. I intend for ubuntu to occupy a hard drive to itself, I will have a windows install alongside it on a separate drive (already done, drives currently disconnected).
Every time I select the drive and either try to generate a new partition table or erase disk and install a dialogue appears to inform what will happen and this is where I'm stopped every time, I can't interact anymore at this stage.
The most it will do is occasionally highlight the buttons but will not click to continue or go back, I have no idea what is going on behind the scenes. The drive was used for a previous windows install but I've cleaned the drive in preparation for a linux install.

system details are:
amd fx-8350
gigabyte mobo (can't remember model number)
radeon r9 390
16gb ram

I've had the same issue during an attempted linux mint install, I've attempted the install on a spare drive I have with no luck there either.
If anyone is aware of this issue and can advice me I'd appreciate it.

---

### Post by oldfred on 2018-11-17
Did drive have RAID settings. Many Windows systems use Intel SRT or a RAID.
That can leave meta-data on a drive, even if erased.
Or does motherboard UEFI have drives set to RAID, they need to be AHCI.

Have you updated UEFI firmware?
       Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to AMD  boards.

---

### Post by jehtblack on 2018-11-18
I have no RAID settings on either the drive or motherboard.
I have no issues booting into the media.
I tried enabling IOMMU and attempting the install but ran into the same problem.

Meta data seems like a possible cause however I don't see why this would cause this particular problem.
Are there any steps I can try if this is the case ?

---

### Post by oldfred on 2018-11-18
You can run this. If drive is blank, it will not hurt anything. Only if actually RAID, would it cause issues.
I think they discontinured dmraid, but I do not know equivalent mdadm command.
       dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later. 
    
       sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb 

Update:
Found this:\
sudo mdadm --zero-superblock /dev/sda

You may have to install dmraid or mdadm, since not running raid.
 
Also if drive is SSD, that may need firmware update in addition to UEFI firmware updates.

---

### Post by jehtblack on 2018-11-24
Hi sorry for being so long I only just got a chance to try your suggestions, unfortunately they didn't work.
I've managed to get through the install by mounting the drive to virtual machine on virtualbox in windows.
I now have a ubuntu install that I can boot from though neither the windows boot manager nor grub recognise the other present OSes so I'll have to figure that out.

Thanks for the suggestions

---

