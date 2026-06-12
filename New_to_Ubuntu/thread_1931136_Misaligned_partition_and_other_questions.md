---
title: "Misaligned partition and other questions"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by thedarkorb on 2012-02-24
I've been casually using Ubuntu for a few years but this is the first time I've had real trouble with the OS. I bought a new laptop for my wife who has been using Ubuntu for a couple years after I installed it on her previous one. I have three questions:

1. After formatting the drive and installing Ubuntu 11.10 (64 bit) the disk utility gives me the message "the partition is misaligned by 3072 bytes" and suggests repartitioning. I formatted and reinstalled and am getting the same message. How exactly do I align a partition properly?

2. I've read that 64 bit Ubuntu has issues with flash. Is this still the case? Am I better off installing the 32 bit version of 11.10?

3. The laptop in question has 4 gigs of RAM but Ubuntu seems to only detect 3.5. Why is this and what can I do to make sure the system uses all four gigs?

---

### Post by thedarkorb on 2012-02-24
I've just noticed another odd quirk. When shutting down the laptop hangs at the Ubuntu screen. The only way to turn it off is to hold down the power button.

---

### Post by thedarkorb on 2012-02-25
Regarding the misaligned partition: I've done some checking around and the brand Western Digital keeps popping up in relation to this issue. If I were to replace the HD with one not from WD would that solve my partitioning problem?

---

### Post by cryptotheslow on 2012-02-25
I don't think it is brand specific.

I am no expert but as I understand it hard drives are in the process of moving from a physical sector size of 512 bytes to 4096 bytes. Ideally we want any partition to start exactly on the start of a physical sector.

However, not all partitioning tools have caught up with this - and to confuse things further some of the newer drives will report they have a 512 byte sector size in order to try to maintain backward compatibility, making the partitioning tool's job even harder to get it right.

If you open a Terminal and enter the command:
```
sudo fdisk -lu
```you will see the relevant information, something like this:

```
crypto@ubulaptop1204:~$ sudo fdisk -lu
[sudo] password for crypto: 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x496b9619

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    52430847    26214400   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    52430848   536088575   241828864    7  HPFS/NTFS/exFAT
/dev/sda3       536089050  1311546599   387728775    7  HPFS/NTFS/exFAT
Partition 3 does not start on physical sector boundary.
/dev/sda4      1311547390  1465147391    76800001    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1311547392  1459984383    74218496   83  Linux
/dev/sda6      1459986432  1465147391     2580480   82  Linux swap / Solaris

```As you see I have the same warnings about partitions not starting on a physical sector boundary. But note near the top where it identifies the different logical and physical sector sizes.

So basically to fix it the partitions either need moving or recreating on a 4096 byte boundary. I've not fixed up mine yet as I intend to blow the partitions away in a couple of months for a reinstall anyway.

I'm sure I read on this forum that Ubuntu tends to partition to the nearest 1024 byte boundary (which would have been fine for 512 byte physical sectors of old) and I'm sure I saw a good post on how to calculate a correct starting value for a partition - just can't find it now :(

*edit to add:*
This is a good explanation:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX)

and does specifically mention that Western Digital did (and maybe still do) have physical 4096 byte sector drives that report themselves as 512 byte to the BIOS and so consequently appear as so to the operating system.

Post up the output of that fdisk command above so we can see what's what for yours.

Good Luck :popcorn:

---

### Post by growingneeds on 2012-04-23
The problem with misalignment lies with the partition editor. The partition editor that Ubuntu uses during installation defaults to "Rounding off to nearest cylinder". Whereas for newer installers like LMDE 201109, it defaults to "**_Rounding off to nearest MB_**". After reinstalling Ubuntu for at least 10 times to verify this, I confirm that when using **_GPartEd Live CD_** to prepare the HDD for Ubuntu installation solves the misalignment issue.

Hope this helps.

---

