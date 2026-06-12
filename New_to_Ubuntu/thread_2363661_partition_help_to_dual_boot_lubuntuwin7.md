---
title: "partition help to dual boot lubuntu/win7"
date: 2017-06-12
forum: New to Ubuntu
---

### Post by rabbitrabbit on 2017-06-12
I've had it with windows and used a lubuntu 17.04 live usb to save a few files from the win laptop that ended up with a virus. I'd like to try dual booting Win7(home) with lubuntu - I'm still an Illustrator user (CS1 files do not convert happily to Inkscape, in my experience) and I have an unreplacable program that no one has reported attempting to use with Wine (yet). The machine in question is a Lenovo U460.

What would be the preferred order of operations for partitioning and cleaning up the Win installation? I don't have a disc, but the laptop does have a recovery partition. Should I adjust the partitions, do a system restore on win, then install lubuntu? 

What partitions do people suggest? Keep in mind that all my files are currently off-machine, but I'd like to be able to share the files between lubuntu and win. 

Using my live USB, gparted shows the following:
sda1, ntfs, (my live usb, yes?), 200MB, flagged boot
sda2, ntfs, 421GB
sda3, extended 29GB, flagged lba
sda5, ntfs, lenovo, 29GB
sda4, ntfs, lenovo_part, 14.75, flagged diag

When I look at the disc preferences I see the 500GB drive as having 5 partitions that are seperated a little differently:
file system, partition 1, 210BM, ntfs (says this is my mounted live USB)
file system, partition 2, 453GN, ntfs
partition 3, 0k unknown
free space 31GB
Lenovo_Part, partition 4, 16GB, ntfs
I'm further baffled by the listing on the left of the disc preferences of four 503MB block devices that must be the RAM and a 919MB "loop device" that says "backing file: /cdrom/casper/filesystem.squashfs". Any idea what that loop device is? I also see the live USB stick on this list too. Clearly I've never looked at this stuff via windows. 

Any assistance would be appreciated! Thanks!

---

### Post by TheFu on 2017-06-12
If you run the **boot-info** script (search the forum here for links to it), then we can help. At this stage, I'm afraid to say much, since it is very possible that your interpretation of things is incorrect.

For example, sda is an entire disk.  sda1-sda127 are partitions on that disk.  sdb would be a different disk.  The method of formatting on the disk would explain much too.  MBR vs GPT.  GPT is much more flexible and safer, but Windows has some limitations around using it which may be an issue.

Regardless - before doing anything, make a 100%, know-you-can restore backup.  Doctors don't do heart surgery in the back of a bus on a bumpy road for a reason.

boot-info will make a URL. Just provide that, please.

BTW, you are on a Lenovo - did you already remove the [rootkit they generally ship]("https://thehackernews.com/2015/08/lenovo-rootkit-malware.html")?

---

### Post by oldfred on 2017-06-13
Windows 7 or later normally has a separate /boot partition that you never see in Windows. That is your sda1 and is required by Windows. And then main install of Windows is in sda2.
Linux separates drives and partitions where Windows mixes them. Or in Windows a "D:" drive can be a second partition on first drive or first partition on second drive. 
Linux uses sda, sdb, etc for drive and number at end for partition on drive like sda1, sda2 etc.
To see Linux partitions using terminal in live installer (Boot-Repair will show this plus lots of other useful info:
sudo parted -l

Loop device is an unpartitioned drive, often your live installer is mounted as a loop device. But depending on tool used to create live installer it may or may not show normal partitions. The Ubuntu ISO is configured as a Hybrid ISO. Or it can be both DVD or flash drive installer, but if imaged to flash drive (not installed) the flash drive does not have standard partitions, but is seen as a DVD.

Best to have working Windows when installing UBuntu. And it always is best to use Windows disk management to resize the main NTFS partition to make unallocated space. And particularly if corrupted resizing with gparted or installer may make it difficult or impossible to repair.
Standard rule is Windows tools for Windows and Linux tools for Linux. But some Linux tools can do a few things to Windows where Windows does not even see or know you have Linux partitions.

---

