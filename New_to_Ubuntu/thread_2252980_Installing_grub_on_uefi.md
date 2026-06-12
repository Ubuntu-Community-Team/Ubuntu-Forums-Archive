---
title: "Installing grub on uefi"
date: 2014-11-16
forum: New to Ubuntu
---

### Post by codetemplar on 2014-11-16
Hi all.
I have made a right pigs ear of my laptop. It came with win8 and I flushed it and put Ubuntu on. I had to disable uefi to install it as grub failed to install. Everything works ace but as I've disabled raid (fake raid) I have an unused partition which I want to put win7 on and dual boot. Problem is I'm going to have to turn uefi back on as win7 won't install otherwise. So I've turned uefi back on but now have nothing to boot. So I'm going to live boot from Ubuntu and reinstall grub on uefi and point it at my old ubuntu partition. Then install win 7.

1. Is what I'm doing even feasible?
2. If so, how am I going to install grub2 on uefi from live CD and point it at my ubuntu installation to boot?

Thanks for any help

---

### Post by yancek on 2014-11-16
I don't know what the problem was with your Ubuntu but, there are countless posts on these forums from users who have successfully installed Ubuntu with windows 8 using UEFI.  windows 7 can be installed in MBR or UEFI and I believe MBR is the default.  What happens when you try to boot the windows 7 installation medium.  I don't use UEFI but you might search the forums and find some workable suggestions.

---

### Post by oldfred on 2014-11-16
Better to have both systems in UEFI.
If system was RAID with 2 drives that was part of issue of installing grub as only server installer supports RAID.

Windows only boots from gpt partitioned drives with UEFI. And all pre-installed Windows 8 use UEFI with gpt partitioning. But Ubuntu may install in BIOS mode on a previous gpt partitioned drive, but then you cannot install Windows except in UEFI mode if drive is gpt.

Post this:
sudo parted -l

---

### Post by codetemplar on 2014-11-17
Model: ATA LITEONIT CMT-64L (scsi)
Disk /dev/sda: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name              Flags
 1      1049kB  59.7GB  59.7GB  ext4            Linux filesystem
 5      59.9GB  64.0GB  4103MB  linux-swap(v1)  Linux swap        boot


Model: ATA LITEONIT CMT-64L (scsi)
Disk /dev/sdb: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  106MB   105MB   ntfs         Microsoft basic data  msftdata
 2      106MB   64.0GB  63.9GB  ntfs         Microsoft basic data  msftdata


Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdc: 31.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  31.2GB  31.2GB  primary  fat32        boot, lba
 2      31.2GB  31.2GB  32.3kB  primary

I think the last is my lived. I have changed BIOS to uefi and turned secure boot on. Thanks for your help

---

### Post by codetemplar on 2014-11-17
I just tried boot repair and still nothings boots. Got the following URL from boot repair [http://paste.ubuntu.com/9061030/](http://paste.ubuntu.com/9061030/)

---

### Post by oldfred on 2014-11-17
You have Windows on sdb in BIOS boot mode, I think, as it does not have an efi partition nor the system reserved. And 100MB boot with main install is a typical BIOS/MBR install. 
But partition table is now gpt and Windows only boots in UEFI mode from a gpt partitioned drive.

You have Ubuntu on a gpt partitioned drive in sda. 
Ubuntu will boot from gpt  with either UEFI or BIOS if you have correct partitions.
If in BIOS boot mode you must have a 1 or 2MB unformatted partition with the bios_grub label from gparted.
If in UEFI boot mode you must have an efi partition formatted FAT32, usually first partition with the boot flag from gparted. Windows default is a 100MB, but we usually suggest larger like 300MB or even more is space is available.

But your sda has the boot flag on the swap partition. So some places say swap and others say efi. It may not work as either?
And you have sda2 as the bios_grub partition, but formatted FAT32 which will not work.

I would add a tiny 1 or 2MB partition anywhere on drive, not formatted and give it the bios_grub flag.
I would change flag on sda2 to the boot flag to make it the efi partition and remove boot flag from sda5.
Then you can install grub using either UEFI boot mode or BIOS boot mode. One or the other of the efi or bios_grub would not be used, but you later could switch.

Not sure about your Windows. Was it BIOS, you may be able to convert back to MBR and run Windows repairs, but then I would configure Ubuntu in BIOS boot mode.
Or you probably have to reinstall Windows in UEFI boot mode to reconfigure sdb correct as  Windows expects several extra partitions in UEFI mode. Make sure default hard drive is sdb before reinstalling Windows.

And how you boot install media, either UEFI or BIOS is how it installs.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by codetemplar on 2014-11-17
Thanks oldfred I really appreciate the time youve put into helping me with this. Please excuse any dumb questions I have as this is very new to me.

I have removed boot from swap sda5 and reformatted sda2 as fat32 and added boot flag.

I've added 1MiB unformatted drive to sdb which is now sdb3 and set flag to bios_grub.

The windows partitions sdb1 and sdb2 are failed installations and I will be deleting them and reinstalling windows7 as uefi when I get grub booting Ubuntu successful under uefi.

The only problem I'm having now is how to install grub to work with above configuration to boot uefi. Any suggestions? Thanks again

---

### Post by oldfred on 2014-11-17
You will not need a bios_grub on sdb, and if using UEFI then you really do not need it on sda either, unless you want to experiment with BIOS boot.

If efi partition is now correct, booting installer in UEFI mode an adding Boot-Repair should let you run the advanced mode total uninstall and reinstall of grub. The auto fix might work, but it may complain about sdb as the auto fix tries to install grub to every drive.

If you can disconnect the Ubuntu drive while installing Windows it will install so that drive is bootable without the Ubuntu drive. Otherwise it may use efi partition in Ubuntu drive for its efi files. Better to have each drive fully configured to boot without the other drive. 

       Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by codetemplar on 2014-11-18
Hi. Unfortunately I can't try this for another 24 hours. I don't have 2 separate drives. It is 1 drive with raid turned off so it is seen as 2 separate drives. At least that's my understanding anyway. I will turn bios_grub off sdb and just leave boot flag on sda2.

You are correct the auto repair in boot repair has been failing so I will use the advanced mode tomorrow.

Also when you say if I've done the efi partition correctly all I've done is create it at 200MiB as fat32 and added boot flag to it. As far as I'm concerned it is an empty partition that boot repair will install grub to tomorrow. Is this correct?

Thanks again

---

### Post by oldfred on 2014-11-18
With RAID you have to have two drives imaged together. You now have separated the drives so they are not and cannot be RAID unless you totally reinstall. 
Not sure if you had RAID 0 which is not recommended, but used to make for a fast system. Or RAID 1 which just writes data to both drives at same time.
Also RAID is not backup.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by codetemplar on 2014-11-19
Still having serious problems with this. I'm just trying to get grub to boot sda2 which should be my efi partition. I just want grub to give me an option to boot Ubuntu on sda1 on a gpt partition table. 

Boot repair says it succeeds but does nothing. I have no advanced options to use as it is all greyed out.

[http://paste.Ubuntu.com/9105663](http://paste.Ubuntu.com/9105663)

Thanks again

---

### Post by oldfred on 2014-11-19
You now have sda2 as an efi partition, but it has no efi boot files. You have grub in MBR probably left over from a BIOS boot, but that does not need to be erased, but do not boot in BIOS mode as it will not work.

But you main install in sda1 seems to only have boot files as if it was just a /boot partition. Script does not show an fstab which would be in / (root).

I think it may be easier just to do a reinstall. But you must use Something Else and choose sda1 as /, format as ext4. It will find swap automatically.

UEFI spec says efi partition should be first partition, but Windows does not make it first and your drives are small enough that where it is should be ok.

Be sure to boot installer in UEFI mode not BIOS.
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


Some examples with screen shots to see Something Else installs if not familar.
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by codetemplar on 2014-11-22
Success using "something else" worked this time! It previously kept failing but I guess my partitions are now setup correctly.

I'm trying to install windows 7 now 64 bit (32 bit doesn't support efi) but it keeps freezing on starting windows before getting to installation screen which apparently isn't uncommon. I am guessing it is something to do with the already created efi partition. Do you have any ideas what could be going on? Thanks for all your help.

---

### Post by oldfred on 2014-11-22
My last install of Windows was XP in 2006. 
Everything else I accumulated from others, so it all is second hand info.

Windows does like either a blank drive or partitions set up correctly for its install, either MBR with BIOS or gpt with UEFI. And each has different partition requirements.

Post #8 has most of what I know on UEFI install of Windows 7.

---

