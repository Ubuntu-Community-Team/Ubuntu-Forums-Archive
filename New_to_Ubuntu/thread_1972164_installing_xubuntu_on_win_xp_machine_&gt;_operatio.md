---
title: "installing xubuntu on win xp machine &gt; operation system not detected"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by natroll on 2012-05-03
I'm trying to install xubuntu on my win xp machine from the live-usb. I have win xp installed on hard disk-a and I also have hard disk-b where I would like to install xubuntu.

I tried to install xubuntu next to me win xp but the installation program says no operation system detected.

I tried to make a partition for the xubuntu to my hard disk-b but gparted says both of the disks are unallocated.

Then I run **sudo fdisk -lu**
> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR=Red]976773168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcc95a08d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   [COLOR=Red]976784129[/COLOR]   488391041    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR=Red]976773168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf93a0b02

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  [COLOR=Red] 976784129[/COLOR]   488391041    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 16.0 GB, 16011542528 bytes
32 heads, 63 sectors/track, 15512 cylinders, total 31272544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1d346152The win xp is installed on sda.

So it look like my partitions are too big for the max size of my hard disks.

How do I shrink those partitions and is it safe to do it for the win xp partition**[SIZE=2]? [/SIZE]**[SIZE=2]What about sdb[/SIZE][SIZE=2]?[/SIZE]
[B][SIZE=2] 
[/SIZE][/B][SIZE=2][SIZE=1]Thank you very much for the help.[/SIZE]
[/SIZE]

---

### Post by oldfred on 2012-05-03
I suggest this:
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Gparted usually will not show drives with partition table issues. You can also use sfdisk, by manually editing the table you export and reimport it, but fixparts is easier to use.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

