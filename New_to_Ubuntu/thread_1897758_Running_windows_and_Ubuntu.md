---
title: "Running windows and Ubuntu"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by bobbyj14 on 2011-12-19
I have Ubuntu installed. I want to also run windows 7. When I try to install windows 7, it tells me the drive is not formatted to NTFS. I downloaded "Gparted" so I could try to fix it. The only thing it let me format to NTFS is too small to install windows 7 on. What do I do??? I'm ignorant with anything besides windows.

---

### Post by hackb0y294 on 2011-12-19
By far the easiest way to dual boot Windows and Ubuntu is to install Windows first, then Ubuntu. Even if you get your drive partitioned properly, there will be boot issues because Windows won't recognize Ubuntu's MBR, while if Ubuntu is installed after Windows, it will automatically let you choose between the two at boot. So, I suggest if you don't have much important in Ubuntu, back up what you do have to a flash drive or something similar, and install Windows. Just format the whole drive with the Windows installer, then after it's finished installing, boot up Ubuntu from the Live CD and select Install alongside Windows. Hope it works for you.

---

### Post by ExileAmongYou on 2011-12-19
> **bobbyj14 said:**
> I have Ubuntu installed. I want to also run windows 7. When I try to install windows 7, it tells me the drive is not formatted to NTFS. I downloaded "Gparted" so I could try to fix it. The only thing it let me format to NTFS is too small to install windows 7 on. What do I do??? I'm ignorant with anything besides windows.

If you only have Ubuntu on the computer, you probably have most of your drive taken up by a large Ext4 partition. You can't shrink or resize it while you're logged in, because that's what Ubuntu is running off. You're best off booting up a live CD/USB, and using Gparted from there. You will have to make sure that you unmount your EXT4 partition if it's mounted. Then you can shrink that partition to free up some space, and create a new NFTS partition to install Windows into.

Be warned that messing with partitions is (potentially) risky, so it's a good idea to back up any important files before you do it.

---

### Post by QIII on 2011-12-19
Windows will often cough, object and cry like a baby unless it is on the first partition.

Do you have anything important in your Linux installation you would not care to lose?

If not, I suggest this:

Using the Live Disk and gparted from there --

1.  Delete all of the partitions.

2.  Decide how much of your disk you want to commit to Windows.  Make an NTFS partition that size.  

3.  Partition the rest of the disk as ext4.

4.  Get out of the Live CD.

5.  Pop the Windows install disk in, shut down and restart (you should have your BIOS set up to boot from CD.)

6.  Install Windows.  It will generally only see the NTFS partition as usable.  Ext4 will be foreign to it.

7.  After the 3 days and 7 hours it takes to get your Windows installation done, shut down.

8.  Pop your Ubuntu disk in.

9.  When it starts up, it should ask you if you want to use the whole disk (you don't) or install it on the rest of the disk (or beside Windows or something like that.)  Don't worry about manually partitioning if you are new to Linux.  That can get dicey (although it is generally best, once you are familiar with Linux, to at least set up a separate /home directory)

10.  Install Ubuntu.

You may or may not have to update GRUB (I don't think you will), but if it comes to that just come back and ask.

(If any of that doesn't make sense because I'm a Linux geek, don't be afraid to ask for better instructions!  We're here to help.)

---

### Post by hackb0y294 on 2011-12-19
> **QIII said:**
> 7.  After the 3 days and 7 hours it takes to get your Windows installation done...

:lolflag:

Actually, Windows 7 installs quite fast compared to previous versions.

---

### Post by HermanAB on 2011-12-19
I would not bother.  Dual booting is so 20th century.  The easiest solution is to install Virtualbox and run Windows in a window, where it belongs.

---

### Post by QIII on 2011-12-19
Except that some things one might want to use Windows for will not be very useful in a virtual machine.

Gamers, for instance, would be very disappointed.

Dual booting is a good choice for working with an Alpha release of a new distro if you want to test down to bare metal.  A virtual machine does not give you that.

---

### Post by oldfred on 2011-12-20
> 
Actually, Windows 7 installs quite fast compared to previous versions.What is quite fast for Windows? My Ubuntu installs take about an hour with all my configuration. My actual install has been 20 min without updates from USB to hard drive, 9 minutes without updates from hard drive to SSD, but then updates, lots of added programs & configuration take a while. I have already partitioned a 25GB / ext4 partition so I have no time used for that, and directly boot an ISO from another drive with grub2.

You do not have to totally reformat although sometimes that is best. Windows requires a primary NTFS partition (sda1 thru sda4) with the boot flag. It does not see the Linux partitions and sometimes if allowed to auto partition corrupts the extended partition. Best if primary installed to is before the extended on the drive, or it may not work. Some have reported they then had to use the Windows disk to reformat the NTFS again, installs of XP have not required that at all.

---

### Post by mastablasta on 2011-12-20
well just installed winXP SP2 (still solving the disk issue) during weekend. takes about 30 minutes from CD to install it. all stuff worked out of the box. but to get it working better (i.e. additional features) i had to install proprietary drivers (GPU, mobo, sound...). after install things wokred (aside ofrm the disk drive which seems to be faulty).
 
anyway the longest to install on it seems to be the updates. which i guess if you isntalled a rolling distro using an image from 2002 would also take some time on 1Mbit connection.

---

