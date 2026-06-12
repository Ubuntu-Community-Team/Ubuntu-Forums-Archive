---
title: "Unbalanced partitions in dual-boot Windows 7/Ubuntu"
date: 2013-08-16
forum: New to Ubuntu
---

### Post by Stonefeather_Grubbs on 2013-08-16
I just installed Ubuntu 12.4 LTS onto my Gateway NV53 laptop with a 500 GB hard drive as a dual-boot with Windows 7 64-bit. 
 
The first thing I did, since Windows was having some stability issues anyway (and to reduce the space it took up on the drive), was a system restore (factory settings) using the manufacturer's utility that uses the Acer PQSERVICE partition, after backing all my data to my 500 GB Lacie external hard drive (which I has originally formatted with FAT32, since I had anticipated eventually wanting to do a dual-boot at some point, and understood--at that time anyway--that Linux has or had issues with the NTFS system. Since I will be using use the Lacie as data repository for both systems, I won't need a partition for that on the internal drive. 
 
After the system restore, and after installing a zillion or so updates in multiple sessions with Windows Update, and then re-installing all of my software, I found I was using less than 10% of the Windows patition (C: ). I had intended to allocate half of this partition's space for Windows and half for Ubuntu, but when I used Shrink Disk in Windows Disk Management, it would only allow me to peel off 13.1 GB. I had read somewhere that Windows installs some immovble files near the end of the partition, which, I suppose, accounts for that. I tried the Ubuntu installer as an alternative , but it would not allow me to resize it at all, and could not see how much unused space there was in the Windows partition--because of the issues with reading NTFS maybe? So I did the shrink with Windows after running Defrag. 
 
I decided to delete the PQSERVICE partion and reassgn it as Swap space for Ubuntu--11.72 GB is more than I need, if I understand correctly that it only needs to be the size of my RAM (4 GB), but at least it would not be eating up any of my root partition that way. I used the Gateway/Acer Recovery utility to transfer it to two DVDs first though. Then I assigned the remainging 13.1 GB block of free space as root and installed (failing to notice that I had left boot assigned to the Lacie, but that has not been a problem). 
 
Both Windows and Ubuntu are bootable now and run well, but I am still irked about the disparity between them in their assigned space on my internal HD. I originally did this to install FontForge (the Windows binary was too unstable to use), but I expect I will use it more and more as I discover and learn more open-source replacements for my Windows programs. And, besides, it just seems obscene in principle. So, my question is: is there any way I can wipe my internal HD altogether and reinstall everything all over again from the Gateway/Acer Recovery DVDs and the Ubuntu CD with more balanced partitioning, either by one of those or with some other partitioning program? Or should I just suck it up and live with it? 
 
 My partions presently, in order, are: 11.72 GB Ubuntu Swap (formerly PQSERVICE); 100 MB Windows SYTEM RESERVED, NTFS (Ubuntu says it's 104 MB); 440.84 GB Windows C: NTFS partition (includes boot and crash dump); and 13.1 GB ext4 Ubuntu root partition (it seemed to be the default filesystem).

---

### Post by carl4926 on 2013-08-16
Typically I set up the partitions first.
That is wipe a drive, create ntfs and ext4 etc....
But because you are using some rubbishy vendor install, you are kind of stuck.

In the past, I have done this, with 100% success so far.
Remember you can only have 4 Primary partitions on a MBR table and the Extended partition you need for the linux logical partitions will count as one.

Defrag your windows C
Shrink it with Gparted to take half of the free space
Create your partitions for Linux and install
When you do finally boot windows it's possible it will do a disk check, let it run.

---

### Post by Mk32 on 2013-08-16
Yes, setting up the partitions manually as a first step usually makes any subsequent operations easier. 

I would suggest that you download any drivers from Gateway for your hardware so that you can use a generic Windows install CD/DVD. [Here](http://support.gateway.com/us/en/product/default.aspx?tab=1&modelId=2374) is the directory where I located the appropriate drivers for your machine (unless you have a NV53a model).

Also, 11.72GB of swap is...rather big, unless you have like 16GB of RAM. Even then, I'd be tempted to stick with a default 2000MB of swap.

---

### Post by Mark Phelps on 2013-08-16
Ignore any advice to use GParted to shrink Win7 -- doing that risks corrupting the Win7 filesystem and rendering it unbootable.

If you wipe the drive and reinstall from the OEM media, you'll get the default partitioning scheme and sizes the OEM established.  You likely will not be given any way to adjust the partition sizes as part of that reinstall.

Your defragging and shrinking Win7 is the best way to go, and unfortunately, Win7 does tend to take a lot more room than Ubuntu.  IF you shrink it too much, that is, if you don't leave it 20% free space, you will see Win7 start to slow down and possibly fail due to lack of free space.

---

### Post by Stonefeather_Grubbs on 2013-08-16
Carl4926: so you are saying that the Recovery *will* eat up the entire drive with its own preset partitions, even if I partition it beforehand with Gparted running from the Ubuntu install disc? *But* that I can shrink the current Windows partition with Gparted, with no damage to the funtionality of Windows 7, to a size much smaller than Windows can do with its own Disk Management utility?

---

### Post by oldrocker99 on 2013-08-16
The unmoveable files Windows installs ner the end of the disk is a common thing, unfortunately. These days, BTW, Linux systems can read FAT 16, FAT32, NTFS etc, just fine and dandy. It's Windows that can't read ext4, which figures.

---

### Post by oldfred on 2013-08-17
While this is Vista, the same issues are in Windows 7.
 [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Also good to have a repairCD or flash drive for the current version of every system you have installed. Ubuntu's live installer automatically becomes one, but you usually need to make one for Windows. Impossible to do after Windows has crashed unless you have another system with Windows.


 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by carl4926 on 2013-08-17
> **Stonefeather_Grubbs said:**
> Carl4926: so you are saying that the Recovery *will* eat up the entire drive with its own preset partitions, even if I partition it beforehand with Gparted running from the Ubuntu install disc? *But* that I can shrink the current Windows partition with Gparted, with no damage to the funtionality of Windows 7, to a size much smaller than Windows can do with its own Disk Management utility?

Yes
Recovery or recovery disks restore the factory state = what you had when you bought the machine

>  *But* that I can shrink the current Windows partition with Gparted, with no damage to the funtionality of Windows 7
Yes.
But some will not agree. All I can say is... I have done this tirelessly for years
*But I backup 
*Only take half of the FREE space
*And defrag just prior

Please note, I can't see exactly what you have or what you are doing.
I have years of experience and do have access to full windows install media

Here is a guide I made in openSUSE using virtual box. IIRC I was have some issues with the mouse at times, so just ignore it if it seems irratic
It's the principles from it you need: [https://dl.dropboxusercontent.com/u/10573557/win_lin_partitions.m4v](https://dl.dropboxusercontent.com/u/10573557/win_lin_partitions.m4v)

---

### Post by Stonefeather_Grubbs on 2013-08-18
I guess I will try this, Carl; at the worst, I still have my OEM Restore on DVD and my personal files backed up, and can redo what I have now from them. Since I already have my swap space on its own Primary partition where the OEM Restoration used to live, I will keep that as is, overlarge though it is. I don't mind having Home in the same partition as Root, since any files I create that get put there will be moved to the FAT32 eternal drive anyway for use by both OS's, so I will just create the new partition from the part of the old Windows C: merged with the current Ubuntu partition, which I will delete, creating a new Primary ext4 partition to reinstall Ubuntu on. Wish me luck.

---

### Post by Stonefeather_Grubbs on 2013-08-19
Reporting from within my newly resized Windows C: drive. This did work, but first, because GParted won't resize an NTFS partition with bad sectors, even after repaired with CHKDSK and rebooting twice as GParted said to do, I had to hack the subsidiary ntfsresize program with directions I found here: [http://www.unfinishedteleporter.com/?p=3238&cpage=1#comment-4401](http://www.unfinishedteleporter.com/?p=3238&cpage=1#comment-4401)

Because I had to do this from within my installed Ubuntu, I could only do shrinking of the C: drive part of it in that operation, since the installation disk would probably not be hackable in that way, but I can do the rest (deleting the current Ubuntu partition and creating the new, larger ext4 partition) through the installation program on the disk. Thanks for your excellent walkthrough, Carl.

---

### Post by carl4926 on 2013-08-19
Happy it worked.

Folks rant about Gparted and it messing up winders, but I've literally done hundreds and never had a fail yet. I'm pretty careful mind you and always have full recovery options in place.

---

