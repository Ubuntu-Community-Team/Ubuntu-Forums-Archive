---
title: "boot-repair cannot fix my boot loader(Ubuntu + Windows)"
date: 2020-12-19
forum: New to Ubuntu
---

### Post by qiuqiyuan on 2020-12-19
Hi Team, 
After I installed a NVME driver my machine can no-longer boot for both Ubuntu and Windows.

What I did:
- install a Samsung SSD nvme driver
- copy OS using Samsung data migration tool([https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)).


Prior to this, I was able to dual-boot. 
My theory is that because I have copied the Windows OS to the new SSD, the boot loader sees two identical copy of Windows with the same signature so it is confused. 

I have tried using boot-repair but it cannot solve my issue, the diagnose paste is: [https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)


I expect boot-repair will solve my problem but I am not sure what went wrong, here is the paste: [http://paste.ubuntu.com/p/SrNgFRDfgg/](http://paste.ubuntu.com/p/SrNgFRDfgg/)

Thanks in advance for any comments, really appreciate your time.

---

### Post by oldfred on 2020-12-20
Look at lines starting at 347.
You cannot have duplicate UUID nor GUID/partUUIDs.
Typically if you image copy a drive, you disconnect old drive or reformat it.

You also show Windows fast start up on/hibernation which needs to be off.
UUIDs are all the same, but some GUIDs are not. And two partitions have same GUID?
The Microsoft reserved partition is unformatted space and as such often confuses many partition tools, so that may be why GUIDs are the same on p3 & p4.

At minimum, try disconnecting sda.
Run Windows chkdsk on all NTFS partitions from your Windows repair/recovery drive and Linux e2fsck on all ext4 partitions from Ubuntu live installer.
I might try changing p3 with partition tools. Not sure if gparted will change GUID. But gdisk may. But gdisk is more for Linux.

GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html) & 
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
There are two GUID codes, one unique to each partition on one that defines type of partition.
Your p3 needs to be Microsoft system reserved and unique partUUID. 
[FONT=monospace][COLOR=#000000]lsblk -o +parttype,partuuid[/COLOR]

[/FONT]https://en.wikipedia.org/wiki/GUID_Partition_Table
Gparted uses flags (right click on partition) and gdisk uses 2 digit code to define partition type.

Depends on which drive you change GUIDs/UUIDs on. If sda removed and repairs done on NVMe drive, it may work. But then you need to change sda's GUID/partUUIDs & UUIDs or totally reformat drive.

Your UEFI boot entry uses the GUID/partUUID to know which ESP to boot from. So you need unique GUIDs for each drive's ESP. And then boot loaders must be configured to use those entries.

Not sure with Windows but probably a full set of Windows repairs to reinstall its boot loaders.
And with Ubuntu a total reinstall of grub after you changed GUIDs & UUIDs on NVMe drive. 
Or it may work with simple repairs if sda just removed.

Do not know best way to move Windows to new drive, but above issues are why I typically suggest a new install of Ubuntu & restore /home, list of installed apps and maybe some other data from your normal backup. As you still have old working drive, you both confirm standard backup procedure works and yet have old data to get anything your backup is missing. And no issues of duplicate GUIDs & UUIDs.

---

