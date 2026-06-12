---
title: "Moove the /boot folder"
date: 2021-05-25
forum: New to Ubuntu
---

### Post by kreace on 2021-05-25
Hello guys,

I'm quite new to Linux so I might have made mistakes when installing my Ubuntu partition.
At the start I had two drives, one SSD(250Go) with W10 on it, and a HDD(1To) with Ubuntu on it and some files.
Then I purchased a NVMe(1To) and cloned W10 on it, then I deleted the Ubuntu partition on the HDD and install it again on the SSD.
And few days ago, my HDD started to make a lot of noise so I decided that I'll disconnect it and use it only when I will need it.
But now I couldn't boot on the Ubuntu partition. 
I think some folders ( the /boot and /) are still on the HDD.

I put some screenshots of GParted of the HDD (sda) and the SSD (sdb) in attachment.

So I have few questions :

1- First of all am I understanding correctly the situation : The /boot folder is on my HDD so when I try to boot on Ubuntu the system need to look at this folder on the HDD?
2- How I can transfer these folders (/boot and /) on my SSD?

Ideally, I would like to have this configuration : NVMe W10, SSD Ubuntu, HDD storage

I hope I put everything you need to answer my question, thanks in advance to read it, if you need something else to help me, please ask.

Have a great day.

---

### Post by yancek on 2021-05-25
Windows 10 is generally an EFI install and on sda you have 2 efi partitions when you should have only 1.  sdb has your Ubuntu system and has an extended partition which would indicate it was installed in Legacy mode.  When you install Ubuntu on a computer which is efi, you need to install it in efi mode which it does not appear to be.  Are your drives gpt or msdos?  If you aren't sure run the following command which will tell you what each drive is.  Post the output here.

```
sudo parted -l
```

That's a lower case letter L in the command.

If your system is efi, you will have efi boot files for both windows and Ubuntu on the efi partition.  Try mounting sda2 and sda3 to see what is there, if anything.  You have extended partitions on both drives which would not generally happen with a gpt drive.

The link below is the official documentation of Ubuntu to dual boot efi with windows 10.  You might take a look at that to see how it compares to what you have done.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you are unable to resolve this issue, it might be best to go to the site at the link below and download and run boot repair.  Use the 2nd option on that page to download it and select the option to Create BootInfo Summary and post the link you get when it finishes here.  Do not try to make any repairs..

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by kreace on 2021-05-25
Hello @yancek and thanks for your answer.
I thought that all my drives where GPT but after typing the result of the command told me that only my NVMe is, the SSD and HDD are msdos.

My system is EFI I ran : 
```

ls /sys/firmware/efi

config_table  esrt              fw_vendor  runtime-map  vars
efivars       fw_platform_size  runtime    systab

```
The folder exist so my system is EFI.

sda2 is like this : 
```

sudo mount /dev/sda2 /home/chris/sda2/

ls sda2/
'$RECYCLE.BIN'   EFI  'System Volume Information'

```

sda3 is like this :
```

sudo mount /dev/sda3 /home/chris/sda3/

sudo ls sda3/
'$RECYCLE.BIN'     Recovery      'System Volume Information'
 EFI         Recovery.txt   Temp

```
I needed to run it as sudo else I got a permission denied.

Hope this will help you to solve the problem.

I think my mistake was when I created the bootable key and I chose the wrong type of drive.

---

### Post by yancek on 2021-05-25
You have windows partitions and 2 EFI partition on sda as well as a LInux(Ubuntu) install on that drive as a logical partition (sda5) within the Extended partition sda4.  You also have a Linux ext4 filesystem on sdb5 drive.  Can't tell form the info you posted if you have two Ubuntu's or something else?  When you mount sda2 and sda3, you need to go into the EFI folder to see what is there.  Should have windows and Ubuntu files there for EFI.  Post that info here.  Windows installed EFI mode would need to be on a GPT drive.

---

### Post by kreace on 2021-05-26
So on sda2 : 

```

chris@chris:~/sda2/EFI$ ls
BOOT  ubuntu
chris@chris:~/sda2/EFI$ ls ./ubuntu/
BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi
chris@chris:~/sda2/EFI$ ls ./BOOT/
bkpbootx64.efi  bootx64.efi  fbx64.efi  grubx64.efi  mmx64.efi

```

on sda3 : (had to go on root because I didn't have the permission to cd into it) 

```

root@chris:/home/chris/sda3# cd EFI/
root@chris:/home/chris/sda3/EFI# ls
BOOT  ubuntu
root@chris:/home/chris/sda3/EFI# ls ubuntu/
BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi
root@chris:/home/chris/sda3/EFI# ls BOOT/
BOOTX64.EFI  fbx64.efi  mmx64.efi

```

---

### Post by yancek on 2021-05-26
The information you posted in post 5 above shows only an Ubuntu entry on the EFI partition.  When you list files/folders in the EFI partition, there should be a folder named Microsoft which contains the windows EFI boot files.  That doesn't show in your output so if that is accurate, windows is not an EFI install.

You forgot to post the output of:  sudo parted -l
Also post the output of: sudo efibootmgr -v

---

### Post by kreace on 2021-05-26
It's just that the EFI partition for windows is on the NVMe on /dev/nvme0n1p2, it's normal I think because windows is on my NVMe. Maybe you could have the info with the following command, my bad I didn't put it before.

```

chris@chris:~$ sudo parted -l
Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size   Type      File system  Flags
 1      1049kB  790GB   790GB  primary   ntfs
 2      790GB   791GB   538MB  primary   fat32        esp
 3      791GB   792GB   538MB  primary   fat32        boot, esp
 4      792GB   1000GB  209GB  extended
 5      792GB   1000GB  209GB  logical   ext4


Model: ATA SanDisk SDSSDA24 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 2      1048kB  240GB  240GB  extended
 5      1049kB  240GB  240GB  logical   ext4
 1      240GB   240GB  537MB  primary   ntfs         msftres


Model: CT1000P2SSD8 (nvme)
Disk /dev/nvme0n1: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2312MB  2311MB  ntfs               diag
 2      2313MB  2749MB  436MB   fat32              boot, esp
 3      2749MB  2766MB  16,8MB                     msftres
 4      2767MB  1000GB  997GB   ntfs               msftdata
 5      1000GB  1000GB  578MB   ntfs               hidden, diag

```

```

chris@chris:~$ sudo efibootmgr -v
BootCurrent: 0017
Timeout: 1 seconds
BootOrder: 0015,0000,0016,0017,000A,0010,0018
Boot0000* Windows Boot Manager    HD(2,GPT,2867d4d3-b3a5-4ac5-a18a-3772083f713b,0x44f000,0xcff17)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot000A* SanDisk SDSSDA240G    BBS(HD,,0x0)..BO
Boot0010* CT1000P2SSD8    BBS(HD,,0x0)..BO
Boot0015* ubuntu    HD(2,GPT,2867d4d3-b3a5-4ac5-a18a-3772083f713b,0x44f000,0xcff17)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0016* ubuntu    HD(2,MBR,0xc0caac29,0x5c066000,0x100800)/File(\EFI\ubuntu\shimx64.efi)..BO
Boot0017* ubuntu    HD(3,MBR,0xc0caac29,0x5c166800,0x100800)/File(\EFI\ubuntu\shimx64.efi)..BO
Boot0018* ST1000DM003-1ER162    BBS(HD,,0x0)..BO

```

---

### Post by yancek on 2021-05-26
What happens when you access your BIOS firmware boot options?  Are you able to boot Ubuntu with any of the 3 options shown by efibootmgr output (Boot0015, Boot0016, Boot0017)/

If you can't resolve this I would suggest you download and run boot repair from the link above in post 2.  Use the 2nd option to download using your Ubuntu install media and select the option to Create BootInfo Summary, do NOT try to make any repairs.

---

### Post by tea for one on 2021-05-26
As you are new to Ubuntu and you probably do not have much data saved yet, I would recommend that you re-install Ubuntu on your SSD.

Your nvme dive with Windows is UEFI with GPT and I assume that it boots and functions OK?
Therefore, install Ubuntu on your SSD in UEFI mode with GPT.

Having OS systems on separate drives is ideal.
It is also good practice to isolate, de-activate or remove your Windows drive when installing Ubuntu to prevent bootloader conflict and avoid human error.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by kreace on 2021-05-27
Here are the boot options that I have : (the 2nd from the top "ubuntu P0:ST1000...." lead me to the partition that I want)
I don't know exactly which one correspond to the boot option that efibootmgr shows.
I'll try to see what boot repair can do but as you mention I will not start any repair.

I have several software installed here so It would be great to not reinstall everything because it takes quite a lot of time.
And yeah Windows is working correctly.

Here is the result of the BootInfoSummary 

[https://paste.ubuntu.com/p/rb939vZmxF/](https://paste.ubuntu.com/p/rb939vZmxF/)

---

### Post by yancek on 2021-05-27
>  Here are the boot options that I have : (the 2nd from the top "ubuntu P0:ST1000...." lead me to the partition that I want)

If you can boot Ubuntu by selecting that option in the BIOS firmware that's the way you will have to do it.  When you want windows, select the windows option in the BIOS firmware.  
Part of the problems is that you have 3 EFI partitions, one on the windows drive and 2 on the Ubuntu drive.   Boot0015 from efibootmgr is on the same drive as windows so you likely had the windows drive attached during one of the Ubuntu installs. 

You may be able to convert sda to GPT but might result in loss of data.  I'd do an online search for converting Ubuntu to GPT without loss of data and see what you can find.

---

