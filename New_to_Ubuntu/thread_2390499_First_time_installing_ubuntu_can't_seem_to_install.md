---
title: "First time installing ubuntu can't seem to install it"
date: 2018-04-29
forum: New to Ubuntu
---

### Post by alekseycs on 2018-04-29
Hi I've always used ubuntu command line and now installing the os 1804 onto my laptop as I've had issues with windows, after installing it would hit the bios screen and turn itself off. When I plug the USB back in I get the black screen with white text saying along the lines of test ubuntu, install ubuntu, install ubuntu (oem). When I click install again I can rebooted into the installation and I attempt again but I can't seem to get it to install.


I tried checking the partitions but I have no idea what I am doing, so I formatted them to test but still can't install it to my laptops hdd.

---

### Post by alekseycs on 2018-04-29
pictures of the drives:
[https://imgur.com/a/14ofDZl](https://imgur.com/a/14ofDZl)

it'll only boot when the USB is plugged in and I run it in test ubuntu mode

---

### Post by mörgæs on 2018-04-29
The command ```
df -h
``` gives a better overview of the partitions. 

Please use CODE tags when posting the output.

---

### Post by alekseycs on 2018-04-29
> **mörgæs said:**
> The command ```
df -h
``` gives a better overview of the partitions. 

Please use CODE tags when posting the output.

```
ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           781M  1.6M  779M   1% /run
/dev/sdb1       7.5G  1.8G  5.7G  25% /cdrom
/dev/loop0      1.8G  1.8G     0 100% /rofs
/cow            3.9G  356M  3.5G  10% /
tmpfs           3.9G     0  3.9G   0% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs           3.9G  516K  3.9G   1% /tmp
tmpfs           781M   64K  781M   1% /run/user/999
/dev/loop1       87M   87M     0 100% /snap/core/4486
/dev/loop2      141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop3      1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop4       13M   13M     0 100% /snap/gnome-characters/69
/dev/sda2       916G  5.9G  863G   1% /media/ubuntu/2c6f27ec-2c92-4479-9e85-7b27623b197c
/dev/loop5       21M   21M     0 100% /snap/gnome-logs/25
/dev/loop6      3.4M  3.4M     0 100% /snap/gnome-system-monitor/36


```

---

### Post by alekseycs on 2018-04-29
I have spent four hours attempting to figure this out and getting nowhere. From what I can see my usb is /sda and my actual hdd is /sdb2.

---

### Post by oldfred on 2018-04-29
Depending on whether you just plug in a flash drive or reboot with it plugged in, may change drive boot order. That is why UUID is preferred to be sure to use correct device.

You show a large 916GB partition as sda2.
Is sda1 then a Windows boot partition?
And then is drive MBR, so Windows has to be booting in BIOS/Legacy mode?
What version of Windows.
Is hardware UEFI or BIOS?

Post this also:
sudo parted -l

---

### Post by yancek on 2018-04-29
> From what I can see my usb is /sda and my actual hdd is /sdb2. 				

sdb2 shows as 7.%GB which would be an 8GB flash drive.  Your sda, from the df -h output shows as 916GB.  I don't think they make flash drives that large, yet.
In addition to answers to the questions above, you might try booting the Ubuntu usb and from a terminal, run the command below and post the output:

> sudo gdisk -l /dev/sda

---

### Post by alekseycs on 2018-04-30
> **yancek said:**
> sdb2 shows as 7.%GB which would be an 8GB flash drive.  Your sda, from the df -h output shows as 916GB.  I don't think they make flash drives that large, yet.
In addition to answers to the questions above, you might try booting the Ubuntu usb and from a terminal, run the command below and post the output:

```

ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
 GPT fdisk (gdisk) version 1.0.3
  
 Partition table scan:
   MBR: MBR only
   BSD: not present
   APM: not present
   GPT: not present
  
  
 ***************************************************************
 Found invalid GPT and valid MBR; converting MBR to GPT format
 in memory. 
 ***************************************************************
  
  
 Warning! Secondary partition table overlaps the last partition by
 33 blocks!
 You will need to delete this partition or resize it in another utility.
 Disk /dev/sda: 15630336 sectors, 7.5 GiB
 Model: Cruzer Facet    
 Sector size (logical/physical): 512/512 bytes
 Disk identifier (GUID): 246023DD-1758-4CA5-9352-DAE59EB5C715
 Partition table holds up to 128 entries
 Main partition table begins at sector 2 and ends at sector 33
 First usable sector is 34, last usable sector is 15630302
 Partitions will be aligned on 2048-sector boundaries
 Total free space is 2014 sectors (1007.0 KiB)
  
 Number  Start (sector)    End (sector)  Size       Code  Name
    1            2048        15630335   7.5 GiB     0700  Microsoft basic data
```

This is being booted from the "try ubuntu" option as I can't boot from my hard drive


On my HDD I am stuck in a boot loop (picture below of a frame before it resets) I am not to sure how to fix it.
[https://imgur.com/a/n4s8OtZ](https://imgur.com/a/n4s8OtZ)

---

### Post by oldfred on 2018-04-30
The gdisk output says you have a MBR(msdos) partitioned drive, but the backup gpt partition table overlaps the last partition.

Did you use Windows to convert from gpt to MBR. Windows automatically does that if you install Windows 7 over Windows 8 or 10. Or re-install any version of Windows in BIOS/MBR mode when system was originally UEFI/gpt.
Windows does not correctly convert drive from gpt to MBR. It leaves the backup gpt partition table. Then Linux tools do not know for sure if drive is MBR or gpt and often fail. You need to run fixparts.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

