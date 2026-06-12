---
title: "Can't mount USB stick"
date: 2014-09-20
forum: New to Ubuntu
---

### Post by michal10 on 2014-09-20
Hi, just recently my hard drive broke, so using Unetbootin I made a bootable pendrive (4gb) with Ubuntu. Everything's working fine, but I'd like to install DOTA 2 (10gb) from Steam on another pendrive (32gb). Both pendrives are fat32 and to install the game Steam requires execute permissions. Not sure if that's true, but I read I'm unable to set such permissions on fat32, so I tried formatting the bigger pendrive with NTFS or ext4 filesystem, but then I'm unable to mount it due to "bad superblock". I'm rather new to Linux, so a 'noob' explanation would be much appreciated.

---

### Post by sandyd on 2014-09-20
Moved to *New to Ubuntu*

---

### Post by yancek on 2014-09-20
Are you trying to use unetbootin to create a Live CD of Ubuntu with persistence on the larger flash drive or are you trying to do an actual install of Ubuntu on the 32GB flash.  If it is the latter option, you will need a Linux filesystem and ext2, ext3 or ext4 should work.

---

### Post by michal10 on 2014-09-20
I used unetbootin to create bootable pendrive with Ubuntu, it's not installed, I have a fresh system each time I reboot so I belive it's loaded onto RAM memory. The system is working fine, all I want to do is install the game on another flash drive, but the game requires execute permissions. I can only mount the flash drive when it's FAT32 though, when I try to format it to ext3 or ext4, I am then unable to mount it.

---

### Post by sudodus on 2014-09-20
Is this a temporary solution, or do you intend to run the computer this way for a longer period of time?

What brand and model is the 32 GB pendrive?

If it is only for a short time, I think you can boot from the 4 GB pendrive and use that 32 GB pendrive for the installation of DOTA. Let it be formatted to **ext4** and mount it manually with ***sudo mount*** or via **/etc/fstab**

Identify the drive with

```
sudo blkid
```

make a mount point

```
mkdir /mnt/dota
```

and mount it

```
sudo mount /dev/sdxy /mnt/dota
```

where x is the device letter and y is the partition number identified via ***sudo blkid***

It is even better to use the UUID to identify the partition to be mounted, can also be found in the output of ***sudo blkid***

```
sudo mount -U a-long-string-of-hex-numbers /mnt/dota
```

If this works, you can come back and get help to make it survive reboots using **/etc/fstab**

---

### Post by michal10 on 2014-09-20
It is temprairly, just until I get a new HDD. I don't know the brand is this pendrive, in propeties it only says 'generic flash disk'. This is what happens when I try to format it using ext4. 

[IMG]https://imagizer.imageshack.us/v2/1129x638q90/901/027PCo.png[/IMG]

And this is what happens when I try to mount afterwards. 

[IMG]https://imagizer.imageshack.us/v2/1129x638q90/907/PlKxzy.png[/IMG]

When I try to mount in terminal using your instructions this is what I get :

root@ubuntu:~# mkdir /mnt/dota
root@ubuntu:~# sudo mount -U 33d45961-74d2-444a-b095-309a1db56be8 /mnt/dota
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by irv on 2014-09-20
Why don't you boot with the live OS off the 4 gig USB Plug in the 32 gig USB and run gparted. Make sure you have the right USB and partition it and format it from there. If you set it to ext4 you should be able to unplug it and when you plug it back in it should mount.

---

### Post by michal10 on 2014-09-20
The same message appears when I do that. 
"Error mounting /dev/sdb1 at /media/ubuntu/6b6cf36b-939b-4970-8910-b69dce2e3897: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/ubuntu/6b6cf36b-939b-4970-8910-b69dce2e3897"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Here's what gparted says about the drive. 
[IMG]https://imagizer.imageshack.us/v2/735x415q90/538/qMvmyx.png[/IMG]

---

### Post by sudodus on 2014-09-21
Maybe there is something ugly in the partition table (or elsewhere in the head end) of the 32 GB pendrive's memory. Such problems can often be fixed by wiping the first megabyte.

1. Install ***mkusb*** and wipe the first megabyte. See this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

2. Then use ***gparted*** to create a new partition table

Device -- Create Partition Table

(It is OK with the standard MSDOS partition table unless you run in a computer with UEFI. Then you should use a GPT partition table.)

And after that create a partition and put an ext4 file system into it.

---

### Post by michal10 on 2014-09-21
Unfortunately that didn't help. Is it possible that the pendrive itself only operates under fat32?

---

### Post by sudodus on 2014-09-22
No I don't think so.

What pendrive is it, brand name and model?

How did you try to repair the pendrive's partition table and file system?

What is the problem now? Is it that you cannot create the file system, or that you cannot mount the pendrive or something else?

Please reply as detailed as possible to those questions, and also,

please post the output of the following commands

```
sudo parted -ls
```

and

```
sudo blkid
```

-o-

Read more about USB pendrives at the following link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

