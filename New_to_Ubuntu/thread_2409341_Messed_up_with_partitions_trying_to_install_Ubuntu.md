---
title: "Messed up with partitions trying to install Ubuntu and now I can't boot in Windows."
date: 2018-12-31
forum: New to Ubuntu
---

### Post by DaDiRa on 2018-12-31
Long story short, I was trying to install Ubuntu for dual boot in UEFI using a live USB. I tried to follow a tutorial about partition, but being almost clueless, I somehow messed up the partitioning. Ubuntu seemed to have installed correctly but after the restart I got a "Reboot and select proper boot device" message. I tried resetting the Bios settings (I had actually only changed the fast boot option) and changing boot order but the problem remained. I then proceeded to format and delete the partitions I had created while I was trying to install Ubuntu, leaving only the 3 ntfs partitions from Windows 10.
What's weird is that in the BIOS the third boot option "Ubuntu" remained even after that, along with the proper boot device error. I've been googling and searching for a while now but I'm not even sure I can identify the actual cause before I can start working on solving it. I read about activating a certain partition or recovering old partitions or repairing the disk but I can't figure out which one I should do and how. I would be grateful if I could get away without having to format my HDD, but I'm willing to do it if it's the only option.

I'm currently running Ubuntu through the live USB I had prepared, since it's the only way I can boot into an OS. I'm posting a screenshot from GParted and the output of ```
sudo fdisk -lu
``` (which I don't know what it is but I saw it was asked in another thread). I'm not very familiar with Ubuntu (especially after the UEFI thing that made dual boot a nightmare for me) so let me know if there is anything else I can do to help you help me.

[ATTACH=CONFIG]282065[/ATTACH]
```
**Disk /dev/loop0: 1.8 GiB, 1864450048 bytes, 3641504 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


**Disk /dev/loop1: 86.9 MiB, 91099136 bytes, 177928 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


**Disk /dev/loop2: 34.7 MiB, 36323328 bytes, 70944 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


**Disk /dev/loop3: 140.9 MiB, 147722240 bytes, 288520 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


**Disk /dev/loop4: 2.3 MiB, 2433024 bytes, 4752 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


**Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


**Disk /dev/loop6: 14.5 MiB, 15196160 bytes, 29680 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


**Disk /dev/loop7: 3.7 MiB, 3887104 bytes, 7592 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


**Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x484dbd17

**Device**     **Boot** **    Start** **      End** **  Sectors** **  Size** **Id** **Type**
/dev/sda1            2048   1026047   1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048 936746751 935720704 446.2G  7 HPFS/NTFS/exFAT
/dev/sda3       975808512 976769023    960512   469M 27 Hidden NTFS WinRE




**Disk /dev/sdb: 14.9 GiB, 16013852672 bytes, 31277056 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0837490a

**Device**     **Boot** **Start** **     End** ** Sectors** ** Size** **Id** **Type**
/dev/sdb1  *     2048 31277055 31275008 14.9G  c W95 FAT32 (LBA)


**Disk /dev/loop8: 409.5 MiB, 429359104 bytes, 838592 sectors**
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

---

### Post by oldfred on 2018-12-31
You are showing a MBR(msdos) partitioned drive which means Windows is in BIOS boot mode.
Windows only can boot in UEFI boot mode from a gpt partitioned drive.

You always want to install Ubuntu in the same boot mode as Windows. But why is Windows in BIOS boot mode, if hardware is UEFI? Microsoft has required vendors to install Windows in UEFI boot mode (with gpt) on all new systems since Windows 8 released 5 years ago.

UEFI & BIOS are really incompatible. Only if separate drives and only booting from UEFI/BIOS can you dual boot in different boot modes.

So you can install Ubuntu in BIOS boot mode. 
Or if you have not spent a lot of time configuring Windows and installed it yourself you can reinstall in UEFI boot mode.

For both Windows & Ubuntu how you boot install media, UEFI or BIOS, is then how it will boot once installed.

---

### Post by DaDiRa on 2019-01-01
I had no idea about this. I installed windows 10 on my own, so it's my fault. But it's been 3 years since then.
Anyway, I figured it is better to format the disk, convert to GPT and install windows 10 all over again. My questions know are:
1) How can I make sure that windows 10 where correctly installed as UEFI this?
2) What guide/tutorial should I follow to install Ubuntu dual boot without messing it up again?

---

### Post by oldfred on 2019-01-01
From a new UEFI system you will have two boot modes, both for USB installer and then once installed as default boot settings. You need to make sure you boot in UEFI mode to install and then have UEFI boot mode as default once installed. 
Some details on Ubuntu UEFI install and links to lots more info in link in my signature.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

If you have any data on drive, be sure to fully back that up. Windows conversion from MBR to gpt will erase entire hard drive.
 
Default install of Ubuntu now is just / (root) as ext4 formatted. If UEFI it will also want an ESP - efi system partition  (FAT32). But you can only have one ESP per drive, so do not make duplicate. Ubuntu & Windows will share an ESP without issue, but have different folders.
If very new user, larger root is ok. But if bit more experiences smaller / like 25 or 30GB and large /home and perhaps larger shared data partition (NTFS) may be desired. 
But make sure Windows fast start up/hibernation is off. It sets hibernation flag on all NTFS partitions and Linux NTFS driver will not mount(see) any NTFS partitions.

---

### Post by yancek on 2019-01-01
Ubuntu has a site which is the official documentation on installing Ubuntu UEFI/GPT with windows.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

