---
title: "Installing Ubuntu"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by Gian_Ross on 2014-03-16
I'm trying to install Ubuntu 12.04 on it's separate HDD, which will dual boot with Win7 on an SSD. The problem I keep having is it won't save what I add. For example, /boot, /, /home and swap. What am I missing here.

Please I'd appreciate any help

thx:)

---

### Post by oldfred on 2014-03-16
Do you have any sort of special configuration? May be best just to see details.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Gian_Ross on 2014-03-16
I'm sorry, I'm sure I'm not clear. The problem I'm having is, if I 'add' /boot and then go to add another (/, /home or swap), /boot gets overwritten, and on and on.It only lets me add that one time, every other time it only lets me use change (hence the overwrite I'm sure)? I am under the impression to use the free space of my drive and add these in this order: /boot, /, /home and swap, is that correct? If not would you please tell me the correct way? If you need me to list drives or something, please let me know.

Thx in advance :)

---

### Post by mastablasta on 2014-03-17
> **Gian_Ross said:**
> I'm sorry, I'm sure I'm not clear. The problem I'm having is, if I 'add' /boot and then go to add another (/, /home or swap), /boot gets overwritten, and on and on.It only lets me add that one time, every other time it only lets me use change (hence the overwrite I'm sure)? I am under the impression to use the free space of my drive and add these in this order: /boot, /, /home and swap, is that correct? If not would you please tell me the correct way? If you need me to list drives or something, please let me know.

Thx in advance :)

why do you need separate /boot and why do you plan separate /home?

can you post some screen shots or video of what you are doing when creating partitions so that /boot gets "overwriten". btw i don't think anything is actually done until you go to next step.

---

### Post by buzzingrobot on 2014-03-17
> **Gian_Ross said:**
> ...if I 'add' /boot and then go to add another (/, /home or swap), /boot gets overwritten, and on and on.It only lets me add that one time, every other time it only lets me use change (hence the overwrite I'm sure)? I am under the impression to use the free space of my drive and add these in this order: /boot, /, /home and swap...
  

Are you using the "Something Else" option in the installer to manually create your partitions?  Typically, you create one new partition in the available free space, then create another in the remaining free space, etc. , until you stop or run out of free space.

---

### Post by Gian_Ross on 2014-03-17
@[COLOR=#000000]mastablasta, 

I got that idea from this article [http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
How can I take screenshots while I'm trying to install?

@[/COLOR][COLOR=#000000]buzzingrobot,

Yes I was using "something else" option. When I thought I was suppose to add /boot, /, /home and swap, if I added /boot it would let me "add", when I went to add any of the others, it would only let me choose "change", which I'm sure was why it overwrote. Its being installed on its own 500GB HDD, so what partitions do I create please?

TY both for your help, I appreciate it

Rosso[/COLOR]

---

### Post by whitesmith on 2014-03-17
Simply install to a single partition on an HDD separate from your Windows drive to reduce complexity. You'll wind up with an upside down tree with / at the top and a bunch of directories dangling off of it. One of these will be /home and, under that, your own home directory (/home/your-user-name). This is where all personal data is stored. I urge you not to try fancy footwork until the OS becomes more familiar. Cheers!

---

### Post by Gian_Ross on 2014-03-17
thats the problem, I need help doing that.

TY

---

### Post by oldfred on 2014-03-17
Did you only have one remaining primary partition and you made /boot that partition. Linux works from logical partitions, but all logical partitions must be inside one extended partition and the extended partition counts as one primary partition.

I usually create partitions with gparted as it is a bit easier, but you still have to use Something Else to choose which partition is /, which is /home and formats like ext4. If swap already exists it seems to find that automatically.

Post this from live installer:
sudo parted -l

If you boot into live mode and then click on install, you can still get to screenshot.

---

### Post by Gian_Ross on 2014-03-17
I have my SSD (win7) then I have an 1TB (programs) and 500GB, which is the one I want to use only for Ubuntuwith no partitions, which is all free space right now.

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAVS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Model: ATA OCZ-AGILITY3 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   120GB  120GB  primary  ntfs


Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot


Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdd: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  15.6GB  15.6GB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: Can't have a partition outside the disk!

---

### Post by grahammechanical on 2014-03-17
We cannot install with a / partition and a /boot partition and a /home partition without first creating partitions. If we tell the installer which hard drive and which partition to install Ubuntu in by telling it which partition should be / then Ubuntu will install into that partition and /boot and /home will be folders inside the / folder in Ubuntu.

If there is only one partition the installer has no choice but to only offer to change the designation. The mounting/location of / should be first. Then Ubuntu will install but /boot and /home will not be in partitions but in folders under / folder. To install boot into its own partition requires a partition to be available. To install home into its own partition requires a partition for it to be available.

The partitioner should be showing available partitions which we select and then click "Change" for we are going to change the use of the partition. If we select the same partition that we have just told the installer what we want it used for then the partitioner will only offer "Change" we are going to change its use.

Regards.

---

### Post by buzzingrobot on 2014-03-17
When you created /boot first on the 500 GB drive, how did you size it?  

I don't have an installer in front of me, but, if memory serves, if you create only one partition, the installer allocates all remaining disk space to it. If /boot is the first partition created, and if its size is not reduced, then it will consume all the free space.  As a result, you would not see an option to create new partitions, but only one to change the existing partition.

As oldfred mentioned, creating only '/' will set it to use all free space. /Boot, /home, etc., will be created as *directories* within that partition. (You need at least one partition.  The rest can be created as directories within that partition.)

Usually, if I am using only one drive, I first create a swap partition of a specific size, and then use the rest of the drive for '/'.

---

### Post by Gian_Ross on 2014-03-17
[B]That makes sense guys, if I understood correctly I need to just create / and that will do the rest? All that is needed then is a / (I create), which will create /home and swap? How would I make swap a certain size, by creating a seperate partition and if so how?

TY :)[/B][URL="http://ubuntuforums.org/member.php?u=1087323"][B][COLOR=#000000]
[/COLOR][/B][/URL]

---

### Post by newb85 on 2014-03-17
Yes, make sure you select the empty space before trying to create the second partition. And there's no need for a separate/boot partition.

---

### Post by buzzingrobot on 2014-03-17
Create the partition you want to use for swap, then set it to "Swap" in the same popup you use to set the filesystem type. I.e., where you choose Ext4, Ext3, etc. (A swap partition doesn't need to be formatted, so don't worry if that option is greyed out.)

After that, highlight the remaining free space on the drive, set it for '/', choose your filesysytem type, set it to be formatted, double check everything, and you should be good to go.

(Or, figure out how much space you want to allocate to swap, subtract that from the total free space, create '/' sized to that figure, and then make swap in what's left.)

There is only one really firm rule about the *size* of a swap partition, I believe:  If you want the machine to hibernate,  the swap partition needs to be at least as large as the total amount of installed RAM.

Otherwise, you can find many recommendations to size it at about twice the size of RAM.  It is not a critical decision.

Swap is used when RAM fills up.  Bits are written off to the drive to free up room in memory.  When those bits are needed, something else in memory is written out to the swap partition, and the required bits are read in.  This works, and keeps things going that would otherwise probably just stop.  But, it is slower, a lot slower. It's pretty obvious when your machine is swapping.

A memory-constrained machine these days is something with only 1-2 gigs of RAM. I'd certainly create something like a 4-gig swap partition for that.  Machines with 4, 8, or more gigs of RAM will seldom need to resort to swap unless something particularly memory intensive is done (loading and processing dozens of very large photo files, etc.). For those machines, I'd create a swap partition of a couple of gigs, as a just in case measure.

---

### Post by newb85 on 2014-03-17
Oops, missed your last post.   Yes, with just one partition, home, boot, and swap will all be files in that partition. Some would argue the merits of a separate partition for /home, but it's certainly not necessary.

---

### Post by Gian_Ross on 2014-03-17
I guess I still don't understand what I'm doing wrong. I created a swap partition using 'gparted'. Then went in to the installer, chose 'try something else' and my only option was to change delete or revert.

What could I be doing or not doing?

TY

---

### Post by oldfred on 2014-03-17
Are you trying to install inside the NTFS partition? 
You have to have one partition for / (root) formated ext4 and mounted as / and one partition unformatted as swap. All other partitions like /home then are optional.

I typically suggest / of 20 to 25GB and swap of 2GB if you have lots of RAM and do not hibernate.
If storing most data into your NTFS data partition(s) you can have just 20 or 25GB. Later you may want more space and could then create /home or Linux formatted data partitions.

 [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


 Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by Gian_Ross on 2014-03-17
Attached are my current drives. The drive in question, disk2, is all for Ubuntu 12.04, which I have nothing on, it's marked as free space. It seems I need a / partition, which I assume will be the whole drive, formatted in ext4? In turn it will create my /home and swap partitions, correct? I would like to give me swap 10GB partition, do I do something special for that? Is there anything I'm missing?

TYAllVM :)

Rosso

---

### Post by oldfred on 2014-03-17
You cannot create partitions inside partitions.
So you can create a / (root) partition of 25GB formatted ext4, a /home partition for all but what you want for swap formatted ext4, and swap at end of drive. I would not create a large swap. 
With Ubuntu you do not need to hibernate as it boots quickly. And if you have a lot of RAM or over 4GB you may only need 2GB and never actually use that. You do not want to use swap as it it orders of magnitude slower than RAM.
On the partition screen choose to install grub2's boot loader to the MBR of the same drive and change BIOS to boot that drive.

---

### Post by Gian_Ross on 2014-03-17
> **oldfred said:**
> You cannot create partitions inside partitions.
So you can create a / (root) partition of 25GB formatted ext4, a /home partition for all but what you want for swap formatted ext4, and swap at end of drive. I would not create a large swap. 
With Ubuntu you do not need to hibernate as it boots quickly. And if you have a lot of RAM or over 4GB you may only need 2GB and never actually use that. You do not want to use swap as it it orders of magnitude slower than RAM.
On the partition screen choose to install grub2's boot loader to the MBR of the same drive and change BIOS to boot that drive.

OK, so root (/) I'm making 25 GB, which will make the rest of the drive /home, correct? How do I specify a size for the swap?

ty :)

---

### Post by oldfred on 2014-03-17
Same way, just once you select swap it will not let you check format.

With gparted (and I have not used installer for ages to create partitions) you could specify both size and location meaning left or right. You can then either add swap after creating /home that leaves some room for swap or create swap on the right side with unallocated between / & swap, and then you create /home in all the remaining space.

---

### Post by buzzingrobot on 2014-03-17
> **Gian_Ross said:**
> OK, so root (/) I'm making 25 GB, which will make the rest of the drive /home, correct?

No. The creation of the '/' partition will reduce the size of the available free space, but that's all. A /home *partition* will not be created.

You need a /home *directory*.  You do not need a /home *partition*.  /home does not need to be on a partition all its own. Linux is pefectly happy if it is not. Whether or not /home is given its own dedicated partition, it remains one of many required directories in the Linux filesystem.

If you use the *Ubuntu installer* to create the '/' partition and create no other partitions, the installer will install Ubuntu on the '/' partition and will also create a /home directory and all other required directories.  They will all reside on the '/' partition.

If you use gparted, or any similar tool to create partitions before you run the installer, and do not create any partitions in the installer, the only partitions created are those you created earlier.  

The installer does not know what you want to do with partitions created elsewhere.  I.e., it does not know that a partition created in gparted for use as '/' is, in fact, to be used as '/' until you tell it.

If you use gparted to create what you want to be the '/' partition, you still need to mark it as the '/' partition in the installer.  All the installer knows is that it found a partition.  You need to tell the installer what to do with it. (Regardless of how it was created, the partition to be used as '/' must be identified as such in the installer.  If '/' is the only partition known to the installer, it will create /home, and all the other needed directories in it.)

Also, if you run run gparted while you are running a live cd/dvd, it's a good idea to reboot before you begin the install. Partition changes often require a reboot to register. (The live image reads the partitions as they exist when you boot it.)

> How do I specify a size for the swap?



See my previous reply. You need to create and size it after selecting the "Something Else" option in the installer.

You can also create and size it in gparted. Just make sure the installer see it as the swap partition.

---

### Post by Gian_Ross on 2014-03-17
Ok, I used Gparted to creat a 25GB / partition, after that it won't let me specify a swap size and in the installer I can only change what I created ingparted

---

### Post by buzzingrobot on 2014-03-17
Did you create a swap partition?

---

### Post by Gian_Ross on 2014-03-17
This is what I got, but it wont let me move the swap to the end

---

### Post by buzzingrobot on 2014-03-17
Swap appears to be at the end.

Are you setting the size of the partitions?  What's shown is a '/' partition of 7.5 gigs and a swap partition of 458 gigs, i.e., you appear to have created a swap partition using all the rest of the free space, without sizing it.

If you want a partition to take X amount of space, you need to set the space it takes.

Delete all existing partitions.  Create a '/' of the desired size.  Then create a swap partition of the desired size.  You should see them listed in those sizes, with the remainder of the disk as free space.

Note: the /home, etc., directories will be created in the "/" partition you create.  They will not use any free disk space. If you create a '/' partition of 25 gigs, and that leaves free space totaling, let's say, 450 gigs, then, after the install completes and all the directories are created, those directories -- the entire Ubuntu installation -- will all reside within the 25-gig '/' directory.  You would still have 450 gigs of unused free space that the filesystem will not see.

---

### Post by oldfred on 2014-03-17
You may have labelled it swap but it is not swap as you have it formatted.

I would delete both partitions as long as you have no data to save or back that up first and start over. Your sda1 of 7.5GB is too small for / (root) better to be 20 or 25GB.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

With gparted you have the amount of space before or after which controls where on drive new partition goes.

 [http://www.dedoimedo.com/images/computers/2009/gparted-create-extended.png](http://www.dedoimedo.com/images/computers/2009/gparted-create-extended.png)

---

### Post by Gian_Ross on 2014-03-17
I meant the / to be 25 GB and the swap 4GB, did I do it right, hhows it written in bytes?

ty

---

### Post by oldfred on 2014-03-17
I think the partition tools always do MB, so you have to add 1000. But there is the MB vs MiB but that should not be a concern as sizes will be slightly different in GB.

I am reusing a 26GB partition in attached. It shows size in MB. This is from installer, as I create partitions with gparted but still have to specify which partition is which, format etc as shown. Note location of boot loader.

---

### Post by buzzingrobot on 2014-03-17
As oldfred said, you need to designate the filesystem used for swap as 'swap".  The image shows it as Ext4.

In decimal, a gigabyte is 1,000,000,000 bytes.  There are 1,000 megabytes in a gigabyte, speaking decimally.

---

### Post by Gian_Ross on 2014-03-17
Ok, please tell me this is correct? I'm tired, as I'm sure you'll agree, with this sadness.

ty :)

---

### Post by buzzingrobot on 2014-03-17
Yes, you have created a 25-gig '/' partition which will contain your entire Ubuntu system.

You have  created a 4-gig swap partition.

You have 437 gigs of unallocated free space which will not be available to Ubuntu.

---

### Post by 3rdalbum on 2014-03-17
Gian, creating different partitions for everything is not necessary. The Ubuntu installer offers to erase the SSD and install itself there, which is the screen with the options "Erase disk" and "Resize Windows" and "Something else". It will be easiest for you because the Ubuntu installer sets up everything got you.

If you want to create partitions using the "Something else" screen, just create your 4gb swap partition and make the rest of the disk your / partition. Don't worry about /home, it will be part of the / partition.

If anyone tells you that you need a /home partition so you don't lose data when you upgrade Ubuntu, please tell that person to stop living in 2008. And then hit them on the head with a recent Linux book.

---

### Post by Gian_Ross on 2014-03-18
@3rdalbum,

Ubuntu installer only presents me with installing Win7/Ubuntu side by side, which I don't want or something else.

@buzzingrobot, 
[COLOR=#000000]
you say I have / and swap correct not sure what you mean 
[/COLOR]> [COLOR=#000000]

You have 437 gigs of unallocated free space which will not be available to Ubuntu.[/COLOR]

---

### Post by oldfred on 2014-03-18
You did not create a partition in the 437GB space. It is still shown as unallocated.

---

### Post by buzzingrobot on 2014-03-18
Operating systems can't use space on a drive unless it is partitioned. That applies to Windows, Linux, OS X, etc.

File systems are created in partitions.  That's what happens when you tell the installer to format a partition.  You select one of several kinds of file systems, and the installer creates it. After that, files can be created and written to the drive.

---

### Post by Gian_Ross on 2014-03-18
OK, I got what you meant and fixed it. Now what does itmean when it says set mount point on partition3 and what would it be?

ty :)

I assume this will let me choose what OS at boot?

---

### Post by buzzingrobot on 2014-03-18
> **Gian_Ross said:**
> OK, I got what you meant and fixed it. Now what does itmean when it says set mount point on partition3 and what would it be?

Depends on what you want to use partition 3 for.

For example, if you want it to be the '/' partition, then you select '/' in the drop down list.  That's the 'mount point'. You'll see other common mount points listed there, as well.  

Filesystems go on partitions.  In Linux, partitions need to be mounted before the filesystems can be used. The partitions that you create during an install are automatically mounted during the boot process.

> I assume this will let me choose what OS at boot?

Nope, that's something else, called 'grub'. If you have only Ubuntu installed, you will not see a menu to choose the OS.

---

### Post by Gian_Ross on 2014-03-18
What I want partirtion 3 for, and Ubutu, is so hopefully, eventually I won't have to rely on Windows much, if at all. That being said, what makes sense for the mount point please? /home, /usr/var etc..?

'Thx

---

### Post by buzzingrobot on 2014-03-18
> **Gian_Ross said:**
> What I want partirtion 3 for, and Ubutu, is so hopefully, eventually I won't have to rely on Windows much, if at all. That being said, what makes sense for the mount point please? /home, /usr/var etc..?

'Thx

You *must* have a '/' partition.  I strongly recommend having a swap partition, as discussed upthread. 

Since you are asking about partition 3, is partition 1 '/' and partition 2 the swap?  If so, the common use for your partition 3 would be as '/home'. (The installer will create a '/home' directory regardless.  If it finds a '/home' partition it will create it there.  Otherwise, it will create a '/home' directory on the '/' partition. )

---

### Post by oldfred on 2014-03-18
I suggest /home, but you could leave it unmounted during install and just make it a data partition later. But that is a bit more complicated.

You also want to change the boot loader destination to sdc or whatever drive your install is in. And then change BIOS to boot from that drive as default. Combo box on drives to install bootloader is at bottom of partitioning screen. See post #30.

---

### Post by Gian_Ross on 2014-03-18
THIS POST IS SOLVED

Thank you all for your help, really. Ubuntu is installed, now I need to make sure my hardware took.

Thx again all :)

---

### Post by buzzingrobot on 2014-03-18
> **Gian_Ross said:**
> THIS POST IS SOLVED

Thank you all for your help, really. Ubuntu is installed, now I need to make sure my hardware took.

Thx again all :)

Nice!  Welcome to Ubuntu.

(You can mark the thread solved by clicking "Thread Tools" at the very top of the thread.)

---

