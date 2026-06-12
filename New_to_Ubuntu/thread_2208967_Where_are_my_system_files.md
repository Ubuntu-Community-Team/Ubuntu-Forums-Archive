---
title: "Where are my system files?"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by RussellXPD on 2014-03-03
Thanks to the forum I'm now running Ubuntu 12.0.4 as dual boot with XP on an 8 year old machine.

I was warned that a lighter distro would have been more suitable. I've greatly reduced what's on the 120Gb HDD and have a 1Tb supporting ED, 2Gb of RAM.

I don't anticipate any problems but I *would *like to know where my Ubuntu system files are.

Explorer in XP and Disk Utility in Ubuntu give me the same readings on the _hard drive _of disk space free and used. I can't see any indication in either system that the Ubuntu system files are there.

In C drive for example are a folder **boot and wubi for Ubuntu Q  **(empty) **wubildr** and **wubildr.mbr.  **The folder is empty and **wubildr** occupies 130kb. There is one instance of this file on each of three partitions.

When I installed Ubuntu I tried to install it on the 1Tb External drive which is always attached. 
 
I believe my maths is right - These are the readings for the three partitions  of the external drive:
A  Size:  227Gb   Used: 226Gb    Unaccounted for:  134 mb
B  Size:   232Gb  Used: 17.7Gb    Unaccounted for: nil
C  Size:   245Gb  Used: 22.9Gb    Unaccounted for: 0.4Gb

If having an old low spec system is a handicap, then I would expect that disk space would become a problem at some stage. I've tried to get answers by reading other threads, Google searches etc. I'd be grateful for any words of wisdom about finding the system files which are down there somewhere!

RussellXPD

---

### Post by Vladlenin5000 on 2014-03-03
System files are there for both system otherwise neither would work. From Ubuntu (or any other modern distro) you should be able to see the whole contents of the drive/partitions regardless of the file systems; Windows, on the other hand, only sees FAT or NTFS. As such, in dual-boot systems the Linux partitions aren't visible from inside Windows.
However, apparently you haven't a classic dual-boot but rather Ubuntu installed "inside" Windows - via "Wubi" - which isn't recommended and even not possible in the new Windows 8. I never used such installation method therefore I don't know how it is supposed to look from inside Windows but I suppose Wubi just reserves the space inside the Windows partitions, like a container or a hidden file, while the Linux file system is inside, not visible in Windows.

I really don't understand WHY you use use wubi to install Ubuntu in a dual-boot with Windows intending to install it in a different drive/disk nonetheless...

---

### Post by Impavidus on 2014-03-03
Hard drive space is rarely a problem when installing Ubuntu on old computers (with the exception of some cheap netbooks). It's about ram and graphics.

It seems you installed using wubi. This isn't really dual booting, it's more like one-and-a-half booting, and in your previous thread you saw it's no longer recommended. In Windows you'll see a root.disk, swap.disk and a few other files. The root.disk file contains the entire Ubuntu file system. Windows cannot interpret this file.

In Ubuntu, the entire filesystem you see, with the exception of the /host directory, some subdirectories of /media and the virtual file systems, is stored inside the root.disk file. This is where you find the Ubuntu system files. Windows cannot see the individual Ubuntu system files, it only sees the virtual partition on which they are stored.

@Vladlenin5000: As to why, most likely as a result of misunderstanding the installation procedure, a.k.a. a mistake.

---

### Post by RussellXPD on 2014-03-03
Thank you, Impavidus. VladLenin

I didn't find the the root.disk file in Ubuntu, but I'm going to look again.  

I'm having a big think about what I'm not understanding.

Russ

---

### Post by grahammechanical on 2014-03-03
I do not have any experience of running a Wubi install of Ubuntu but you can try this.

Open File Manager and in the left hand pane scroll down until you see either "file system." or "computer" Click on it and Fle Manager will open a window and in that window will be folders that represent the Ubuntu system. May be. should be. Cannot say for sure.

Regards.

---

### Post by endlessinstant on 2014-03-03
hard disk space isn't as issue typically.  I think Ubuntu needs something like 6-7 GB for essential system files but that is just space for you to play with.  As long as you don't need it, you can fill your storage to capacity and things will still work, for the most part.   My primary Linux system is an HP Chromebook that only has a 16 GB SSD.  It works fine while having both my Debian build and Chrome OS sitting on the hard drive.   Main issue you'll have on old hardware like that is the read/write speeds are probably not as good compared to a newer drive so you'll have slower loading times.   Unless your 120 GB internal drive is really antiquated, you will probably get better performance from partitioning and installing the OS on that drive and using your 1 TB external for data storage.   root.disk should only be visible while looking at it in Windows.  This is because when looking at it in Ubuntu, Ubuntu is seeing it not as one file called root.disk but all the files on your Ubuntu system.   Root.disk is essentially a disk image, like if you were to rip a CD and create an ISO file from it.   Think of WUBI as mounting and reading that image for you so you can run your Ubuntu system.   It's location on the drive should be something like c:\ubuntu\disks depending on how you did your install

---

### Post by RussellXPD on 2014-03-05
Thanks to all for your replies on this topic. It&#8217;s made all too clear to me my ignorance on the mechanics of Unix and everything that&#8217;s been developed from it.  I hope that in a few months time I will have a better understanding of system operation and also why it will have taken me so long to break into it.
 
The reason I wanted to see the disposition of system files was to reassure myself that my computer was going to cope with the load that&#8217;s put on it.  I&#8217;m pretty sure now that it is.  At the moment this remains a mystery, though I shall be trying again.
 
As I found with many Windows systems, and especially teaching beginners, some concepts are beyond understanding for those beginners. The way in is to **do** things, acquire a competence in completing tasks. With luck the understanding will come slowly later.
 
I chose Wubi because it worked and I had enough  trouble getting that, rather than to choose a better system and get locked out &#8211; which is something that&#8217;s happened a few times!
 
Being positive, I am doing things with 12.0.4 and slowly the wraps are coming off.  I&#8217;ll mark this as SOLVED because ultimately, it was the wrong question.

---

