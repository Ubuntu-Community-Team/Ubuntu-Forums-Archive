---
title: "Ubuntu doesn't list my 2nd hard drive"
date: 2017-04-02
forum: New to Ubuntu
---

### Post by Satyros on 2017-04-02
I had my main drive with Windows 10 and a 2nd drive for storage and backup. I booted Ubuntu from a flash drive and selected "erase Windows 10 and install Ubuntu". I was expecting it to erase all content on the 1st drive but keep my 2nd drive intact.
Now, when I click on "Files" all I see is "Computer", nothing about a second drive. What is strange is, it says the total capacity is 600 GB. I'm pretty sure that's the total capacity of the two drives summed up.
So I have two questions:

1 -- How can I access the files that were on that second drive (that, in theory, shouldn't have been deleted)
2 -- How can I make Linux display it as a separate hard drive?


thx@thx55:~$ sudo parted -l
[sudo] password for thx: 
Model: ATA Hitachi HTS54756 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  632GB  632GB   primary   ext4            boot
 2      632GB   640GB  8569MB  extended
 5      632GB   640GB  8569MB  logical   linux-swap(v1)

---

### Post by oldfred on 2017-04-02
What brand/model system.
Some have two drives in RAID mode. And if RAID 0 half of data is on one drive and half on other drive, alternative stripes. Or only way to recover is from backup.

Post this.
sudo parted -l

If just Windows NTFS, newer Windows uses fast start up or hibernation. And that keeps all NTFS partitions mounted. It it just may still be mounted.
Then you may be able to manually mount in read only mode. But Linux will not otherwise mount a hibernated NTFS.

---

### Post by Satyros on 2017-04-03
Well, I have no idea what the brand/model is, nor the file-system. It's a Toshiba laptop, a Satellite L775-12V. I had Windows 7 and after that Windows 10. There were always 2 hard drives labeled with different character. C: and D:, if I recall correctly.

sudo parted -l returns the following:

Model: ATA Hitachi HTS54756 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  632GB  632GB   primary   ext4            boot
 2      632GB   640GB  8569MB  extended
 5      632GB   640GB  8569MB  logical   linux-swap(v1)

[h=1][/h]

---

### Post by mooreted on 2017-04-03
It sounds like you may have had one drive with two partitions. Allowing Ubuntu to format the drive and install Linux would have removed both partitions and re-partitioned the drive.

From the Dash menu search for 'Disks'; what does it show for connected drives?

---

### Post by oldfred on 2017-04-03
Microsoft has always mixed the definition of drive, which really is a partition.
Or with Microsoft two physical drives could be c: & d:. But a second partition on the first drive is also d:.
In Linux it is clear. Drives are sda, sdb, sdc etc. And partitions are last number like sda1, sda2, sda3 for three partitions on first drive.

If you overwrote your d: "drive" and it really was part of sda, then [COLOR=#ff0000]STOP[/COLOR] using system. All use is overwriting more data.
Linux is not large, but writes data into all areas of a partition. NTFS writes data primarily at beginning of a "drive" and after a defrag all data is at beginning.

There are recovery tools but some work better than others. But some data will be lost no matter what. That is why all install instructions suggest really good backups before the install.

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
      [/URL]
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 
    
      
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by Satyros on 2017-04-03
I am inclined to think you are right, as a search for my laptop model only mention one hard disk of 640 GB: [http://www.toshiba.pt/discontinued-products/satellite-l775-12v/](http://www.toshiba.pt/discontinued-products/satellite-l775-12v/)

I'd simply never considered that scenario as I'm 99% that I never partitioned my hard disk. Is it possible that it came partitioned by default, hence appearing as two disks?

[IMG]http://i.imgur.com/v1Ed5NR.png[/IMG]

---

### Post by mooreted on 2017-04-03
Yup, you have one physical hard drive on your computer.

---

### Post by mastablasta on 2017-04-04
> **Satyros said:**
> 
I'd simply never considered that scenario as I'm 99% that I never partitioned my hard disk. Is it possible that it came partitioned by default, hence appearing as two disks?


yes, laptops usually come like that. in fact most newish ones would have 4 partitions made while the new ones have at least 3 or more. 

usually (with newwer) they are system, data, boot, recovery. on mine (win7) i had system&data, tools, recovery and boot.

stop using it and follow oldfreds advice to recover the data.

---

### Post by Satyros on 2017-04-04
Fortunately, I had most data backed up. All I wanted was to solve the mystery of the missing drive :)

Thank you.

---

