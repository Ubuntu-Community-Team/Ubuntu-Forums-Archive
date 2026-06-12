---
title: "USB Flash drive."
date: 2013-10-18
forum: New to Ubuntu
---

### Post by Toni_Vines on 2013-10-18
I have a Freecom FHD-2 Pro 80 GB usb flash drive. It was last used with Windows so I'm guessing it's a NTFS format. I would like to use it for this Unbuntu 12.04 as a storage space. I've done "ls usb" and it's listed but I don't know how to format it and get it recognised on my desktop. 
Any suggestions please?
Thanking you,
Toni.

---

### Post by david98 on 2013-10-18
The drive might be corrupt try opening it with gparted then create a small partition within then you should be able to use it. This has worked for me to repair lot's of flashdrives sd card's etc that linux or windows would not detect.

---

### Post by Toni_Vines on 2013-10-18
gparted not seeing it I'm afraid!

---

### Post by david98 on 2013-10-18
Is window's still detecting the drive ?

---

### Post by Toni_Vines on 2013-10-18
Yes it is. 
Thanks for taking the time to help me.
Toni.

---

### Post by fantab on 2013-10-18
Format the USB Flash Drive in Windows... see if you can.

---

### Post by Toni_Vines on 2013-10-18
As a matter of interest when I do lsusb I get the following:
toni@toni-System-product-name:~$ lsusb
Bus 001 Device 004: ID 07ab:fc81 Freecom Technologies 
Bus 003 Device 002: ID 03f0:0305 Hewlett-Packard ScanJet 4300c
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
toni@toni-System-product-name:~$ 

The Freecom Technologies is the drive I want. 

I'll try to format in Windows later but I can't get to a Windows machine for a while.
Cheers,
Toni

---

### Post by fantab on 2013-10-18
Can you post the output of:
```
sudo fdisk -l
sudo parted -l
```

---

### Post by Toni_Vines on 2013-10-18
fdisk -l gives me:
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002b030

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   157691903    78844928   83  Linux
/dev/sda2       157693950   160835583     1570817    5  Extended
/dev/sda5       157693952   160835583     1570816   82  Linux swap / Solaris
toni@toni-System-product-name:~$ 

parted -l gives:
Model: ATA HDS728080PLAT20 (scsi)
Disk /dev/sda: 82.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  80.7GB  80.7GB  primary   ext4            boot
 2      80.7GB  82.3GB  1609MB  extended
 5      80.7GB  82.3GB  1609MB  logical   linux-swap(v1)

Hope this helps
Toni.

---

### Post by fantab on 2013-10-18
I don't think you had your USB plugged in when you ran those commands... We need to see the output with USB Freecom FHD-2 Pro plugged in. I guess I wasn't explicit enough.

---

### Post by Toni_Vines on 2013-10-18
It is in! It hasn't been out all afternoon!

---

### Post by fantab on 2013-10-18
> **Toni_Vines said:**
> fdisk -l gives me:
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002b030

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   157691903    78844928   83  Linux
/dev/sda2       157693950   160835583     1570817    5  Extended
/dev/sda5       157693952   160835583     1570816   82  Linux swap / Solaris
toni@toni-System-product-name:~$ 

parted -l gives:
Model: ATA HDS728080PLAT20 (scsi)
Disk /dev/sda: 82.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  80.7GB  80.7GB  primary   ext4            boot
 2      80.7GB  82.3GB  1609MB  extended
 5      80.7GB  82.3GB  1609MB  logical   linux-swap(v1)


The output of the command does not show it, unless its the only drive in the system, /dev/sda. Is it?

Was it mounted when you ran those commands?

---

### Post by Toni_Vines on 2013-10-18
The drive that you see is the hard drive in the computer. The flash drive is plugged into a usb port and that's it. You mention it being mounted, what is this please? Maybe this is what I'm doing wrong?

---

### Post by Dennis N on 2013-10-18
> **Toni_Vines said:**
> The drive that you see is the hard drive in the computer. The flash drive is plugged into a usb port and that's it. You mention it being mounted, what is this please? Maybe this is what I'm doing wrong?

Mounted means its connected to the computer's file system and you can then read and write with the drive.

**Ideas:**

In the terminal:

**df -h** 

will show all mounted filesystems including usb systems. 

If you see your usb drive there, try gparted again and **be sure to select the usb drive with the drive selector in the upper right**.

If successful, you can wipe (erase) the drive by making a new partition table, then create new partitions for linux. It needs to be unmounted to do this.

---

### Post by Toni_Vines on 2013-10-18
OK, the flash drive is not there. So I guess now I need to mount it. Would you be so kind as to guide me through this process? Sorry if I appear stupid but I'm learning as I go.
My thanks to you for you help and patience.
Toni.

---

### Post by Dennis N on 2013-10-18
USB devices should mount when they are plugged in. If it isn't showing up, pull it out and plug it back in and it should show up.

On my system, last item is a usb flash drive (named COMMON) mounted (connected) at /media/dn/
Plugin USB devices by default show up  in **/media/<username>/** 

```
dn@Sydney:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        29G   11G   18G  37% /
udev            478M  8.0K  478M   1% /dev
tmpfs           195M  780K  194M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            486M     0  486M   0% /run/shm
none            100M   12K  100M   1% /run/user
/dev/sdf1       3.7G  577M  3.1G  16% /media/dn/COMMON

```

---

### Post by Toni_Vines on 2013-10-18
I've unplugged and re plugged it back in. The light on it is on but it's not showing up. I've checked in /media/ and nothing there either. 
Very strange. Is there a way to mount it via the terminal? 
Cheers,
Toni.

---

### Post by Dennis N on 2013-10-18
Test: Do other USB flash drives show up with **df -h** after being plugged in? If they do, then I would look to this particular usb device to possibly have some problem.  But, you said it worked in Windows so that seems unlikely. 

I searched and found a thread about a failure to automount problem in ubuntu 12.04. You should look through it. I see manual mount directions are given in post #21.

[http://ubuntuforums.org/showthread.php?t=1969210](http://ubuntuforums.org/showthread.php?t=1969210)

---

### Post by Dennis N on 2013-10-18
Also, this may explain a few things:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Especially, see the section "Manual Mounting"

---

### Post by Toni_Vines on 2013-10-18
Interesting stuff Dennis. I've done lsusb again and it's definitely there but if I sudo fdisk -l it is not! I particularly like the idea of adding the external usb media to the boot but I tried to follow the instructions and came unstuck! I was able to get the relevent page up in the terminal but it would not allow me to add the extra line as instructed. 
I'm certainly up for trying to sort this because it will help me to learn but I'm feeling somewhat swamped at the moment!
Any help will be great!
Thanks,
Toni.

---

### Post by Dennis N on 2013-10-18
Did you find that other USB drives mount automatically? If they do, it's seems specific to this drive and you have no general problem. Did you try the manual mount described in the link in post 19? 

**Some Observations:**

**lsusb** shows detected usb devices even when unmounted. (I unmounted one of two)
**df -h** only shows only the mounted usb's filesystems (and other mounted filesystems).
**Disks** utility gives device identifiers ( /dev/sd_ ) even for the detected but unmounted usb.
**sudo fdisk -l /dev/sdf** shows the partition information on my mounted usb identified as /dev/sdf 

(Disks is the graphical utility for working with disks - its in Lubuntu which I am using at the moment, I assume its in Ubuntu too).

---

### Post by Dennis N on 2013-10-18
> **Toni_Vines said:**
> Interesting stuff Dennis. I've done lsusb again and it's definitely there but if I sudo fdisk -l it is not! I particularly like the idea of adding the external usb media to the boot but I tried to follow the instructions and came unstuck! I was able to get the relevent page up in the terminal but it would not allow me to add the extra line as instructed. 
Toni.

Some of the things they are trying or suggesting are pretty advanced and beyond my pay grade. Be careful editing system files requiring root access to modify and back them up first.

I assume you are using the **nano** editor, as I saw it in that thread. Once in the relevant directory, use **sudo nano filename** to edit with root privileges. Practice first using its commands on practice files to get familiar with it.

---

### Post by Toni_Vines on 2013-10-19
I've tried another flash drive and I have the same problem. I'm with you Dennis as regards getting beyond myself. I certainly don't have the experience to try some of this stuff so I think I'll just leave it for now and try again in the future! 
Thanks for trying Dennis, I really appreciate it.

---

### Post by Dennis N on 2013-10-19
> **Toni_Vines said:**
> I've tried another flash drive and I have the same problem. I'm with you Dennis as regards getting beyond myself. I certainly don't have the experience to try some of this stuff so I think I'll just leave it for now and try again in the future! 
Thanks for trying Dennis, I really appreciate it.

That is a big problem if you cannot use the USB ports. That suggests a bug in the system and nothing wrong with your drive.   

Some thoughts:

Google "Ubuntu 12.04 flash drives won't mount" and there are lots of hits, some from these forums. Check for any solutions presented.

Start a new thread with title such as "Ubuntu 12.04 flash drives won't mount" - someone may be aware of a solution. There are a lot of smart people around here.

Possibly test a newer Ubuntu using a live cd and see how that works. Or, if you know how to dual boot, you could install two Ubuntus side-by-side, test the newer, then switch over if all is ok.

---

### Post by Toni_Vines on 2013-10-19
Excellent thoughts Dennis, I'll try some stuff tomorrow. Got my daughter getting married in 2 hours so better go and do that! 
Cheers,
Toni.
P.S. I plugged my scanner into a usb port and it worked straight away! Weird or what!

---

