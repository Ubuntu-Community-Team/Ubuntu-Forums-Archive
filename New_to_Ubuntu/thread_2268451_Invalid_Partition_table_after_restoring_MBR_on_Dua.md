---
title: "Invalid Partition table after restoring MBR on Dual boot Windows 7 and Ubuntu 14.04.2"
date: 2015-03-09
forum: New to Ubuntu
---

### Post by kvs on 2015-03-09
Hi, I seem to be stuck in a bit of a mess. I had Windows 7 installed on my Dell Latitude E7440 laptop, and I installed ubuntu by creating a separate partition for it.
After installation, it booted right into Ubuntu. If I changed to UEFI boot, it showed "No bootable devices found."

First I ran boot-repair and selected the recommended repair option. The resultant file is at [http://paste.ubuntu.com/10566661/](http://paste.ubuntu.com/10566661/)
I should also mention that boot-repair gave me the following warning when I ran it:

[COLOR=#000000][FONT=Calibri]"The boot files of [The OS now in use - Ubuntu 14.04.2 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)"[/FONT][/COLOR]

I chose to ignore this suggestion. Also, my fstab -l output contained the following:

"partition does not start on physical sector boundary" and "Partition table entries are not in disk order". I ignored this too.

Then, after restarting, I still couldn't boot into windows. However, I saw a grub after booting which allowed me to select from some options. Ubuntu was listed but windows was not listed in the options.
I then ran os-prober on ubuntu and it did not list anything.

I assumed there was something wrong with the windows MBR, so I ran boot-repair again and selected the "Restore MBR" option as suggested here : [http://askubuntu.com/questions/326532/how-to-fix-the-mbr-for-windows-7](http://askubuntu.com/questions/326532/how-to-fix-the-mbr-for-windows-7)
The result of this boot-repair is at [COLOR=#000000][FONT=Calibri]http://paste.ubuntu.com/10566755/

Now when I select legacy boot, I get "Invalid Partition Table". UEFI boot still gives "No bootable devices found."

Any help as to what I can try now would be appreciated. Do you think that the warnings I ignored about the partition table entries not being in disk order could be causing this issue?
[/FONT][/COLOR]

---

### Post by kvs on 2015-03-09
Some more information:
Now, on running boot repair using a live USB and choosing "recommended repair", I get the following message:

"The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB-250MB, start of the disk, boot flag). Do you want to continue?"

---

### Post by ajgreeny on 2015-03-09
You have run up against the problem of having one OS, Windows probably, installed in UEFI mode, and the second, Ubuntu I presume, in legacy MBR mode which will not work as you want it to, I'm afraid, though there is no UEFI boot showing in either of your two reports, and you certainly have no GPT partitions which are needed for UEFI to work.  Also in the second report it shows grub removed from the MBR of /dev/sda, not surprising as you have restored the MBR.

Have a look at these two sites which may help you more, and hopefully **oldfred** will chance upon this thread and be able to help you more, he being the UEFI guru of this forum.  I can usually manage single OS installation problems but as I have not run Windows for about 8 years, I am lost with dual booting.
[UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295")
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Those warnings you saw are not something that is of particular importance on a modern computer but date back to previous times and hardware, so I think you were correct to ignore them, but wait for oldfred; as I say, he is more likely to be able to help you properly.

---

### Post by oldfred on 2015-03-09
You are only showing two NTFS partitions and MBR partitioning.
Windows has to have the efi partition and a system reserved partition with gpt partitioning to be in UEFI mode. 
So even if your hardware is UEFI, you only have a BIOS/MBR system as configured. If you want UEFI, you have to totally reinstall both Window & Ubuntu with conversion of drive to gpt partitioning.

Scripts are not showing/mounting NTFS partitions. That can be from hibernation or needing chkdsk. But you can only fix those issues from a Windows repair console, either f8 on boot or your Windows installer, or a separate Windows repair CD or flash drive.

I have yet to see any newer UEFI/BIOS system have issue with far from start of drive issue. That message is for older systems, so separate /boot not recommended.

---

### Post by kvs on 2015-03-09
Thanks a lot oldfred and ajgreeny. I really appreciate both of you helping me out here.

I have a question though:

To fix the MBR issue, on the windows side I should run chkdsk from a repair CD or console, but to fix from the ubuntu side, should I do something? I mean, earlier it was booting ubuntu and not showing windows in grub, but now on trying to boot ubuntu it just shows "Invalid partition table" (even after running recommended repair from boot-repair)

---

### Post by oldfred on 2015-03-09
Part of grub is a search by UUID to find the correct partition, but if it cannot parse the NTFS partition to know it is not a Linux partition, it may be giving the error. So fixing Windows NTFS partition may fix grub. 
You could also in grub menu delete the search by line and see if it boots. It has two ways to set the root partitions, one fixed that normally should be correct, but then a review with the search by UUID to make sure you have correct partition. Either fixed setting or search should work without the other.

---

### Post by LostFarmer on 2015-03-09
Do not know just what is going on but looking at your pastbin line 370 , your Volume boot record data for sda1 and sda2 are totolly wrong and would never be able to boot into Win 7.  Possibly the reason for the "Invalid partition table" error. Would suspect that the start sector listed for the 2 partitions are wrong.  I do not know what to say on fixing problem, mybe "oldfred" might have an idea.

---

### Post by oldfred on 2015-03-10
As Lost Farmer points out the PBR partition boot sector or volume boot sector is not a standard NTFS type. 
I then am not sure chkdsk will fix it as it will not see the partition as NTFS.

NTFS does save a backup and if only damaged once, you can restore backup with testdisk. Or use testdisk to create a default NTFS PBR, but I think it is the old XP type, but chkdsk from Windows 7 will convert it back to the correct type. 

Testdisk is in repository or in many Linux repair disks. You can just install into Ubuntu live installer.

 As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

        select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

---

