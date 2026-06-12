---
title: "Dual Boot Ubuntu with Windows 64bit Shared Data Partition?"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by Cheeky88 on 2012-02-09
Hi There!

I only just discovered how awesome Linux was by playing with a live CD, I also love the Linux GNU concept - I'm pro liberty and freedom, but I need to use windows for certain applications. 

I would love to set up my installation so that I can use Ubuntu(32bit), Windows7 (64bit) and Share data with a seperate partitian (NTFS)

Now, Is there a tutorial that can set me up with this? 

I have a 1TB internal drive, which I am about to DBAN with zeros and start fresh. 

I will install windows 7, now, should I chose a "install all on one partitian" or "install to OS partitian and have a seperate data partitian"?

Then what do I do to install Ubuntu with a shared partitian. 

Also, what are the ideal sizes for both OS's

---

### Post by hildenbrandsteven on 2012-02-09
It doesn't matter what size you set them as... lughinux can read NTFS/ext partitions, Windows can only read NTFS/FAT parttitons. You *may* run into problems with permissions though.

---

### Post by QIII on 2012-02-09
May I ask why you would use 32 bit rather than 64 bit?

(I'm on my cell right now or I'd link in some tutorials for you now.  You can use the forum search functionality.  There are a number of good resources here.)

---

### Post by Cheeky88 on 2012-02-09
32bit is recommended by ubuntu.com I want everything to run, even if I am sacrificing a bit of speed, I only have 4GB of ram.

Should I make a 64bit disc?

---

### Post by centaurusa on 2012-02-09
> **Cheeky88 said:**
> 
I would love to set up my installation so that I can use Ubuntu(32bit), Windows7 (64bit) and Share data with a seperate partitian (NTFS)


With a 1TB hard drive, assigning space to individual partitions is no problem.  Ubuntu will run in less than 5 GB, but you can easily afford to make it much bigger and never have any space issues.  Similarly, it is likely that Windows 7 won't need more than about 40 GB, but that partition too can be made much larger on your disk.  

The main issue is the size of the data partition.  Clearly, this depends on the amount of data that you have to store.  

I would concur with using an NTFS partition for this purpose.  In this way, you can share precisely the same files (e.g. word processing, digital images, etc.) in both operating systems, and it becomes very easy (and quick) to back up the data independently of the OS and applications.

FYI, I have Ubuntu 10.04 LTS and Windows 7, both running in 64 bit versions and have not experienced any issues with software that won't run in one machine or the other.
 
Once you have Windows 7 installed in an OS partition, and have established a second data partition, install Ubuntu and select the dual-boot, side-by-side, or whatever your distro calls this option.  

You can either resize the (large) data partition at this point to free some unallocated disk space and let the installer use this for Ubuntu, or leave a bunch of free space on the disk when you create the OS and data partitions and have the installer use this block of the disk for Ubuntu.

---

### Post by Cheeky88 on 2012-02-09
> You can either resize the (large) data partition at this point to free  some unallocated disk space and let the installer use this for Ubuntu,  or leave a bunch of free space on the disk when you create the OS and  data partitions and have the installer use this block of the disk for  Ubuntu. 	

So 64bit is the way to go? I am going to use the latest version. 

I am going to follow this tutorial, if someone could lemme know if that fits my goal, I will be stoked. 

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

Thankyou so much for the advice :)

Does the OS allocation include programs you want to install or can they go the the data partition?

---

### Post by Mark Phelps on 2012-02-09
IF you install Win7 to a blank drive, it's going to create TWO partitions -- a boot partition and an OS/programs/data partition.

You can avoid this by first, creating a 50GB (what I would recomment) NTFS partition on the blank drive using Gparted run from an Ubuntu desktop CD.

Then, when you go to install Win7, have it reformat that partition. I know this sounds redundant, but it is the best way to go in the long run.

If you decide, instead, to let Win7 take the whole drive, do NOT then use the Ubuntu installer to shrink it down; instead, boot into Win7 and use the Disk Mangement utility to do the shrinkage.  This will avoid the risk of filesystem damage that sometimes occurs using the Ubuntu installer slider to shrink Win7 OS partitions.

---

### Post by Cheeky88 on 2012-02-09
> **Mark Phelps said:**
> IF you install Win7 to a blank drive, it's going to create TWO partitions -- a boot partition and an OS/programs/data partition.

You can avoid this by first, creating a 50GB (what I would recomment) NTFS partition on the blank drive using Gparted run from an Ubuntu desktop CD.

Then, when you go to install Win7, have it reformat that partition. I know this sounds redundant, but it is the best way to go in the long run.

If you decide, instead, to let Win7 take the whole drive, do NOT then use the Ubuntu installer to shrink it down; instead, boot into Win7 and use the Disk Mangement utility to do the shrinkage.  This will avoid the risk of filesystem damage that sometimes occurs using the Ubuntu installer slider to shrink Win7 OS partitions.

Ok, so should I use Gparted to make all three sections, or just the windows and storage, then let the ubuntu install split the storage?

---

### Post by wolfen69 on 2012-02-09
> **Cheeky88 said:**
> 32bit is recommended by ubuntu.com 
That is kind of outdated at this point. Starting with ubuntu 12.04, the default ubuntu iso will be 64bit. I've been running 64bit for over 2 years with no issues. 
> Should I make a 64bit disc?
Imho, yes. You should have no issues. 64bit is becoming the standard these days.

---

### Post by Cheeky88 on 2012-02-09
> **wolfen69 said:**
> That is kind of outdated at this point. Starting with ubuntu 12.04, the default ubuntu iso will be 64bit. I've been running 64bit for over 2 years with no issues. 

Imho, yes. You should have no issues. 64bit is becoming the standard these days.

Done and Done :D

Now all I need to know is do I use gparted to make the three partitions? (WINOS UBUNTUOS and SHARED STORAGE)

Or do I use gparted to just make the windows and shared, then let the ubuntu installer split the shared?

Sorry if these are dumb questions, I only found out about linux yesterday when my computer got infected and I needed a way to move files safely from the infected PC (ubuntu live CD ftw)

---

### Post by Lateralis on 2012-02-09
These aren't dumb questions at all! You're new, and Ubuntu forum members are glad to help you out. =) 

If I were you, I would get a rough idea of what your hard drive will look like before you start installing anything.  For me, this is what I would do.  I can't say that this is what you must do, or what you should do, or if this is even the best way to do it.  This is only my opinion; I am sure if someone will correct me if they see a problem or an error.  


If you want to nuke the whole hard drive and start afresh, which is what you said in your first post, I would load up the Ubuntu live CD and use gparted to nuke the whole drive.  With a blank drive, I would create 1 primary partition for Win7, 1 primary partition for the shared storage and then 1 logical partition for Linux. 

Then use the Win7 installation to format your Win7 OS partition and, if you can, the shared storage space.  If you can't format the shared space in the installer, do so in Win7 after the install. 


When you install Ubuntu, you will need as a minimum two partitions - 1 for the "root" of the filesystem (mount point '/') and one for swap.  I don't know how much you know already about Linux, but the swap aware acts as memory.  It is also where your RAM gets dumped to when you hibernate.  For the latter reason, most people would recommend making your swap partition *at least* as large as the amount of RAM you have.  If you do not intend to hibernate, the swap can be smaller than the amount of RAM you have.

One of the great things about Linux though, is that partitions are mounted to different parts of the filesystem as directories.  For instance, you may want to consider having three partitions:

1 partition for "root" (mount point '/')
1 partition for swap 
1 partition for "home" (mount point /home)

The /home directory is kind of equivalent to the Windows "Users and Settings" folder, which is where people keep their user-specific configuration files, music, videos and so forth in their own personal folders.  In Linux, you can easily keep these directories in a separate partition and then have that partition mounted at /home.  Then, if you want to install the latest and greatest version of Ubuntu, you can do a fresh install whilst leaving /home untouched.  

This also means that more complicated partition schemes can be devised, with each partition using a file format which is suited to the task of that partition.  I, for instance, have partitions for '/', /home, /var and /tmp and /media/data.  

Separate to this is how much space you will need for each partition. You should know roughly how big you want your Win7 system partition, but for the Linux partitions I would recommend your swap partition be equal to your RAM size and '/' equal to around 125-150 GB if you do not go with a separate /home partition.  If you have a separate /home, then you will need around 15-20 GB for '/' and maybe 100-120 GB for /home.  The rest can be for your shared data partition.  


I hope this isn't too long, boring or telling you things you already know!  

As I said at the start of the post though, we Ubuntu users like answering questions.  If you have any more feel free to post them!

---

