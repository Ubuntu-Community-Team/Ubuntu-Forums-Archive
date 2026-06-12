---
title: "Grub error no such partition"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by CharlesJF on 2012-12-23
I've read through many posts related to my issue and have tried several fixes, but I am still having an issue recovering from not removing a linux install properly.

I have an ASUS Eee 1005HAB netbook.  It was pre-installed with XP and did not come with a recovery CD.  About a year or 2 ago, the machine crashed and it would no longer boot up.  I was unable to access the recovery partition for some reason.  In order to get the machine working again, I loaded Linux Mint and things were working fine.  It even was able to provide me access to the recovery partition that was on the machine.  A few days ago I tried to reinstall windows using the recovery partition.  My thought was that I would reinstall windows and then reinstall a linux os as well once that was done.  The windows install seemed to go fine, but when the machine rebooted, I got the "grub error no such partition."  From reading similar posts, I now know that the boot loader is looking for a partition that no longer exists.  I tried to boot from a USB with Mint, but get the same error. I then tried to boot from a USB with Ubuntu and had some success.  I was able to boot and run Ubuntu from the USB, but when I tried to install it on the machine I got the grub error again.  I could really use some help getting this issue resolved.

Thanks.  Charles

---

### Post by fdrake on 2012-12-23
> 
 The windows install seemed to go fine, but when the machine rebooted, I got the "grub error no such partition

i don't understand .. you have a grub error message with just windows installed? can you boot into a live cd and run in the terminal
```

sudo fdisk -l

```or
```

sudo parted -l

```
post the output here

---

### Post by CharlesJF on 2012-12-23
I had a working version of Mint on the machine in the past, so that is why grub is loaded,

The only way i am able to get the machine to boot up at the moment is by booting off a usb that has Ubuntu.  Below are the results of the two commands after booting off the usb.

  	 	 	 	 	 	   Command 1 - sudo fdisk -l
 

 Disk /dev/sda: 160.0 GB, 160041885696 bytes 
 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0xc0bf6260 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *          63   162770579    81385258+   7  HPFS/NTFS/exFAT 
 /dev/sda2       302246910   312496379     5124735    c  W95 FAT32 (LBA) 
 /dev/sda3       312496380   312576704       40162+  ef  EFI (FAT-12/16/32) 
 /dev/sda4       162770580   302246909    69738165   15  Unknown 
  
 Partition table entries are not in disk order 
  
 Disk /dev/sdb: 4167 MB, 4167041024 bytes 
 129 heads, 62 sectors/track, 1017 cylinders, total 8138752 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x20ac7dda 
  
 This doesn't look like a partition table 
 Probably you selected the wrong device. 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT 
 /dev/sdb2   ?  3272020941   930513678   976730017   16  Hidden FAT16 
 /dev/sdb3   ?           0           0           0   6f  Unknown 
 /dev/sdb4        50200576   974536369   462167897    0  Empty 
  
 Partition table entries are not in disk order 
 

 

 Command 2 - sudo parted -l
 

 Model: ATA Hitachi HTS54321 (scsi) 
 Disk /dev/sda: 160GB 
 Sector size (logical/physical): 512B/512B 
 Partition Table: msdos 
  
 Number  Start   End     Size    Type     File system  Flags 
  1      32.3kB  83.3GB  83.3GB  primary  ntfs         boot 
  4      83.3GB  155GB   71.4GB  primary 
  2      155GB   160GB   5248MB  primary  fat32        lba 
  3      160GB   160GB   41.1MB  primary 
  
  
 Model: SKY CSD8300 (scsi) 
 Disk /dev/sdb: 4167MB 
 Sector size (logical/physical): 512B/512B 
 Partition Table: loop 
  
 Number  Start  End     Size    File system  Flags 
  1      0.00B  4167MB  4167MB  fat32 
  
Thanks.

---

### Post by ajgreeny on 2012-12-23
The re-installation of XP obviously did not go as it should have done as there is apparently no windows bootloader, only grub still, and as there is no Linux OS on the disk there is no configuration for grub either.

It used to be possible to reinstall a bootloader for WinXP using a live ubuntu system, but I do not know if it still works.
Try this and let us know whether successful or not for booting windows.
```
sudo apt-get install lilo
```
Ignore the warning then 
```
sudo lilo -M  /dev/sda mbr

```
Now shutdown the live system, reboot and you should be able to boot directly into Windows again if all goes well.

When you had "some success" with installing Ubuntu after XP, at which stage did you then get the grub error;  was it only when you tried to boot windows from grub, or did you get that trying to boot Ubuntu as well?

---

### Post by CharlesJF on 2012-12-23
I ran the commands and rebooted.  It seemed to be working as Windows started its install.  The problem is that the install crapped out mid way through.  I am no longer getting the grub error, but now get an error that I need to re-run the windows install.  Problem is I don't know how to access the recovery partition again.  At the moment, all I can do is run Ubuntu from the USB.

To your question, "some success" meant that I could run Ubuntu off the USB but once I tried to actually install it on my machine, it fails.   Any suggestions?

Thanks.

---

### Post by fdrake on 2012-12-23
> **CharlesJF said:**
> I ran the commands and rebooted.  It seemed to be working as Windows started its install.  The problem is that the install crapped out mid way through.  I am no longer getting the grub error, but now get an error that I need to re-run the windows install.  Problem is I don't know how to access the recovery partition again.  At the moment, all I can do is run Ubuntu from the USB.

To your question, "some success" meant that I could run Ubuntu off the USB but once I tried to actually install it on my machine, it fails.   Any suggestions?

Thanks.
there should be a way to into recovery with a fuction key when you boot same as when you get into safe mode.. check f8 to f12 if they bring up anything

---

### Post by CharlesJF on 2012-12-23
I have tried that and it doesn't work.  The only way I have been able to access the recovery partition was after loading linux and booting through grub.  It allowed me to choose the recovery partition. Unfortunately, I no longer get that option.  So now I can't find a way to access the partition and am not able to load Ubuntu on the machine.  The only thing I can do is boot Ubuntu from a USB and run it from the USB.  I think the recovery partition is still there.  I just need to find a way to access it or to load Ubuntu.

---

### Post by fdrake on 2012-12-23
boot with the live cd and try```

sudo update-grub
```
reboot and see if you have a new option showin up

---

### Post by CharlesJF on 2012-12-23
I get the error below after running the command.

/usr/sbin/grub-probe: error: failed to get canonical path of /cow.

---

### Post by fdrake on 2012-12-23
> **CharlesJF said:**
> I get the error below after running the command.

/usr/sbin/grub-probe: error: failed to get canonical path of /cow.

ops.. I mad a mistake.. you have installed lilo to fix the bootloader. i got confused becaused you called grub.. run again the 2 commands that ajgreeny gave you in post #4

---

### Post by CharlesJF on 2012-12-23
I ran the commands again.  On bootup, it automatically tries to boot windows and I get an error that setup has not completed and to re-run the install.  I need to access the recovery partition to rerun it though.  The only time I was able to access this partition was when I had Linux Mint and grub loaded.  Grub gave me the option to boot linux, windows, or the recovery partition.  However, that was broken when I started the windows recovery and linux got deleted.  Any ideas?

---

### Post by fdrake on 2012-12-23
well you can try then installing grub . with trhe live cd do:
```

 sudo apt-get install grub-pc
 sudo grub-install /dev/sda 
 sudo update-grub 

```

---

### Post by CharlesJF on 2012-12-23
I get this error when executing the second command

Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

---

### Post by oldfred on 2012-12-24
Not sure, but often a recovery expects to see the original drive configuration or mostly one large NTFS Windows partition to reinstall into. It does not reinstal the boot loader, so that is why you still had grub.

But it rewrote partition table? And that will cause issues.

I might try testdisk. But it usually finds multiple version of old partitions and you have to sort out which version of old partitions are what you want. And they cannot overlap with a new version partition.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
    
       repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

    
       Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by CharlesJF on 2012-12-29
Thanks for all the help.  I ended up giving up on trying to recover and reinstall Windows XP and just Ubuntu instead.  It installed fine and now I am up and running.

---

