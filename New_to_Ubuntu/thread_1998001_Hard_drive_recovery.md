---
title: "Hard drive recovery?"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by jlkersti on 2012-06-06
I'm brand new to Linux and don't know the first thing about them or any other Live CDs, I put Ubuntu on my computer in an effort to try to recover some files from my wife's computer, I have Ubuntu on a USB, and I've got my computer back, but I can't see any of my old files, no pics, no docs.  Nothing. Do I need to Install Ubuntu 12.04 LTS onto my computer before I'll be able to see my hard drive or is my computer stuffed and the data non-recoverable for some dummy like me.  If it's useful, when my computer when down it said that there was "No bootable device-insert boot disk and press any key"...my cd drive on this computer has been broken for awhile, so I went the USB route...any help for this know-nothing about computer guy is much appreciated in advance...

---

### Post by carl4926 on 2012-06-06
You can access files using the Live system. But only if the HD is OK.
Look in the BIOS is the HD seen in there still? Even if it is, it doesn't mean it's OK. But at least we know it's still connected. Which brings me to the next point. It's worth pulling the connections and re-seating them on the HD and Motherboard. You must turn off the machine :D

Now from the Live system you are running, open a terminal and do

```
sudo fdisk -l
```
Report the output here.

Also FYI: If a HD is failing and you want to recover info, it's better not to mess about too much trying to mount it.
The application TestDisk might help recover files, if the HD is still working. Parted Magic includes TestDisk

---

### Post by jlkersti on 2012-06-06
below is the information I got when I put in the code you asked, and the hard drive is still there on the BIOS, this is about all I know, I have no idea what the below does or is supposed to tell me...?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x89900f6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   598075391   299036672    7  HPFS/NTFS/exFAT
/dev/sda2       598075392   625135615    13530112    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 8088 MB, 8088715264 bytes
5 heads, 32 sectors/track, 98739 cylinders, total 15798272 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    15798271     7895104    c  W95 FAT32 (LBA)

---

### Post by Mark Phelps on 2012-06-06
I'm guessing that you're trying to recover from the 320GB drive, right?

Since fdisk sees the partitions, the problem must be that you are not able to mount those partitions.

That will happen when NTFS partitions become corrupted or damaged -- which, unfortunately, you generally can NOT fix from Ubuntu. There are some ntfs utilities you can run in Ubuntu, but they only handle trivial filesystem problems.

What you will need to do is hook up the 320GB drive to an MS Windows PC and see if it will mount the partitions.  Using a Win7 PC, at the bottom left, type "Disk" into the entry.  Select the line that says "create and format partitions". That will open the Disk Management utility.

Scroll through the list of Disks to see if the 320GB is listed there.  IF it is and it does not have a drive letter, then assign it one.  Once it has a drive letter, you should be able to access it to copy the files and directories off.

If Windows will not allow you to assign it a drive letter, the filesystem is probably damaged.

In that case, you can try running CHKDSK on the partitions.  That might fix the damage.

If all else fails, you will then need to use MS Windows file recovery products to retrieve your directories and files.  Runtime Software makes several of these.  You can try them for free (to see what they find), but you have to purchase them to do the actual recovery.

---

### Post by carl4926 on 2012-06-06
I concur with Mark

Very likely 'Dirty' ntfs partitions

---

### Post by jlkersti on 2012-06-06
thanks so much to you both!

---

