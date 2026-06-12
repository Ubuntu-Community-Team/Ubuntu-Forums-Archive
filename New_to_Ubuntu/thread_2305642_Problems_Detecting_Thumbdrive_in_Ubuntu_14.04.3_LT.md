---
title: "Problems Detecting Thumbdrive in Ubuntu 14.04.3 LTS"
date: 2015-12-07
forum: New to Ubuntu
---

### Post by lee-wei-de on 2015-12-07
Hi everyone! :) 
 
Recently, I have been using Ubuntu 14.04.3 LTS to diagnose my thumbdrive, which failed to get detected by Windows 7/8 after being safely ejected from a Mac. 
 
The same problem surfaced in Ubuntu 14.04.3 LTS, in that when I plugged in my thumbdrive, running dmesg on Terminal showed that the thumbdrive has been detected, with the following message shown below: 

```
[  877.012162] usb 2-6: new high-speed USB device number 5 using ehci-pci
[  877.144898] usb 2-6: New USB device found, idVendor=abcd, idProduct=1234
[  877.144904] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  877.144908] usb 2-6: Product: UDisk           
[  877.144911] usb 2-6: Manufacturer: General 
[  877.144914] usb 2-6: SerialNumber: 1312272015495735275011
[  877.145640] usb-storage 2-6:1.0: USB Mass Storage device detected
[  877.146261] scsi host7: usb-storage 2-6:1.0
[  899.156154] usb 2-6: reset high-speed USB device number 5 using ehci-pci
```

Strangely, when I did a "sudo fdisk -l", I am unable to find my thumbdrive, i.e. it is not mounted. The messages below are what I see when I did a "sudo fdisk -l":
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00066786

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   405506047   202752000    7  HPFS/NTFS/exFAT
/dev/sda2       405506048   543221759    68857856    7  HPFS/NTFS/exFAT
/dev/sda3       543221760   625137663    40957952    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0825c156

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    31266815    15632384    c  W95 FAT32 (LBA)
```

The 16GB thumbdrive is the drive I use to boot Ubuntu. The 320.1GB drive is my internal laptop hard disk.

When I did a "lsusb", the following messages are returned:

```
Bus 002 Device 005: ID abcd:1234 Unknown 
Bus 002 Device 004: ID 04f2:b033 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0781:5575 SanDisk Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 04fc:00d5 Sunplus Technology Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 005 Device 004: ID 0b05:1751 ASUSTek Computer, Inc. BT-253 Bluetooth Adapter
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

The first line should be the line for my USB disk.

Just a little background info, my thumbdrive is brandless, hence it may explain why the vendor and product IDs listed in dmesg are so strange. :X

May I ask, is there any way to force mount my volume in Ubuntu 14.04.03 LTS, so as to access the files in my thumbdrive? I don't need write access to my thumbdrive, just read-only and the ability the copy files out of my thumbdrive. :(

Thank you very very much! :)

-Galaxy_Twirl

---

### Post by sudodus on 2015-12-08
The thumbdrive is ***not*** detected as a mass storage device, **/dev/sdx**, where x is the drive letter. It means that there are serious problems, that cannot be managed with 'tools that are available for you and me', at least not in that computer. You can try in other computers, but it may be damaged beyond repair.

See this link: [Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by lee-wei-de on 2015-12-08
Hi sudodus. Thank you very much for your reply. :)

Just wondering, if I were to reconstruct the partition table via the "wipe only the first megabyte" option as stated in the guide under "Pendrive lifetime" above, will I be able to recover files from my thumbdrive?

Thanks again! :D

---

### Post by sudodus on 2015-12-08
If you need to recover files, I think you need to see the pendrive as a mass storage device, /dev/sdx, where x is the drive letter. There are specialized companies, that use advanced tools, and they can recover files beyond what can be done with 'tools that are available for you and me', but the cost is high.

Anyway, I think the best tool available in this case is ***photorec***. Get an iso file for a repair drive and try, but I'm afraid it will not work unless you find a computer that can see the pendrive as a mass storage device, /dev/sdx.

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

-o-

Finally,*** if you want to recover files, you should not wipe the first megabyte. You should not wipe anything***. The best method is to make a cloned copy of the drive and work on the copy. The info manual of ***ddrescue*** is a good help for recovering data from failing drives. But also in this case it must be seen as a mass storage device.

```
sudo apt-get install gddrescue
```

```
info ddrescue
```

[online manual for ddrescue](https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html)

---

### Post by BobUgh on 2015-12-08
> **lee-wei-de said:**
> Hi sudodus. Thank you very much for your reply. :)

Just wondering, if I were to reconstruct the partition table via the "wipe only the first megabyte" option as stated in the guide under "Pendrive lifetime" above, will I be able to recover files from my thumbdrive?

Thanks again! :D

1) I personally can't read this thread and understand which device is which, &#8230; too much info on devices that are not the problem that I can not personally filter out. So I got lost. I am responding mostly to **your latest question about recovering files**.

If when you plug your thumb drive into a machine and the machine DOES detect it but fails to auto-mount it (ie. if it creates a new /dev/sd[a-z]  but not any new /dev/sd[a-z]n (if I remember right, that is ubuntu's disc naming convention, different OSs do it differently)  ), that is very different than the machine not detecting it&#8230;

In the first case, if your machine is creating a /dev/sd[a-z] entry but your filer isn't mounting any partitions, and you want to recover files from it, you next step is probably to use something like **Gnu ddrescue** before you do anything further to the thumb drive. After ddrescue does what it can but if it isn't totally successful, there are further recovery programs that try to piece together fragments of photo files etc. **It mostly depends how important the files on the thumb drive are**. You might even avoid trying it on various systems as one system might try running file system check on it - although that might fix it. Depends on how the drive is formatted, for example, some (older?) OSX systems will usually mount NTFS formatted partitions read-only, but if the NTFS formatted partition needs a file system check, it couldn't check a NTFS so it doesn't mount it. I could imagine Ubuntu doing likewise if the partition is formatted for Mac.

If it is the second case, you are not even getting a new /dev/sd[a-z] entry under Ubuntu, then what to do is above my level of expertise.

You said you ejected it safely from a Mac, what OS was the Mac running? Is the thumb drive formatted anything different than factory settings? If it is formatted for Mac and it previously worked in a Mac running OSX, what happens when you plug it into the Mac? You may have to look in OSX's console as you plug it in. If you get messages that it "can not enumerate a usb device", your problem is above my level. If you don't get any messages, does it get mounted?  If not then maybe you could use OSX's disk utility to check the drive. Under OSX, you get new /dev/disk[0-9] entries for usb disks, and /dev/disk/[0-9]s[1-9] entries for partitions.

And excuse my ignorance, but does pendrive mean the same thing as thumb drive?

---

### Post by sudodus on 2015-12-08
Pendrive means the same as thumb drive for me.

---

