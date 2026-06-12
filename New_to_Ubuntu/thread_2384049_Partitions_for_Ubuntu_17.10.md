---
title: "Partitions for Ubuntu 17.10"
date: 2018-02-01
forum: New to Ubuntu
---

### Post by axis-yk on 2018-02-01
Windows 10 failed me so I’m going to install Ubuntu 17.10, want to ask what is the recommended disk space for each of the partitions needed? I have 1 2TB HDD. 

[My PC Specs]([http://www.acer.com/datasheets/2012/4871/PredatorG3620/DT.SJPSG.005.html](http://www.acer.com/datasheets/2012/4871/PredatorG3620/DT.SJPSG.005.html))

---

### Post by oldfred on 2018-02-01
With Ubuntu you only need one / (root) partition. 
If UEFI you then also need the ESP - efi system partition.
Optional are /home or /mnt/data partition(s).
If an Acer you also need "trust" on the UEFI boot file.

 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) 

      
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

