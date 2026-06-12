---
title: "Post-Installation Partitions/BIOS utilities/GRUB install fail"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by benijenks on 2012-08-03
Hey all. I just installed Ubuntu 12.04 onto my Hp Pavilion G6,
and I just had two questions, and a useless anecdote:

1) Before I installed Ubuntu, I had 3 partitions that I knew of. One was Windows 7, one was a system partition, and the other was an HP tools partition. I just downloaded GParted, because I couldn't find any administrative tools or similar app (EDIT: I just found Disk Utility.). Listed are

/dev/sda1  FS: ext4   Mount point: root  size: ~700gb

/dev/sda2  FS: Extended size: 5.74gb           (6.2gb in Disk Utility)
     /dev/sda5  FS: linux-swap  size: 5.74gb   (6.2gb in Disk Utility)

What is the sda2 partition, and it's sub-partition?


2) When I boot up my PC, I still have some BIOS utilities that don't exist anymore. Like recovery, some kind of bios-checker. What is the purpose of these? Are they firmware that will not go away, even if I got rid of the HPTools partition which held them?

Thoughts on either of these?

As a side-note:

When I installed from a live USB, the grub installation kept failing. I had read of others who had this problem, but no one seemed to figure it out. So, I booted up into a live environment, after a couple failed installs, and installed from there. It worked! I have no idea why, but it did! I don't know if this is worth mentioning, but I figured I'd share.

---

### Post by oldfred on 2012-08-03
Are you sure you did not have 4 partitions? HP's almost always do. But one is the Windows hidden boot/repair partition.

this may be a bit after the fact:
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

It looks like you installed with the overwrite the entire drive option which erases everything else. Your sda2 extended partition is a container for logical partitions. With MBR(msdos) partitioning you can only have 4 primary partitions. Windows only boots from primarys. But you can convert one primary to the extended and put many logical partitions in the extended.  Linux boots from logicals. You are showing one partition in your extended and it is the swap partition. Swap is for use when RAM is full and it needs more memory.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by benijenks on 2012-08-03
> **oldfred said:**
> Are you sure you did not have 4 partitions? HP's almost always do. But one is the Windows hidden boot/repair partition.

this may be a bit after the fact:
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

It looks like you installed with the overwrite the entire drive option which erases everything else. Your sda2 extended partition is a container for logical partitions. With MBR(msdos) partitioning you can only have 4 primary partitions. Windows only boots from primarys. But you can convert one primary to the extended and put many logical partitions in the extended.  Linux boots from logicals. You are showing one partition in your extended and it is the swap partition. Swap is for use when RAM is full and it needs more memory.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

I got rid of my recovery partition a while back, to make room for a separate ubuntu partition.

So basically, the other partition is just like... a page file? And not some left-over crap from HP?

---

### Post by oldfred on 2012-08-03
The default install is just / (root) and swap. 

Many like to have /home as a separate partition so you can do a clean reinstall and reuse /home but still should have full backups of /home either way. But I used the default install with a small added NTFS data partition as I had XP on one drive and Ubuntu on another and wanted to share some data. After another larger drive and many test installs I now have lots of partitions. :)

---

