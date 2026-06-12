---
title: "Dual Boot after Mobo+CPU replacement and stuck"
date: 2020-07-06
forum: New to Ubuntu
---

### Post by FamilyFriendlyName on 2020-07-06
I am very new to this so please direct my inadequacies.

I replaced my Mobo and CPU and RAM today 6/7/2020 (6th July for americans) and have problems.

 I previously has a dual boot machine with windows 10 and Ubuntu 18.04 on. I had various kernels of 18.04 (4.15, 5.00, 5.01) etc. this was becuase some strugled with my wifi card (AX200) and some struggled with graphics card (Nvidia 2060). But in the end I got them working nicely. Windows at this point would just update as usual and drivers agree with all hardware.

So now I replace Intel i7-920, Pegatron Truckee, and 20GB of Crucial RAM
with an updated RYzen 9 3900, MSI ACE x570, 32GB Corsair (not the rgb flashing ones)

I had a seagate 2TB Hybrid HDD/SSD which was partitioned by an IT genius at work and this has remained constant between builds. I basically did this fingers crossed that it would work and I was amazed that when I FIRST turned my pc back on it did work. I ran a work simulation in Ubuntu no problem and opened MATLAB. My Son also played a few games of fortnite on Windows and the CPU and GPU activated and all worked well.

I then restarted my PC for no reason other than to switch back to Ubuntu and there was no Ubuntu. I went into the MSI settings and tried to find it and couldn't. So i tried to open Windows and it failed. I did the troubleshooting and tried the repair and that failed. I tried to boot Windows from a USB stick and that failed. I am now on an Ubuntu 20.04 USB boot so i can get internet.

I am concerned that a) I have lost all of my work in Ubuntu and b) that I have upgraded my PC to an RGB fan and a persistant failed booting cycle.

I would like to get back to what I had previously and realise I haven't given you much technical information, but this is because I don't know what to say as I am not particularly technical, but very willing to learn.

I have tried to get my partitiion information from fdisk and it is this:
```

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.93 GiB, 2049204224 bytes, 4002352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 27.9 MiB, 28405760 bytes, 55480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 54.97 MiB, 57614336 bytes, 112528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 240.82 MiB, 252493824 bytes, 493152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 62.9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 49.8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ST2000DX002-2DV1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x1723f2a5

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048    1126399    1124352   549M  7 HPFS/NTFS/exFAT
/dev/sda2          1126400 2047999999 2046873600   976G  7 HPFS/NTFS/exFAT
/dev/sda3       2048002046 3907028991 1859026946 886.5G  5 Extended
/dev/sda5       2048002048 3907028991 1859026944 886.5G 83 Linux

Partition 3 does not start on physical sector boundary.


Disk /dev/sdb: 14.46 GiB, 15518924800 bytes, 30310400 sectors
Disk model:                 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x01294be9

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 30310399 30308352 14.5G  c W95 FAT32 (LBA)
```

Thank you for any help

---

### Post by zeekstern on 2020-07-07
Sounds like you're in trouble:)) I'm no Ubuntu pro, but I just went through a couple of installations of dual booting Ubuntu and XP and might be able to help a little until a Ubuntu Guru joins in.


From looking at your fdisk output, it looks like both Ubuntu and Win 10 are there on disk so hopefully you didn't lose any work. 


1. Do you get the Grub Menu when you turn your PC on and if so, what does it look like?
For example, on mine I boot from /dev/sda2 to boot into Windows and just *Ubuntu to boot into ubuntu.


2. How did you try to open Windows?


3. Did Windows start booting up and then just crap out or what did it do when you tried booting from USB?


4. Is your system set to boot from USB first?


5. You said you "tried the repair". Did you install the ubuntu boot-repair package and run that?
That worked for me.

---

