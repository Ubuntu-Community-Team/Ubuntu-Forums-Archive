---
title: "How to properly install server system on nvme ssd and use 2 hdd drive in RAID 1"
date: 2022-11-03
forum: New to Ubuntu
---

### Post by mikhail-shkaralevich on 2022-11-03
Hello,

I am just starting with linux and I've been trying to figure out how to create a home NAS with ubuntu server 22.04. I want to install the server on Nvme SSD and use my 2x16tb seagate hdd in RAID 1 as a storage and share it across my home network.

My main concern:
[LIST]
[*]I don't quite understand the file system. Where do i need to mount my hdd drives? What directory? /home? /media/?
[*]What file system do i need to format my hdd drives, so that they will be accessible by windows machine?
[/LIST]

Thank you!

---

### Post by TheFu on 2022-11-04
> How to properly install server system on nvme ssd and use 2 hdd drive in RAID 1 

"properly" is highly subjective.  There are many options. That's because Linux is flexible to meet specific needs for specific situations.

If it were me, I'd disconnect/ignore the HDDs during installation and use just the NVMe for the OS, but not for data.  Here's my setup:
```
nvme0n1                      465.8G disk                   
&#9500;&#9472;nvme0n1p1                     50M part vfat   EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                    600M part ext4              /boot
&#9492;&#9472;nvme0n1p3                    465G part LVM2_m            
  &#9500;&#9472;vg00-swap                  4.1G lvm  swap              [SWAP]
  &#9500;&#9472;vg00-root--00               35G lvm  ext4              /
  &#9500;&#9472;vg00-var                    35G lvm  ext4              /var
  &#9492;&#9472;vg00-home                   26G lvm  ext4   home       /home
```
This was setup at the end of August 2022, so it shows what I actually do.  The actual use:
```
$ df -Th
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root--00                   ext4   35G  9.1G   24G  28% /
/dev/nvme0n1p2                              ext4  574M  272M  260M  52% /boot
/dev/nvme0n1p1                              vfat   50M  5.2M   45M  11% /boot/efi
/dev/mapper/vg00-home                       ext4   26G  9.8G   15G  41% /home
/dev/mapper/vg00-var                        ext4   35G   25G  8.1G  76% /var
/dev/mapper/istar--8TB--B-jellyfin_varlib   ext4   89G  6.9G   77G   9% /var/lib/jellyfin

```
That system has about 40TB of storage connected. I removed the pure data parts.

I use LVM for volume management. This provides great flexibility.  LVM is LVM regardless of the Linux OS.  Find a tutorial and use that.  I find the disk setup that the installer provides basically sucks. Instead, before the installer runs the disk stuff, I setup the LVM PV, VGs and LVs as I like. In the installer, I only need to connect the LV to the mount location.  As you can see above, I leave most of the storage unused by LVs.  LVM provides massive flexibility, provided plenty of storage is left available for future needs.  Increasing an LV is 5 seconds, so start small.

The RAID stuff has lots of options, beginning with the volume management.  Today, there are 4 choices, mdadm, LVM, ZFS or BTRFS.  LVM allows any file system to be used for each LV.  ZFS and BTRFS are both a volume manager and tightly integrated file system.  For the size of storage you plan, I'd use ZFS.  BTRFS has some issues when used in multi-disk setup - data loss has happened. Read more here: [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/)

Mdadm can be a separate layer below all the others and has been enterprise capable over  20+ yrs.  It is common to see older systems with mdadm providing RAID, then LVM doing the volume management on top.  LVM has the mdadm code inside it for about the last 8 yrs, so it is possible ( and easier ) to use LVM's RAID.  I've used both.  Today, I use the LVM-only RAID when that is needed, but I don't use RAID much anymore, since SSDs are extremely reliable. I spend my redundancy efforts on backups.

Backups are still mandatory. RAID never replaces backups.  RAID solves 2 issues. Backups solves 1001 issues, including RAID corruption. In short, only consider RAID **after** backups are handled perfectly.

If I were setting up a new RAID for data only, then I'd use ZFS today.  

If you seek exact commands, I'll leave that for others ... since those are in threads here and on other websites. The big picture and options are more important.

BTW, it is fine to NOT use any volume management on the OS storage, though if you want 100% perfect backups, snapshot capabilities and some other enterprise storage features, using a volume manager is mandatory.  There's no way short of a reinstall to get those back.  For data storage, changes are easier, later, but expect no 'in-place' methods to change. You'll need to copy all the data off (i.e. backups) and setup the data storage how you like, then copy all the data back.  In Linux/Unix, the underlying storage methods used doesn't really matter, provided that the storage is mounted to the same locations in the file system.  Don't think of storage as "drive letters", since that isn't how it works in any OS, except 1.  Plus that term "drive letters" isn't factually correct.  They are partition or file system letters in reality on that other OS.  On Unix systems, we mount file systems to nearly any directory, usually an empty directory 99.9999% of the time.  That is called a "mount point".  Above you can see that I've mounted a file system to /var/lib/jellyfin. That's because it is where I needed it and it is for a specific purpose.  For me, separate file systems are mostly about backup design.

Anyway, hope this is helpful in some way.  I also hope that someone with ZFS skills will post. Just know that ZFS isn't ready to be used for the OS storage yet, at least by non-experts.  For data storage, definitely use ZFS if you can.

Oh ... for network access by Windows machines, the file system on a Linux server isn't important, except that it be a native Linux file system.  So, you can use zfs, ext4, xfs as you like. There are reasons to use each.  After all, Windows systems will access to the storage over the network using CIFS.  It is a bad idea to make storage choices for an OS the file systems will never be connected to directly.  In short, don't pick NTFS just because Windows needs network access.  NTFS is for Windows storage that is directly connected to Windows. NTFS brings too many issues for serious use on Linux for storage. It doesn't support POSIX file permissions, so 50% of the critical information about data is lost.

---

### Post by mikhail-shkaralevich on 2022-11-04
Thank you very much for your explanation!

---

