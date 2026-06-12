---
title: "Dual boot advice for 1st timer"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by KelVarnsen on 2011-11-02
Hi, I'm hoping someone can offer me some advice.

I'm planning on partitioning my hard drive and installing a dual boot with windows 7 and Ubuntu 11.10 tonight and there's a few things I'm unsure about because I haven't done anything like this before.

I have a 500GB HD and was wondering what would be the minimum amount I need for windows 7? I am only leaving it on for windows only programs like photoshop. Also is the partitioning permanant? Say for example I wanted to [-Xgo back to windows or get rid of windows completly could I do this afterwards? Does anyone know as well if the ubuntu installer is the best tool to do this? Some how to's I've read are saying to partition your hard drive in diferent ways.

Thanks for reading

---

### Post by Rubi1200 on 2011-11-02
Hi and welcome to the forums :)

Probably the best site for information on dual-booting can be found here:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by KelVarnsen on 2011-11-02
Thanks, that looks like a very useful site

---

### Post by Greywolft on 2011-11-02
[FONT="Georgia"][COLOR="Purple"][I]Hey Kel,
Must be something in the air, since I'm doing something similar. I can tell you from my past attempt, keep windows, if only for running programs that CAN'T run on anything else.

[FONT="Times New Roman"][COLOR="Black"]> **KelVarnsen said:**
> Hi, I'm hoping someone can offer me some advice.

I have a 500GB HD and was wondering what would be the minimum amount I need for windows 7? I am only leaving it on for windows only programs like photoshop. Also is the partitioning permanant? Say for example I wanted to [-Xgo back to windows or get rid of windows completly could I do this afterwards? Does anyone know as well if the ubuntu installer is the best tool to do this? Some how to's I've read are saying to partition your hard drive in diferent ways.

Thanks for reading[/COLOR][/FONT]

What I was told is to make sure windows is there first and then install ubuntu, using a partition(ntfs) to store things that both OS can access. I would create one partition for windows, one for Ubuntu and one for storage. Once a drive is partitioned it is permanent, unless you don't mind losing the info on them. To re-partition a drive it must be formatted which erases everything on the drive.

I myself am using 2 drives, one for each OS and using the external drive to store my info from both.

Good luck and feel free to PM me if you run into any problems, I've got mine up and running so might be able to help if only from this experience.

T[/I][/COLOR][/FONT]

---

### Post by KelVarnsen on 2011-11-02
Thanks for the reply T.
Did you use the Ubuntu installer to partition your drives? I've never partitioned a drive before so I'm a bit nervous about it. How long did the whole process take do you think?

---

### Post by oldfred on 2011-11-02
I have only partitioned empty drives and that is very quick. If you have lots of data that has to be moved it can take a very long time and you do not want to interrupt the process.

House clean Windows, defrag it once or even twice. Use Windows tools to shrink the Windows partition. It may not let you shrink it as much as you might like. Do not use Windows to create any partitions but use gparted from the Linux liveCD.

I like rubi1200 like Herman's instructions as they are very detailed. Some more links.
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

If you have a vendor based system, you probably have all 4 primary partitions used.
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create vendor recovery DVD(s) first. And a Windows repair CD.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by centaurusa on 2011-11-02
> **KelVarnsen said:**
> Did you use the Ubuntu installer to partition your drives? I've never partitioned a drive before so I'm a bit nervous about it. 

I have used Ubuntu's partitioner on a number of occasions, and it has always worked well.  These days, I tend to use the "Something Else" option which allows manual partitioning.  See: [http://linuxnorth.wordpress.com/manual-partitioning/](http://linuxnorth.wordpress.com/manual-partitioning/) for details.  On your system, the best bet would probably be to use the "side-by-side" option that, as it says, will install Ubuntu on the disk "next to" Windows 7.  You will end up with a dual-boot system that uses GRUB2 (GRand Unified Boor loader) as a start-up menu for selection of the operating system to be booted.

One reply to your question indicated that after partitioning you would need to format the drive to change the partitioning scheme.  This is not so.  For example, Ubuntu's manual partitioning allows you to delete partitions, i.e. the root partition and swap area, thus creating unallocated (free) space, which can then be used to add new partitions for a new installation.  Alternatively, you can use a bootable CD or USB memory stick with GParted ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) to re-partition the drive.

---

### Post by centaurusa on 2011-11-02
> **KelVarnsen said:**
>  Say for example I wanted to go back to windows or get rid of windows completly could I do this afterwards? 

Two further points on disk partitioning.

If you remove the Ubuntu partition, you will have to use the Windows installation disk to repair the boot sector of the hard drive.  GRUB2 lives on the Ubuntu partition so, once this is deleted, the Master Boot Record has to be modified to point to the Windows 7 system.

Another way to do this (that I highly recommend) is to make a complete backup of your hard drive (a disk image) using a freeware package such as Macrium Reflect ([http://www.opcug.ca/public/Reviews/MacriumReflectFree.htm](http://www.opcug.ca/public/Reviews/MacriumReflectFree.htm)).  Not only will this protect your data from possible disaster but, if you really want to remove Ubuntu, you can just reload the image and your disk will be exactly as it was before you installed Ubuntu.  Just be aware that any changes that you make after creating the disk image will be lost if you restore the "old" image.

I recommend using a separate data partition and making frequent backups of this.  The operating system isn't critical.  You can roll it back to an old image and then patch it back up to date using Windows Update/Ubuntu's Update Manager.  But, you need current backups of (original) data files.  You can make the data partition an NTFS drive under Windows.  Linux can see and use the same files on this partition but, if you try to use a Linux file system, Windows won't (will refuse to) recognize it.

---

### Post by philinux on 2011-11-02
> **KelVarnsen said:**
> Hi, I'm hoping someone can offer me some advice.

I'm planning on partitioning my hard drive and installing a dual boot with windows 7 and Ubuntu 11.10 tonight and there's a few things I'm unsure about because I haven't done anything like this before.

I have a 500GB HD and was wondering what would be the minimum amount I need for windows 7? I am only leaving it on for windows only programs like photoshop. Also is the partitioning permanant? Say for example I wanted to [-Xgo back to windows or get rid of windows completly could I do this afterwards? Does anyone know as well if the ubuntu installer is the best tool to do this? Some how to's I've read are saying to partition your hard drive in diferent ways.

Thanks for reading

Windows will only let you shrink it so far. I had this on laptop some files cant be moved and they were about half way into drive.

I also used easybcd to boot ubuntu and put grub on the root partition during install. Reason being laptop still under warranty.

---

### Post by Mark Phelps on 2011-11-02
> **KelVarnsen said:**
> I have a 500GB HD and was wondering what would be the minimum amount I need for windows 7? I am only leaving it on for windows only programs like photoshop.
Windows wants extra room, so an absolute minimum size is asking for trouble. I find 30GB to be a comfortable size for the Win7 OS.

However, that presumes that any large data files (i.e., photoshop stuff) is stored OUTSIDE the Win7 OS partition.
>  Also is the partitioning permanant? 
All partitioning is permanent.

> Say for example I wanted to go back to windows or get rid of windows completly could I do this afterwards? 
To go back to Windows, it would be best to do an image backup.  Macrium Reflect is a great tool and has already been mentioned. 

To get rid of Windows, you can do that by booting from an Ubuntu desktop CD and using a partitioning app to remove the Windows partitions.

> Does anyone know as well if the ubuntu installer is the best tool to do this? Some how to's I've read are saying to partition your hard drive in diferent ways.

I've found from personal experience, that the BEST tools for manipulating filesystems and partitions are the ones NATIVE to the OS in question: Windows tools for NTFS partitions, Linux tools for Ext3/4 partitions. When you use the Ubuntu installer to shrink the Win7 OS farther than it likes, you may encounter problems afterward with filesystem corruption.[/QUOTE]

Also, if you do install Win7, once you have it working, use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later should you encounter booting or filesystem problems in Windows.

---

### Post by KelVarnsen on 2011-11-03
Thanks for the replies everyone, this is really helpful stuff.

---

### Post by KelVarnsen on 2011-11-03
> **philinux said:**
>  I also used easybcd to boot ubuntu and put grub on the root partition during install. Reason being laptop still under warranty.

 Hi Phil, thanks for the reply. What do you mean about the laptops warranty? I'm also installing on a new laptop and hadn't considered this would affect the warranty

---

### Post by philinux on 2011-11-03
> **KelVarnsen said:**
> Hi Phil, thanks for the reply. What do you mean about the laptops warranty? I'm also installing on a new laptop and hadn't considered this would affect the warranty

I did not want to mess with the mbr in case it had to be returned.

---

### Post by larrypg on 2011-11-03
Hello all,  I might have missed it but the first thing you should do is to find out how many partitions you already have.  Many times a new computer comes with all four allowed partitions already used.  My new computer for example had three used which only left one available.  I made that an extended partition and put logical partitions inside it.    Just thought I would mention that just in case you had not considered it.

---

### Post by bobpur on 2011-11-03
I'm dualbooting Windows 7 Starter and Lubuntu 11.10 in an Acer Aspire One Netbook D257. I maxed out the memory (2 gbs) and added a 7200 rpm WD hard Drive of 500 gbs. The whole thing was pretty straightforward. 
I partitioned the hdd with a 60 gb partition for Win7. 2 gb "Swap' partition, and then a 60 gb partition for Lubuntu. The remainder of the drive was partitioned as NTFS for storage.
I saved the original hard drive intact in an anti-static bag. I used a new "blank" drive for the dualboot. 
Lubuntu installed with the wireless drivers functioning so I didn't have too hardwire the internet for updates. I don't know if this works for all wireless cards; but, it was a pleasant surprise as i was on the road and didn't have a hard wired hookup available.
Good luck.

---

### Post by KelVarnsen on 2011-11-07
Hi everybody, just wanted to say thanks for all the help and advice. I've got my dual boot up and running and didn't experience any problems thanks to this thread and all the links.

Cheers again guys

---

### Post by Rubi1200 on 2011-11-07
No problem, you are more than welcome :)

Glad we were able to help and that you can enjoy your system.

---

