---
title: "FSTAB   V's Storage Device Manager Query"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by Mccfuzz on 2011-10-28
Recently had problems with my partitions running Win2k.  You'll all be pleased to here Ubuntu kept me going until all was fixed. Thie fixing included a 2nd drive being disconnected.
After it was fixed, however,  I now have messages from Ubuntu saying things like 
Media sda4 not found press s
Drive 2 not ready press s
sdb6 not ready press s


I was hoping to correct these in with the Storage Device Manager but it doesn't actually give reference to the devices giving the problem as does FSTAB.

Before I make changes in FSTAB can someone confirm what changes I should be making.
stab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sdb2 during installation
UUID=2e65e39b-c9c9-4627-814a-077d6ae24fa1  /                 ext4  defaults                  0  1  
# swap was on /dev/sdb7 during installation
UUID=1bdb7a63-b579-4d6e-be10-304962df81f4  none              swap  sw                        0  0  
/dev/fd0                                   /media/floppy0    auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/sdc1       vfat  users,noauto              0  0  
/dev/sdc1                                  /media/DRIVE-TWO  vfat  users                     0  0  
/dev/sdc1                                  /media/sda2       vfat  defaults                  0  0  
/dev/sdb1                                  /media/sdb1       vfat  noauto                    0  0  
/dev/sdb3                                  /media/sdb3       vfat  noauto                    0  0  
/dev/sdb5                                  /media/sdb5       vfat  users,noauto              0  0  
/dev/sdb6                                  /media/sdb6       ntfs  defaults                  0  0  
/dev/sda5                                  /media/sda5       vfat  defaults                  0  0  
/dev/sda2                                  /media/sda2       vfat  noauto                    0  0  
/dev/sda4                                  /media/sda4       vfat  defaults                  0  0  
/dev/sda6                                  /media/sda6       ntfs  nls=iso8859-1,noauto      0  0  
/dev/sda3                                  /media/sda3       vfat  noauto                    0  0  

--------------------------------------------------------------------------------------------------------
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8a45b80b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5290    42491893+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2            5291       10554    42283080   83  Linux
/dev/sda3   *       10555       14953    35334967+   c  W95 FAT32 (LBA)
/dev/sda4           14954       24321    75248429+   f  W95 Ext'd (LBA)
/dev/sda5           14954       17757    22523098+   b  W95 FAT32
/dev/sda6           17758       24139    51263383+   7  HPFS/NTFS
/dev/sda7           24140       24321     1461883+  82  Linux swap / Solaris

Disk /dev/sdb: 15.4 GB, 15352725504 bytes
61 heads, 61 sectors/track, 8058 cylinders
Units = cylinders of 3721 * 512 = 1905152 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               3        8059    14988864    c  W95 FAT32 (LBA)
kevles@kevles-desktop:~$ gksu gedit /etc/fstab

---

### Post by Mccfuzz on 2011-10-28
Bump!

No replies so despite my inexperience experimented with 'fstab' itself and with a bit of trial and error got Ubuntu loading without the press 's' routine.

Here's the new 'fstb' read out if it helps someone:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sdb2 during installation
UUID=2e65e39b-c9c9-4627-814a-077d6ae24fa1  /                 ext4  defaults                  0  1  
# swap was on /dev/sdb7 during installation
UUID=1bdb7a63-b579-4d6e-be10-304962df81f4  none              swap  sw                        0  0  
/dev/fd0                                   /media/floppy0    auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/sdc1       vfat  users,noauto              0  0  
/dev/sdc1                                  /media/DRIVE-TWO  vfat  noauto                    0  0  
/dev/sdc1                                  /media/sda2       vfat  defaults                  0  0  
/dev/sdb1                                  /media/sdb1       vfat  noauto                    0  0  
/dev/sdb3                                  /media/sdb3       vfat  noauto                    0  0  
/dev/sdb5                                  /media/sdb5       vfat  users,noauto              0  0  
 
/dev/sda5                                  /media/sda5       vfat  noauto                    0  0  
/dev/sda2                                  /media/sda2       vfat  noauto                    0  0  
/dev/sda4                                  /media/sda4       vfat  noauto                    0  0  
/dev/sda6                                  /media/sda6       ntfs  noauto                    0  0  
/dev/sda3                                  /media/sda3       vfat  noauto                    0  0

---

