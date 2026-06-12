---
title: "Ubuntu 14.04.1 does not detect Windows 7 during installation"
date: 2014-11-23
forum: New to Ubuntu
---

### Post by george91 on 2014-11-23
Hello everyone,

I recently got tired with Windows and decided to try Ubuntu. However since I am new to this I don't want to completely delete Windows. While trying to dual boot Ubuntu I expected the installer to ask me if I want to install it next to my Windows installation. That did not happen. I searched the web and found several posts from people having the same problem but they were using terms I don't know and commands I am afraid to use so I am asking for your help. Can you please guide me to figure out the problem? Thank you in advance.

---

### Post by sandyd on 2014-11-23
> **george91 said:**
> Hello everyone,

I recently got tired with Windows and decided to try Ubuntu. However since I am new to this I don't want to completely delete Windows. While trying to dual boot Ubuntu I expected the installer to ask me if I want to install it next to my Windows installation. That did not happen. I searched the web and found several posts from people having the same problem but they were using terms I don't know and commands I am afraid to use so I am asking for your help. Can you please guide me to figure out the problem? Thank you in advance.

Hi, can you go to the terminal (Unity Dash -> Type in 'Terminal'), and post the output to the following commands?

```

sudo fdisk -l
sudo parted -l
```
Thanks!

---

### Post by krizna on 2014-11-24
Hi,
I had the same issue . i created free space and started installing ubuntu 14.04.1 and it does not detect windows 7 while installing .
After installation i tried this command in terminal and rebooted .
```
sudo update-grub
```
After reboot, i can see windows 7 option in my grub .

---

### Post by mastablasta on 2014-11-24
follow sandyd advice. the commands will show us how your disk is currently setup (partitions).


[LIST]
[*]sometimes the installer would now show that option if there are already (max) 4 primary partitions setup (which is the usual way in preinstalled windows computers).
[*]sometimes there is still one primary partition available, and the installer still doesn't show that option. if that is the case, manual install will work just fine and we can guide you through it.
[/LIST]


to get the option to show one needs:

[LIST]
[*]on old MBR partition scheme less than 4 primary partitions have to be occupied
[*]free unformatted disk space available (where the OS will be installed)
[/LIST]

---

### Post by george91 on 2014-11-26
Hey guys. Sorry for not responding to your answers. After creating the thread I continued researching the web about what to do, came across the partition section on the official Ubuntu site, read all about what kind of partitions I had to make and did it. I guess I was afraid to do it without someone confirming that what I was doing was right. I gutted up and did it and it worked. Updated grub after installation and everything works like a charm. I love it and the next desktop I am building will run a linux os from the very start. 

However since I am trying to learn here is what you asked for ( with Ubuntu installed though )

```
george@george-laptop:~$ sudo fdisk -l
sudo: unable to resolve host george-laptop
[sudo] password for george: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x23692471

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   409804799   204798976    7  HPFS/NTFS/exFAT
/dev/sda3       409806848   850939903   220566528    7  HPFS/NTFS/exFAT
/dev/sda4       850941950   976771071    62914561    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       850941952   866940927     7999488   82  Linux swap / Solaris
/dev/sda6       866942976   976771071    54914048   83  Linux

Disk /dev/sdb: 4102 MB, 4102029312 bytes
255 heads, 63 sectors/track, 498 cylinders, total 8011776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     8011772     4005855    b  W95 FAT32
```


```
george@george-laptop:~$ sudo parted -l
sudo: unable to resolve host george-laptop
Model: ATA Hitachi HTS54755 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   210GB  210GB   primary   ntfs
 3      210GB   436GB  226GB   primary   ntfs
 4      436GB   500GB  64.4GB  extended
 5      436GB   444GB  8191MB  logical   linux-swap(v1)
 6      444GB   500GB  56.2GB  logical   ext4


Model: JetFlash TS4GJFV10 (scsi)
Disk /dev/sdb: 4102MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4102MB  4102MB  primary  fat32        boot
```


Can you see what was wrong by this? If you do please explain.

Thank you guys ;)

@mastablasta 
I had free unformatted space when I was trying to install it. The partitions I had where 1 System reserve which i had no idea what it was, 1 for C:/, 1 for D:/ and the free unalocated space where I intended to install Ubuntu

---

### Post by flaymond on 2014-11-27
[B]george@george-laptop:~$ sudo fdisk -l
sudo: unable to resolve host george-laptop
[sudo] password for george: 



^

Hello,when I saw the "sudo: unable to resolve host george-laptop", I think you might change the DNS hostname without change information in the localhost.

If you wanna make the arguments disappeared, go to 'Network', go to 'host' tab..then click 'unlock', then click properties and type 'george-laptop' that you wanna put in the same line of your localhost IP (127.0.1.1) to

george-laptop. Click lock, reboot and the you will not see the arguments appear whenever you run the sudo command.** Don't change the IP Address, just change the name (usually right-side of the Ip Address.


* My answer is not what you're looking for I believe. But, the arguments will annoy people when they always use sudo's.

** The Lock and Unlock is probably not same in Lubuntu (LXDE) or Xubuntu Desktop, maybe the lock button is edit or add in Ubuntu.


[/B]

---

### Post by mastablasta on 2014-11-27
> **george91 said:**
> 
@mastablasta 
I had free unformatted space when I was trying to install it. The partitions I had where 1 System reserve which i had no idea what it was, 1 for C:/, 1 for D:/ and the free unalocated space where I intended to install Ubuntu
on preinstalled systems there is usually also a recovery partition, which could be hidden and primary.

since you already installed Linux I can't know what was wrong before :)

also in my case I had 3 primary, 1 secondary and free space available and the installer still didn't recognise the free space. manual installation worked just fine though.

it's we that make it complicated with dual boots and such. with Ubuntu only install things are so simple - only  4 or 5 clicks and it all get's installed in 15 minutes or so.

or something like this it will just drop the OS to disk: [https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by Mark Phelps on 2014-11-27
> The partitions I had where 1 System reserve which i had no idea what it was, 

That partition, the small first one, is the Windows boot loader partition.  The "C" partition contains the OS and apps.

---

