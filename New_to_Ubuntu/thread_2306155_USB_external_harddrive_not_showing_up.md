---
title: "USB external harddrive not showing up"
date: 2015-12-12
forum: New to Ubuntu
---

### Post by devlin3 on 2015-12-12
Hello, and apologies in advance for any decorum violations.

I have a toshiba external hard drive on which I keep all the movies/music I keep. I recently plugged it into my Xbox One, and the Xbox One prompted me to format so it would work with the Xbox One. After doing so, I noticed that Xbox's media player did not recognize the harddrive as being connected. I then plugged in the same hard drive into my ubuntu powered laptop, on which I had used hard drive many times before. But now, the hard drive does not appear to be mounted. I ran lsusb, which gave me this

> Bus 001 Device 003: ID 0480:a007 Toshiba America Info. Systems, Inc. External Disk USB 3.0

I also entered "dmesg | tail -n 20" into the terminal, which gave me

> [  440.729523] usb 1-1.1: Product: External USB 3.0
[  440.729526] usb 1-1.1: Manufacturer: Toshiba
[  440.729529] usb 1-1.1: SerialNumber: 20120921002871F
[  440.729909] usb-storage 1-1.1:1.0: USB Mass Storage device detected
[  440.730047] scsi7 : usb-storage 1-1.1:1.0
[  443.573968] scsi 7:0:0:0: Direct-Access     TOSHIBA  External USB 3.0 0001 PQ: 0 ANSI: 6

I assume Xbox's formatting messed with the hard drive. How do I resolve? Thank you.

---

### Post by sandyd on 2015-12-12
Not sure, may be format not supported by Ubuntu

Post output of
```

sudo fdisk -l
sudo parted -l
```

---

### Post by yancek on 2015-12-12
Did you have your moves/music on this drive?  What filesystem format was on the drive?   A brief explanation of what formatting does at the link below.

[http://www.tomshardware.com/forum/264997-32-does-formatting-external-drive-erase-files](http://www.tomshardware.com/forum/264997-32-does-formatting-external-drive-erase-files)

---

### Post by devlin3 on 2015-12-12
> **sandyd said:**
> Not sure, may be format not supported by Ubuntu

Post output of
```

sudo fdisk -l
sudo parted -l
```

Output of Sudo fdisk -l:
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000650d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   304480255   152239104   83  Linux
/dev/sda2       304482302   312580095     4048897    5  Extended
/dev/sda5       304482304   312580095     4048896   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 4146 MB, 4146069504 bytes
255 heads, 63 sectors/track, 504 cylinders, total 8097792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x416d5e9c

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

Output for sudo parted -l
> Model: ATA FUJITSU MHZ2160B (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  156GB  156GB   primary   ext4         boot
 2      156GB   160GB  4146MB  extended
 5      156GB   160GB  4146MB  logical


Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
 1      17.4kB  134MB  134MB               Microsoft reserved partition  msftres
 2      135MB   500GB  500GB               Basic data partition          msftdata


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 4146MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4146MB  4146MB  linux-swap(v1)

> **yancek said:**
> Did you have your moves/music on this drive?  What filesystem format was on the drive?   A brief explanation of what formatting does at the link below.

[http://www.tomshardware.com/forum/264997-32-does-formatting-external-drive-erase-files](http://www.tomshardware.com/forum/264997-32-does-formatting-external-drive-erase-files)

I was concerned about this. Unfortunately I have to be going in a minute, but if the Xbox formatting did format my hard drive, are there reliable, free programs available that can recover the lost files? Also, the Xbox formatting must have done something besides erasing all the files, since even an empty hard drive should be recognized by the computer as a D drive, no?

---

### Post by yancek on 2015-12-12
> are there reliable, free programs available that can recover the lost files? 

Yes and no.  Testdisk and photorec are free software which are pretty good at recovering lost data but as free software you will never get a guarantee of anything.

> since even an empty hard drive should be recognized by the computer as a D drive, no? 		

No.  It might be recognized in the BIOS and by the system using something like fdisk or gparted in Linux.  The upper case Letter is just a windows naming convention carried over from the first OS they bought in 1980 and as I'm sure you know, Linux and other operating systems have different naming conventions.

---

### Post by devlin3 on 2015-12-14
So my first step should be to try testdisk and/or photorec, and see whether they can recover the files. If one does recover them, the hard drive should again show up on my laptop

I have begun to run testdisk and it is asking this question
> Disk /dev/sdb - 500 GB / 465 GiB - TOSHIBA External USB 3.0

Please select the partition table type, press Enter when done.
 [Intel  ] Intel/PC partition
>[EFI GPT] EFI GPT partition map (Mac i386, some x86_64...)
 [Humax  ] Humax partition table
 [Mac    ] Apple partition map
 [None   ] Non partitioned media
 [Sun    ] Sun Solaris partition
 [XBox   ] XBox partition
 [Return ] Return to disk selection



Hint: EFI GPT partition table type has been detected.
Note: Do NOT select 'None' for media with only a single partition. It's very
rare for a drive to be 'Non-partitioned'.

How do I know which one to choose?

---

### Post by yancek on 2015-12-14
Testdisk is pointing to the correct one, not the arrow > on the second option and also at the bottom of the page it states EFI GPT partitin table detected.

---

### Post by Yawanathan_Israel on 2015-12-16
Hello,

Though it may have formatted the drive with the correct filesystem, That does not mean that the files are there. Usually formatting a drive is wiping all data, and then giving you a clean drive. If this has been done, Then all files are lost.

Thanks
Yawanathan

---

### Post by sudodus on 2015-12-16
Don't give up with ***testdisk*** yet. It might work :-)

The files might or might not be lost in the meaning that there are no addresses to the directories and files. But the data might still be there 'on the drive surface' and available for a tool like ***photorec***, even if testdisk can't fix the file system. Only wiping the drive (overwriting with zeros or garbling the mapping between logical and physical blocks) will remove the data 'from the drive surface'.

---

### Post by Skaperen on 2015-12-16
even formatting overwrites only a small fraction of sectors.  many files may be damaged but many others may still be whole ... between the rewritten sectors.  file recovery tools read *around* the filesystem formatting.

---

### Post by devlin3 on 2015-12-16
Photorec is currently restoring the files. However, the files now have serial designations instead of their actual names, EG "f21987459" instead of a music track of movie name. Interestingly, VLC will display the files true name while playing it. Better than nothing.

Once it is done recovering, I think it should be fairly straightforward to set up the HD so that it appears on the computer once more.

The hard drive has been formatted to ext2 and once again shows up as a device. However, it cannot be modified, as it is owned by "root." How can I modify?

---

### Post by Dennis N on 2015-12-17
You need to change owner and group of the mount point folder of the mounted file system to your user name.

example:

if mounted at /mnt/data
```
sudo chown -R user:user /mnt/data
```
put your user name in both spots.

This may help: Use the command **df -h** to see mount points:

```
[dmn@Roxanne ~]$ df -h
Filesystem      Size  Used Avail Use% Mounted on
dev             1.8G     0  1.8G   0% /dev
run             1.9G  1.2M  1.9G   1% /run
/dev/sda3        39G   10G   27G  28% /
tmpfs           1.9G  3.5M  1.9G   1% /dev/shm
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           1.9G   20K  1.9G   1% /tmp
/dev/sdb11       53G   29G   22G  58% /mnt/Common-Files
tmpfs           371M   16K  371M   1% /run/user/1000
/dev/sdc1       7.3G  2.5G  4.4G  37% /media/dmn/MyData


```/dev/sdc1 is on a USB drive. Mount point is /media/dmn/MyData

So to change owner and group to me (dmn) I would use: 
```
sudo chown -R dmn:dmn /media/dmn/MyData 
```
That also changes the owner and group of all files and folders in that file system.

---

### Post by devlin3 on 2015-12-17
Thanks, your first post did the trick. I was able to see the mount point on the disk utility. The hard drive is now working as before.

I'm not out of the woods yet. The hard drive was still not compatible with xbox one's media player, so xbox support told me to reformat the drive as a NTFS (as opposed to an ext2, which is what the drive was, and which is also compatible with xbox one). This allowed me to play media files on the xbox. However, when I put the hard drive back on by ubuntu laptop, I received this error message:

> Error mounting /dev/sdb2 at /media/devlin/Toshiba NTFS: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb2" "/media/devlin/Toshiba NTFS"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

Also, the hard drive runs smoothly on my windows 10 laptop. It worked with my ubuntu laptop initially, as that's what i used to change the file system from ext2 to NTFS; I also used the ubuntu laptop to put the media files on the hard drive that I was then able to play on the xbox. But after playing media on the hard drive using xbox's media player, I got the error message quoted in the previous post

---

### Post by Jonathan Precise on 2015-12-18
I don't have an Xbox, but it seems to have the same technology as Fast Startup in Windows. Maybe it has to do with that?

UPDATE: [This]("http://support.xbox.com/en-US/xbox-one/system/learn-about-power-modes") seems to say that it does. Try [changing the Power Settings to Energy-Saving mode]("http://support.xbox.com/en-US/xbox-one/system/change-power-settings"), reconnecting the drive to the Xbox, turning the Xbox off, and reconnecting to the Ubuntu Laptop.

Oh, and [repeat the process with the laptop, changing Fast Startup to off]("http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html").

NOTE: This will disable the functions in the Xbox noted in the article, and will make startup slower on both devices.

---

### Post by devlin3 on 2015-12-18
I will give that a try shortly. 

However, in the mean time, I backed up the files on the hard drive, and reformatted the drive (keeping the filesystem as NTFS). This allowed the drive to be mounted on the Ubuntu laptop. I then added the files to the hard drive once again. I then had to restart my Ubuntu laptop for unrelated reasons. Upon the completion of the restart, the hard drive again gave the same error message as quoted in my previous post. 

To fix this, I downloaded the ntfs-3g package from the Ubuntu Software Center. After installation was complete, I ran the command 
>  sudo ntfsfix /dev/sdb2
which made the drive mountable and writable, meaning I would not have to reformat the hard drive once again. I will see if this needs to be done any time I connect the hard drive to my Ubuntu laptop, but it is a temporary fix for now.

---

