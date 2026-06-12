---
title: "Secure Boot Problem"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by Equinox05 on 2013-07-09
I have a HP p7-1234 with Windows 8 Pro. I've been trying to put Ubuntu 13.04 on it for 2 days now and can't get it to work. I have narrowed it down to the Secure Boot option, but when I startup my computer it does not have the option even listed to disable it!!!!!!!! It's literally driving me crazy. I don't think my computer "knows" if it has Windows 8 because when I installed Ubuntu it said install Ubuntu alongside WINDOWS 7 which is what OS I bought the in.                                                                                                                  






Thanks in Advanced,
Equinox

---

### Post by fantab on 2013-07-09
Can you boot with Ubuntu Install DVD/USB and 'Try Ubuntu without installing'?
If yes, then boot with it and opt to 'Try Ubuntu'. From the desktop open Terminal [Ctrl+Alt+T] and run the following command:

```
sudo parted -l
```

If you can't for some reason, then post the Screeshot of your HDD and its partitions from Windows Disk Management.

---

### Post by Equinox05 on 2013-07-10
I don't know what it's really telling me here. But it gave me this:


```

buntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  106MB   105MB   fat32           EFI system partition          boot
 2      106MB   240MB   134MB                   Microsoft reserved partition  msftres
 3      240MB   565GB   565GB   ntfs            Basic data partition
 6      565GB   565GB   1049kB
 7      565GB   958GB   393GB   ext4
 8      958GB   966GB   8039MB  linux-swap(v1)
 4      966GB   982GB   15.7GB  ntfs            Basic data partition
 5      982GB   1000GB  18.0GB  ntfs            Basic data partition


Model: pny USB 2.0 FD (scsi)
Disk /dev/sdf: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      5399kB  16.0GB  16.0GB  primary  fat32        boot, lba
```

---

### Post by oldfred on 2013-07-10
Since you have gpt partitioning and an efi partition, Windows is in UEFI mode to boot. If you originally had Windows 7 you may not have secure boot. Only systems purchased with Windows 8 have secure boot.
Some just have settings for Secure Boot, UEFI, CSM or BIOS and others combine settings often in confusing ways.

Best to see details. 
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Equinox05 on 2013-07-10
THANK YOU SO MUCH!!!!!!!! It worked the GRUB scared me though (I thought i lost windows 8) XD.   Thanks for both of you helping me. :D  :-P

---

