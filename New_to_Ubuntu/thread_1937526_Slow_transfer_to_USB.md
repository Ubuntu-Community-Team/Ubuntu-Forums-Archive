---
title: "Slow transfer to USB?"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by d4m1r on 2012-03-08
Hey guys, this has been something I've witnessed over and over again under my Ubuntu partition, transferring files takes waaaay too long ](*,)

To fill my 8GB USB stick, it usually takes 10-15 minutes but in Windows 7, the same transfer takes 5 minutes MAX. Is EXT4 inherently slower than NTFS when it comes to transferring files to external media or? During the transfer, speeds never exceed 7-8mb/s...

(8GB Sandisk Micro stick, NTFS formatted if it makes a difference).

---

### Post by 3rdalbum on 2012-03-08
> **d4m1r said:**
> 
(8GB Sandisk Micro stick, NTFS formatted if it makes a difference).

It makes a difference.

NTFS on Linux is implemented a little differently to most other filesystem drivers (for certain reasons), and so data to be written to an NTFS filesystem actually goes through the CPU. For most filesystems, the CPU doesn't directly deal with the data to be written.

That's why writing to NTFS on Linux is slower than writing to anything else on Linux, or writing to NTFS on Windows.

How slow? Well, it depends on your CPU.

You could format your flash drive as Ext4 (Linux-only) or fat32 (cross-platform, but 4 GiB file size limit) to work around the issue. Or just make a cup of coffee while copying large files :-)

---

### Post by HermanAB on 2012-03-08
Howdy,

There was a USB bug that caused a tremendous slowdown.  So, first of all, update your system and see if the problem goes away.

---

### Post by LowSky on 2012-03-08
This is actually a bug with the Kernel stemming back over two years to be really honest. The fix is still in the works. The reason it sat so long is large file transfers are not something done until very recently. The most people use to push was an MP3. Now we send HD videos to portable devices, so now its importance is noticed.
The problem is how Linux handles file transfer commands, sadly it pushes USB file transfers to the bottom of the list giving speeds as slow as USB1.1 in some cases. This problem only manifests itself in files around 100MB and larger.

Her is the link to the bug on launchpad
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069)

---

### Post by d4m1r on 2012-03-08
> **3rdalbum said:**
> It makes a difference.

NTFS on Linux is implemented a little differently to most other filesystem drivers (for certain reasons), and so data to be written to an NTFS filesystem actually goes through the CPU. For most filesystems, the CPU doesn't directly deal with the data to be written.

That's why writing to NTFS on Linux is slower than writing to anything else on Linux, or writing to NTFS on Windows.

How slow? Well, it depends on your CPU.

You could format your flash drive as Ext4 (Linux-only) or fat32 (cross-platform, but 4 GiB file size limit) to work around the issue. Or just make a cup of coffee while copying large files :-)

I figured it would lol But I have a very fast CPU (3.2GHz quad core) so I doubt my CPU is the root of my problems.....

@Herman, thanks but my 11.10 system is 100% up to date.

@Lowsky, thanks, I commented on the bug and am subscribed. This is an important issue so I am surprised it is unresolved since 2009 ](*,)

---

### Post by GuiGuy on 2012-03-23
> **3rdalbum said:**
> 
NTFS on Linux is implemented a little differently to most other filesystem drivers (for certain reasons), and so data to be written to an NTFS filesystem actually goes through the CPU. For most filesystems, the CPU doesn't directly deal with the data to be written.


That is not my observation; transferring large files from a server across a gigabit network via a Ubuntu Oneiric desktop to a WD Elements USB HDD (NTFS) works extremely well for me. The transfer for a ~2G file will take a couple of minutes or thereabouts. 

The same exercise using a quality USB2 4G flashdrive formatted as FAT32 will take about 30minutes to an hour using the same system. 

>  Or just make a cup of coffee while copying large files :-)

... which begins to debunk the argument about what is the world's best OS.


Cheers

---

