---
title: "How to access hard drives?"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by RoverV8 on 2012-12-27
Hello! I've just acquired a new computer without OS after my 2005 Dell (WinXP) died... got three hard drives in, the Dell's old C:\ and F:\ drives (The former as master) and a new drive in... but I cannot for the life of me see how to access them through the "Home Folder" function (File System > Media just displays 'floppy' and 'floppy0' - the machine came with a floppy drive... I haven't used floppies in  decade!). There are a hell of a lot of files and apps I need to access on these drives... any ideas? I'm keen on the concept of Ubuntu but at the moment Windows is looking a hell of a lot more usable...

---

### Post by sudodus on 2012-12-27
Welcome to the Ubuntu Forums :-)

How are you running Ubuntu?

Normally hard disk drives are easy to see with the file browser (I guess that's what you mean by Home Folder function).

But to help us help you, please start a terminal window with the hotkey combination

**ctrl + alt + t**

and type the following commands (and run them with the ENTER key).

```
sudo fdisk -lu
```
```
df
```
Paste the output into a reply.

---

### Post by superDave972 on 2012-12-28
If I am not mistaken, WInXP formatted their hard drives in a NTFS format. If I remember correctly, Linux is not compatible with NTFS formats. I believe it prefers FAT.

---

### Post by superDave972 on 2012-12-28
After some quick searching, I did affirm that NTFS is proprietary to Microsoft. 

I have also found this [information]("http://ubuntuportal.com/2012/05/heres-two-methods-to-mount-automatically-ntfs-drive-in-ubuntu-12-04.html"). It may be helpful to you.

---

### Post by oldos2er on 2012-12-28
> **superDave972 said:**
> If I am not mistaken, WInXP formatted their hard drives in a NTFS format. If I remember correctly, Linux is not compatible with NTFS formats. I believe it prefers FAT.

Ubuntu can read and write to NTFS (and FAT) formatted partitions just fine.

---

### Post by Wim Sturkenboom on 2012-12-28
A partition will only be in filesystem -> media once it's mounted. The filemanager will have a left pane where the partitions will (should) show with names similar to '80GB Filesystem' under the section 'Devices'. Clicking them will mount them and next you can access your files. If you did label your harddisks in windows, they will be represented by their name; the attached image shows this for 'Win7', 'WinXP', 'WinXPData' and 'SHARED_FAT'. The '27GB Filesystem' and the '125GB Filesystem' are partitions that have no labels (in my case containing an old 10.04 install)

---

### Post by oldfred on 2012-12-28
Is BIOS seeing drives?

You mention master, are old drives IDE and do you then have jumpers correctly set to slave or slave with Master.
Or if you are using the newer 80 conductor cables are drives set to cable select, not master nor slave?

       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by RoverV8 on 2012-12-29
Sudodus, tried that but it won't let me copy or paste the content... CtrlC results in ^C appearing in the command line...

These two drives are not appearing under File System > Media or Devices - nor, in fact, is the new 500gb drive. That's set as the master drive with the one jumper I have. Haven't a clue what type of ribbon cable it uses. I'm just an end user with a mistrust of Microsoft and a liking for open source software...

---

### Post by RoverV8 on 2012-12-29
Forgot to mention, new drive is SATA, older ones are PATA.

---

### Post by sudodus on 2012-12-29
> **RoverV8 said:**
> Sudodus, tried that but it won't let me copy or paste the content... CtrlC results in ^C appearing in the command line...

These two drives are not appearing under File System > Media or Devices - nor, in fact, is the new 500gb drive. That's set as the master drive with the one jumper I have. Haven't a clue what type of ribbon cable it uses. I'm just an end user with a mistrust of Microsoft and a liking for open source software...
If you click Edit at the top of the terminal window, you will get a pull down menu with Copy and Paste options. There are hotkeys too, but not the usual ones, since they are already in use for other purposes. So you can use

***shift + ctrl + c*** to copy
***shift + ctrl + v*** to paste

Ubuntu can manage with a mixture of SATA and PATA drives. Now I am looking forward to see the output of your terminal commands :-)

---

### Post by RoverV8 on 2012-12-29
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82b682b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 15.9 GB, 15931539456 bytes
255 heads, 63 sectors/track, 1936 cylinders, total 31116288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8192    31116287    15554048    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ df
Filesystem     1K-blocks   Used Available Use% Mounted on
/cow             1032668 990580     42088  96% /
udev             1024048      4   1024044   1% /dev
tmpfs             413068    916    412152   1% /run
/dev/sr1          771372 771372         0 100% /cdrom
/dev/loop0        739712 739712         0 100% /rofs
tmpfs            1032668 145636    887032  15% /tmp
none                5120      4      5116   1% /run/lock
none             1032668    208   1032460   1% /run/shm
none              102400     56    102344   1% /run/user
/dev/sdb1       15549952  18752  15531200   1% /media/ubuntu/No.1 Squad.
ubuntu@ubuntu:~$

---

### Post by sudodus on 2012-12-30
> **roverv8 said:**
> ```
ubuntu@ubuntu:~$ sudo fdisk -lu

[color="blue"]disk /dev/sda: 250.1 gb, 250058268160 bytes[/color]
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
units = sectors of 1 * 512 = 512 bytes
sector size (logical/physical): 512 bytes / 512 bytes
i/o size (minimum/optimal): 512 bytes / 512 bytes
disk identifier: 0x82b682b6

   device boot      start         end      blocks   id  system
[color="blue"]/dev/sda1   *          63   488375999   244187968+   7  hpfs/ntfs/exfat[/color]

[color="red"]disk /dev/sdb: 15.9 gb, 15931539456 bytes[/color]
255 heads, 63 sectors/track, 1936 cylinders, total 31116288 sectors
units = sectors of 1 * 512 = 512 bytes
sector size (logical/physical): 512 bytes / 512 bytes
i/o size (minimum/optimal): 512 bytes / 512 bytes
disk identifier: 0x00000000

   device boot      start         end      blocks   id  system
[color="red"]/dev/sdb1            8192    31116287    15554048    c  w95 fat32 (lba)[/color]
ubuntu@ubuntu:~$ df
filesystem     1k-blocks   used available use% mounted on
/cow             1032668 990580     42088  96% /
udev             1024048      4   1024044   1% /dev
tmpfs             413068    916    412152   1% /run
/dev/sr1          771372 771372         0 100% /cdrom
/dev/loop0        739712 739712         0 100% /rofs
tmpfs            1032668 145636    887032  15% /tmp
none                5120      4      5116   1% /run/lock
none             1032668    208   1032460   1% /run/shm
none              102400     56    102344   1% /run/user
[color="red"]/dev/sdb1       15549952  18752  15531200   1% /media/ubuntu/no.1 squad.[/color]
ubuntu@ubuntu:~$
```

Fdisk sees one HDD of 250 GB ([COLOR="Blue"]blue[/COLOR]) and I guess one USB flash drive of 16 GB ([COLOR="Red"]red[/COLOR]). The partition on the HDD is not mounted, and the partition on the USB drive is mounted on

[FONT="Courier New"][SIZE="3"]/media/ubuntu/no.1 squad[/SIZE][/FONT].

Can you identify which of the drives that is seen?

Next, try to mount it using the tips by *Wim Sturkenboom* how to do it from the file browser!

If no success, try to mount it from the following terminal command
```
sudo mount -t auto /dev/sda1 /mnt
```

and try to look at what is found in the directory ***/mnt***

1. with the file browser or
2. with the terminal commands
```
cd /mnt
``` and ```
ls -l
```

Good luck :-)

*Edit*: "ell-ess space minus ell"

---

### Post by oldfred on 2012-12-30
Not sure if contributing to issue, but LInux does not like space. To use them you have to put names in quotes or escape the space. 

/media/ubuntu/No.1 Squad.

I label partitions with Disk Utility as that is one of the easiest ways.

       I learned a while back to stop using spaces. Use CamelCase or under_score or just onename. Windows will work without the spaces and it makes things a lot simpler in Linux.

---

### Post by Wim Sturkenboom on 2012-12-30
It's time to check your connections of the HDs. Are they picked up in the BIOS.

As sudodus pointed out, there is one hard disk at this stage and I like to add that the others are not detected. You mention a 500GB in one of your posts but sda is only 250GB.

What is on sda? Do you have a Windows install on there? If so, does it pick up your other disks?

---

### Post by RoverV8 on 2012-12-31
I am now able to access the 250gb PATA drive (despite not having made any changes). The new 500gb SATA drive (which is set as the master) and the ancient 80gb PATA drive remain invisible and inaccessible. The other media was a USB micro SD card which I had forgotten to disconnect.

---

### Post by sudodus on 2012-12-31
Please read carefully all the replies you have received in this thread! Try to use the advice to make the computer 'see' the drives!

Check the connections and jumper settings!

Look in you BIOS menus and see what drives are found there! Maybe you need to change some BIOS setting to see the SATA drive.

You could even test booting from a CD/DVD/USB drive and run the appropriate linux commands, for example

```
sudo fdisk -lu
```

---

### Post by RoverV8 on 2012-12-31
The connections and jumper setting are all correct as I have already said. I will check BIOS. I am booting off a disc as I have not yet installed the OS (I'm using the 'Try Ubuntu' option) - I don't pretend to understand partitioning, nothing I can do to it, it seems, will satisfy it such that it will proceed with the installation and would rather wait until I've got the SATA drive up and working. There are TWO PATA drives, the 250gb one and an older 80gb one - it's only seeing the former. I've already run the command 

sudo fdisk -lu
and posted above what it returned, establishing that the system could see the 250GB drive and a memory card reader (though it was not allowing me to access the hard drive and was not displaying it under File System).

---

### Post by oldfred on 2012-12-31
I do not know Dell that well. One user had a very old Dell that had one IDE and one SATA connection. It could only boot from the IDE master and the SATA was SATA1. which I did not really know existed as most SATA drives I have seen were SATA2.
I think some others also had issues with Dell only booting from one drive. You may need to review manual.

---

### Post by sudodus on 2012-12-31
> **RoverV8 said:**
> I will check BIOS.


Take your time to search for and test several settings in the BIOS menu system :-)
> 
I am booting off a disc as I have not yet installed the OS (I'm using the 'Try Ubuntu' option)

OK, that's already so. This means a fresh system without any bad setting, that you could have caused.
> 
 - I don't pretend to understand partitioning, nothing I can do to it, it seems, will satisfy it such that it will proceed with the installation and would rather wait until I've got the SATA drive up and working.

So far you need not understand partitioning. First we must use our combined efforts to make the computer 'see' the missing HDDs. I agree that you should concentrate on the SATA drive. Maybe try and disconnect the PATA drives, and check if that will make the SATA drive visible.
> 
There are TWO PATA drives, the 250gb one and an older 80gb one - it's only seeing the former. I've already run the command 

sudo fdisk -lu
and posted above what it returned, establishing that the system could see the 250GB drive and a memory card reader (though it was not allowing me to access the hard drive and was not displaying it under File System).
I agree, you can wait with the fdisk command until you have done something else, that might help the computer see the missing disks.

Maybe you will solve the problem yourself, but it helps to discuss it with some other people. Maybe trying to explain clearly to me and others at the Ubuntu Forum will help you see it ;-)

Good luck :KS

---

