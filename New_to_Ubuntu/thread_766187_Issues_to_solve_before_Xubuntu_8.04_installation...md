---
title: "Issues to solve before Xubuntu 8.04 installation.."
date: 2008-04-25
forum: New to Ubuntu
---

### Post by SweetBearCub on 2008-04-25
I have three issues to solve before I can install Xubuntu 8.04. Any help with them would be appreciated.

1) The system is currently loaded with Windows XP Home SP2. XP is on an NTFS partition which occupies the entire HD. My data is co-mingled with the OS in the 'My Documents' directory. I'd like to find a way to shrink the NTFS partition down so that I can allow space for a Linux Ext2 (Or is that Ext3?) partition, a swap partition, and finally, a partition that both XP and Xubuntu can make use of for storing data w/ read & write access.

When I booted the Xubuntu 8.04 LTS LiveCD and started up the installer, the part where you set the partitioning options was of absolutely zero help. In its default mode, it wanted to 'use entire disk'. I didn't think that was a wise idea, so I switched to manual mode. In that mode, it listed my NTFS partition, but gave no way to shrink it, or to create the other partitions I needed.


2) My only source of Internet access is through my Sprint Mogul PocketPC, which is running its built-in Internet Sharing application to share out Sprint's EVDO RevA network with my desktop via USB.

In Xubuntu, my PocketPC is not seen at all, as far as I can tell. I did some Googling on this, and I did find some stuff, but there were a few problems:

A) I have no idea what the numerous commands I was supposed to enter in terminal were doing, and consequently, would have no idea how to correct any errors that might occur.

B) The procedure appeared to assume that I already had Internet access working in Linux. For me, this is not the case. Therefore, I must download whatever files are needed before I Install Xubuntu. To that end, I have a 1 Gig NTFS formatted USB stick. (512 byte allocation unit size, compression enabled - These options allow me to squeeze as much data as possible onto it.) I'm not sure if Xubuntu can deal with that, as the allocation unit size is smaller than the normal NTFS default, and I have no idea how the NTFS driver handles file-system level compression.

C) The procedure appeared to be written for another Linux distro, and did have notes to the effect that some things might be different on other distros. Considering that I have very little Ubuntu (or Linux) experience, and will have no Internet while I work, this isn't good. The only way I'll be able to get Internet access is by rebooting into XP, or by via Pocket Internet Explorer on my PocketPC, which is pretty limited.


3) When XP SP3 is released, I plan to slipstream it into a copy that has no service pack, and then customize it with nLite, so that I can be assured of a clean install CD. I'll then want to blow away my current copy of XP and reload my system. however, I have no idea how Xubuntu (Or its bootloader) will react to this. Negatively, I'd bet. What should I do so that this soon-to-be upgrade goes well?


Thanks!

---

### Post by zvacet on 2008-04-25
> In that mode, it listed my NTFS partition, but gave no way to shrink it, or to create the other partitions I needed.

Of course,because your entire HDD is NTFS and Ubuntu have no choice.

> The procedure appeared to be written for another Linux distro

Don´t follow guides for other distros.You can go wrong way with that.It is better to find something Ubuntu related or ask here.

If you plan to reinstall Windows leave some place (unallocated space) for Ubuntu.

---

### Post by MikeMLP on 2008-04-25
Here is what I would do:

1. - get a "real" source of internet if possible, via ethernet Bring your box to a friend's house.

2. - If that is not an option, think about whether you would find Xubuntu at all valuable to you without an internet connection, since getting one piped through a pocket pc may not be possible without a whole lot of effort (and a "real" internet connection, or a second computer with a "real" internet connection).

3. - If you are still set on installing Xubuntu, but find the partitioner on the disc unable to resize properly, try downloading the Gparted livecd [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") and using that to repartition ahead of time.  You should then be able to set mountpoints and install as desired.
     As far as partition planning goes:  I have a fat32 partition that I use to shunt files between Windows and Ubuntu.  Now that Ubuntu (and, I would think, Xubuntu) has NTFS read/write support, you might want to consider making that third partition an NTFS partition because NTFS will allow you to read and write certain system files that Fat32 will not.  Fat32 sucks for trying to back up /home, for example, because files with certain permissions don't carry over. If you don't need to keep your files separate from both operating systems, then just install Xubuntu and XP without an intermediary partition.  However I believe that write support for EXT2/3 does not yet exist for NTFS.  For read support you'd have to install a driver, I believe it is EXT2IFS.
     With linux, some people also make a separate partition for their home directory (you can set a separate partition as the mountpoint for /home in the install process.  I've never bothered to do this, and it can cause trouble when settings are carried over across different versions of programs, etc..

3.  As far as bootloaders go, an automatic install off the live cd will install the bootloader (GRUB) to your MBR.  This is ideal because it is simple and effective.  Unless you choose to wipe your entire drive during the Windows install, and do not tell it to use only unallocated space, reinstalling Windows will not wipe out Xubuntu.  
     HOWEVER,reinstalling Windows after you install Xubuntu will wipe out GRUB so that you will not be able to boot into your Xubuntu install.  To fix this, you'll want to reinstall GRUB only (and not the entire OS).  I've had to do this before, and I've done it by burning an Ubuntu Alternate CD.  Using this CD, you can choose to perform only one step of the install process.  You find an entry to install GRUB, and do it.  It should detect your Windows and Xubuntu installs, and list the automatically.

4.  As for your getting your PocketPC to work with Xubuntu... I don't know.  Someone else might have an answer.  If not, your best bet is to search the net, as you have been doing.

---

### Post by warbread on 2008-04-25
> **SweetBearCub said:**
> I have three issues to solve before I can install Xubuntu 8.04. Any help with them would be appreciated.

1) The system is currently loaded with Windows XP Home SP2. XP is on an NTFS partition which occupies the entire HD. My data is co-mingled with the OS in the 'My Documents' directory. I'd like to find a way to shrink the NTFS partition down so that I can allow space for a Linux Ext2 (Or is that Ext3?) partition, a swap partition, and finally, a partition that both XP and Xubuntu can make use of for storing data w/ read & write access.

When I booted the Xubuntu 8.04 LTS LiveCD and started up the installer, the part where you set the partitioning options was of absolutely zero help. In its default mode, it wanted to 'use entire disk'. I didn't think that was a wise idea, so I switched to manual mode. In that mode, it listed my NTFS partition, but gave no way to shrink it, or to create the other partitions I needed.




There is a way to shrink NTFS partitions, but I advise against it.  It's not reliable, and the time spent trying to do it right and then recovering from the inevitable data loss is better spent backing up valuable information and then doing a fresh install of both OSes.  That's just my experience, though, and you may have better luck.  

That said, if you're set on resizing your partition, make sure you defragment the drive first. 

The partitioner you were talking about (called gParted) is what you want.  It's useful, and actually very easy to use.  It will show your partition as a long colored block.  There should be a "resize" button on the top of the window.  That will let you specify the size you want for the partition, which will leave the remainder of the hard drive empty.  From there, you hit the "new" button and specify the size/type/mount point of the new partition you want created from the empty space.  

I suggest doing a "sudo apt-get install gparted" in terminal from the live boot and running the partitioner from there instead of loading up the installer.  From the program proper, I would do each step one at a time.  Resize the partition, and then hit "apply" to finalize.  Then create a new partition and hit "apply" once again.  Do this until  you're done.  

The instructions are spartan, but there are tutorials online for doing this sort of thing.  The point I'm trying to make is that you have the tools you need, but I suggest you go the safer route and do two fresh installs.  

And, of course, no matter what you do, back up your valuable information.

---

