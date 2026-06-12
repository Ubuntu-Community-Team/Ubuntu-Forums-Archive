---
title: "Partition table issues laptop Lenovo y470"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by nynoah on 2011-11-27
I just bought a new Lenovo y470 laptop.  I am trying to do a dual boot install of Ubuntu and windows 7.  I only have one hard drive in the lap top.  Here is the problem.  When I open up Gparted to see what I have for partitions it turns out I have 4 primary partitions as part of the stock Lenovo setup.  

List 
1 200mg boot partition, NTFS, sda1
2 654gb one large, NTFS, sda2
3 29gb Extended, flaged as lba, NTFS, sda3
4 29gb medium, NTFS, sda5
5 15gb Labeled Lenovo_Part, flagged as diag sda4

Now is there anything I can do to get Ubuntu onto this machine.  I can reload the computer with windows 7 if need be.  Would it be advisable to wipe the hard drive, set up a EXT4 and swap with a NTFS primary and let Win 7 do what it can do, or is there no hope that way.  

Any advice?

---

### Post by oldfred on 2011-11-27
Lenovo did something good, as they did not use all 4 primary partitions as most vendors do. Use Windows only to shrink the c: partition, it does not handle extended partitions well.

You should be able to shrink your main Windows partitions with Windows  and  then with gparted extend the extended partition into the free space. Then you can with gparted create additional logical partitions for / (root) and swap and possibly /home. Then use manual install (Something Else) to choose & format partitions as part of the install.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

It seems you already have a shared data partition or is that a vendor recovery?

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by nynoah on 2011-11-30
Nice thanks for that.

---

