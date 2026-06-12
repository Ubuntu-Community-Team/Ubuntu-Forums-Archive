---
title: "Boot-Repair removed all of my partitions"
date: 2015-01-05
forum: New to Ubuntu
---

### Post by alex310 on 2015-01-05
Guys, I need help. I had no idea something like this could happen and I'm afraid I might have lost some data that is important.

So I have a laptop. It runs (or used to run) Windows 7. Yesterday I was going to install Ubuntu on a separate ext4 / partition. At the moment of installation it looked more or less like this:
sda1: some small partition created by the manufacturer
sda2: windows system partition
sda3: unallocated space I'd left for Ubuntu, formatted to ext4 during the installation
sda4: a backup partition with some stuff I don't have backed up elsewhere
sda5: small windows system recovery partition

1. So I installed Ubuntu to sda3 using the "do something else" option during the installation. 
2. The Ubuntu installer (14.04.1) didn't recognize Windows at all, so I had no option to install alongside it. 
3. I formatted sda3 to ext4, marked it as root.
4. Installation continued.
5. Everything went fine.
6. Laptop rebooted.

And then the problems began. Only Windows would boot again and GRUB was nowhere to be found. Nothing helped - boot menus, another installation etc. When I would boot from LiveUSB I would see Ubuntu there and I would see all my logical disks as well with all the data on them. At that moment everything was fine except Ubuntu wouldn't boot.

I was lurking the forums until I'd stumbled onto a page linking to [this tool]("https://help.ubuntu.com/community/Boot-Repair"). There had been people with a similar issue and running this helped them. So:
1. I boot into the LiveUSB.
2. I install Boot-Repair via terminal.
3. I run recommended repair.

Somehow this ruined everything. I had no idea boot repair would mess with anything that wouldn't be grub/ubuntu related, but apparently it did. 

1. I have no more partitions, just the small one from the manufacturer, the system restore partition and the large 600GB partition instead of Windows partition (sda2), Ubuntu partition (sda3) and backup partition (sda4).
2. Even Ubuntu won't boot now. In fact, nothing boots - at startup I get flashing screen (black/gray). No console or anything, it just looks lik it's about to start booting but can't.
3. When I boot from LiveUSB I don't see any partitions anymore, just one partition with some of Ubuntu files on it.
4. Windows installation USB doesn't see any of the old partitions either, is unable to repair anything.
5. All I got is this boot info script from Boot-Repair - [http://paste.ubuntu.com/9672929/](http://paste.ubuntu.com/9672929/)

I really need help. My priorities at the moment are:
1. Get the sda4 stuff back. Preferably get the partition back as it had been, but if that's not possible - I need to at least get the files.
2. Get the sda2 partition back if that's possible. Get my old Windows 7 system to boot.

The biggest question here is - could Boot-Repair have formatted the partitions? And why would they all be gone after I ran it anyway?

---

### Post by alex310 on 2015-01-05
UPD:
1. Did some more googling. Found a 3rd part utility called Boot Disk to try and restore partitions. Created a bootable USB.
2. It's currently doing a deep scan (quick scan found nothing) and so far it seems to have found my Win7 system partition and I can see the files (yay?). Not sure if it will be able to restore it as boot partition, but I guess I will at least be able to create a disk image or something.
3. Backup partition still out there somewhere. The file system looks super weird, there are literally dozens of small partitions that I didn't have yesterday, their integrity status is shown as "Very bad". 

At this point I guess the best I can hope for is booting back to Windows to get back control of my hard drive, format everything and create proper partitions again.

---

### Post by yancek on 2015-01-05
Looking at the bootinfoscript output you posted, the first thing I see at the top is "No boot loader is installed in the MBR of /dev/sda" so you can't do a standard MBR boot.  This would indicate UEFI/GPT booting which does not put any boot code in the MBR.  Scroll down to the sda1 section which shows it as a vfat partition which is what you would have if you were using UEFI/GPT to boot.  The problem is that there should be both windows and Ubuntu efi files there and there are no files shown.

sda2 shows filesystem unknown and no boot files are shown which usually do show, whether windows or Linux.
sda3 shows as swap partition.  No windows or Linux partitions are indicate.  Don't know what is or was on sda2 but if it was a standard windows 7 install, it probably would have been where  the windows system files were.  Scroll down a little further to the "GUID Partition Table Detected" and you see the output below:

> Partition    Start Sector    End Sector  # of Sectors System /dev/sda1           2,048     1,050,623     1,048,576 EFI System partition /dev/sda2       1,050,624 1,242,050,559 1,240,999,936 Data partition (Linux) /dev/sda3   1,242,050,560 1,250,263,039     8,212,480 Swap partition (Linux) 

Which looks like Ubuntu was on sda2.  I don't see any sign of a windows or Linux system nor do I see "dozens of tiny partitions" you refer to in your last post.  Maybe some changes were made since you posted the bootrepair output.  If you succeed in getting windows back, before you try to install Ubuntu again do some reading on MBR booting compared to UEFI/GPT.  Mixing the two methods leads to problems as you can see.  Good luck with it.

---

