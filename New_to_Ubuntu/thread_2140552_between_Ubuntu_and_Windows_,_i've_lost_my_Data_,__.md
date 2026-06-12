---
title: "between Ubuntu and Windows , i've lost my Data ,  help me please ."
date: 2013-04-30
forum: New to Ubuntu
---

### Post by abdkh on 2013-04-30
dear friends ,
three months ago i had a message from Windows, warning me of having illegal copy of Win OS .
so i converted to Linux , Ubuntu . but one week ago i had a problem that my kid did remove the power wire while my laptop was on ! 
then Ubuntu no more boot !
so i said that is easy , i took my old copy version of Vista and try to reinstall it ,
but after one single time of taking the choice of repair system , the CD boot freez ! 
so i said again that is easy , the computer is upset because of that treason to Linux !! so i maid a flush portable Ubuntu which i'm using now , and try to install Ubnutu again ! 
as i say ( that is easy ) but that process freezes too . the hard disk have 4 partitions , but i cant access to the first two .
then i said that is easy , and i started long trip of reading problems like this in this forum and try that long chains of ( sudo - apt ... etc )
but no success yet .,
then i said that is easy , i've lost the MBR and the Grub , and the Bios will not start , and the hard disk is full of bad sectors so let's take that sick hard disk to a running computer to extract the important Data because ... that is easy !!
and after three days to recover only 3.5 GB , i  find this morning that more than half of my pictures are corrupted !!:(
help me please to recover my files , because i start thinking that is probably NOT easy .:P:P
thanks

---

### Post by coldraven on 2013-04-30
Firstly, give us some more information:
Is it a laptop, if so what model?
What version of Ubuntu are you using?


Do not install or write anything on your hard drive, the more you do the more chance that you will overwrite your data.
I would buy a new hard drive. Take out the old one, fit the new one and install Ubuntu on it.
Now at least you will have a working computer to use to get your images back.

Buy an enclosure for the old drive so that you can plug it into a USB port.
Depending on your drive it would be something like this:

[http://www.ebay.co.uk/itm/External-2-5-SATA-to-USB-Hard-Drive-Caddy-HDD-Enclosure-Laptop-Drive-SSD-/160981754960?pt=UK_Collectables_HardDriveEnclosures_RL&hash=item257b42a450](http://www.ebay.co.uk/itm/External-2-5-SATA-to-USB-Hard-Drive-Caddy-HDD-Enclosure-Laptop-Drive-SSD-/160981754960?pt=UK_Collectables_HardDriveEnclosures_RL&hash=item257b42a450)

Then post back for more help.

---

### Post by Mark Phelps on 2013-04-30
When you were doing one reinstall after another, were these pictures in a different partition -- one that was not affected by the reinstalls?

If so, what filesystem was in use on that partition?

If it was NTFS, you MIGHT do better connecting the hard drive to a Windows PC and using Windows data recovery apps.

---

### Post by abdkh on 2013-04-30
first of all , i would like to thank you for paying your attention to my problem ,
my laptop is HP G62
OS : Ubuntu 12.10 32bit
actually  i did buy enclosure for the old drive and use Live boot program to save  3 GB along 3 days ! but the recovered pictures indeed are few ones !  and the rest windows can't recognize them .
i place my pictures into  driver D , the second partion for windows , and its file system NTFS and  i'm now conncting the hard to another coputer , and i,m using EaseUs  Data recovery for windos 7 but since 24 hours it is scanning my  corrapted hard disk .
i am afraid of having the same result as Live boot gave
thanks

---

### Post by coldraven on 2013-05-01
You could try using PhotoRec. It comes with the testdisk utility.
sudo apt-get install testdisk

I suggest you only use PhotoRec to search for the exact filetype that your images are in, jpg for example otherwise you will end up with thousands of results.

> TestDisk checks the partition and boot sectors of your disks.
It is very useful in recovering lost partitions.
It works with :
 * DOS/Windows FAT12, FAT16 and FAT32
 * NTFS ( Windows NT/2K/XP )
 * Linux Ext2 and Ext3
 * BeFS ( BeOS )
 * BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
 * CramFS (Compressed File System)
 * HFS and HFS+, Hierarchical File System
 * JFS, IBM's Journaled File System
 * Linux Raid
 * Linux Swap (versions 1 and 2)
 * LVM and LVM2, Linux Logical Volume Manager
 * Netware NSS
 * ReiserFS 3.5 and 3.6
 * Sun Solaris i386 disklabel
 * UFS and UFS2 (Sun/BSD/...)
 * XFS, SGI's Journaled File System
 .
PhotoRec is file data recovery software designed to recover
lost pictures from digital camera memory or even Hard Disks.
It has been extended to search also for non audio/video headers.
It searches for following files and is able to undelete them:
 * Sun/NeXT audio data (.au)
 * RIFF audio/video (.avi/.wav)
 * BMP bitmap (.bmp)
 * bzip2 compressed data (.bz2)
 * Source code written in C (.c)
 * Canon Raw picture (.crw)
 * Canon catalog (.ctg)
 * FAT subdirectory
 * Microsoft Office Document (.doc)
 * Nikon dsc (.dsc)
 * HTML page (.html)
 * JPEG picture (.jpg)
 * MOV video (.mov)
 * MP3 audio (MPEG ADTS, layer III, v1) (.mp3)
 * Moving Picture Experts Group video (.mpg)
 * Minolta Raw picture (.mrw)
 * Olympus Raw Format picture (.orf)
 * Portable Document Format (.pdf)
 * Perl script (.pl)
 * Portable Network Graphics (.png)
 * Raw Fujifilm picture (.raf)
 * Contax picture (.raw)
 * Rollei picture (.rdc)
 * Rich Text Format (.rtf)
 * Shell script (.sh)
 * Tar archive (.tar )
 * Tag Image File Format (.tiff)
 * Microsoft ASF (.wma)
 * Sigma/Foveon X3 raw picture (.x3f)
 * zip archive (.zip)

---

### Post by Mark Phelps on 2013-05-01
Easus Data Recovery is one of the best Windows data recovery apps out there.  IF it can't recover your files, chances are nothing else is going to do any better.  Sorry, but once files get corrupted, data recovery won't work after that.

---

### Post by Mopar1973Man on 2013-05-01
> **Mark Phelps said:**
>  Sorry, but once files get corrupted, data recovery won't work after that.

This where backing up to a second computer with a very large hard drive or using a external backup drive is best to protect your data from damage. Not sure but I think you can do a SMART test on hard drive through Linux to verify the hard drive health too. But I would do that only after saving your data first.

---

