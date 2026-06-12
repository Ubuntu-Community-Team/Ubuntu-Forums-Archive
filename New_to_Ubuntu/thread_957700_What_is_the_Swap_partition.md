---
title: "What is the Swap partition?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by CoreyB. on 2008-10-24
I am looking into installing Ubuntu when 8.10 drops.  I currently have Vista installed.  I have a Dell Inspiron 1525 laptop.  I already have four partitions:  1. C: Has Windows and data on it (220.32 GB),  2. D: Called the Recovery drive (10.00 GB), 3. Has no name or letter, just says 'Healthy (EISA Configuration)' (71 MB), 4. No name, no letter, says 'Healthy (Primary Partition)' (2.50) GB.  Either partiton 3 or 4 is used by Dell for Dell Media Center, I think it is 4 but I am not sure.

I read that there is supposed to be a Swap partition when you install Ubuntu.  I am wondering what how I have to partition my HDD to have Vista and Ubuntu dual booting and without having to install Vista.

If you could provide details of what programs to use and in what order that would be great, bit of a newb here.
Thanks in advance!

---

### Post by northern lights on 2008-10-24
> **CoreyB. said:**
> I read that there is supposed to be a Swap partition when you install Ubuntu.
The swap partition is the virtual memory in GNU/Linux.

Virtual memory is space on the hdd that is used once the physical memory (RAM) has filled up.

The Windows equivalent is the *pagefile.sys* in *C:\Windows*

> **CoreyB. said:**
> I am wondering what how I have to partition my HDD to have Vista and Ubuntu dual booting and without having to install Vista,
Pop in the LiveCD. Make sure the CD-Drive is part of the boot sequence (BIOS). Boot from the CD. During the Ubuntu installation process, make sure you don't select "Guided partitioning - use whole disk", since that would erase your Windows partition. Instead choose "manual partitioning".

Resize the Vista drive ("C:") to around 220-X gig. Create a 15 gig Ubuntu partition, a Y gig /home partition (depending on how much data you think you'll acquire in /home and how full the Vista partition is) and a 2 gig swap space.
Naturally X=15+2+Y.

Install following onscreen instructions.

Keep in mind that you cannot have more than four primary partitions. Hence, Vista should remain your first primary partition, Ubuntu the second, swap the third and the fourth should be an extended partition including all extra data partitions and /home.

[EDIT]
A separate /home partition is not required, it can be part of / (root), but I'd highly recommend having one as it eases reinstalls.

For further reference, a decent read might be [http://psychocats.net/ubuntu/dualboot]("http://psychocats.net/ubuntu/dualboot")
[/EDIT]

---

### Post by Cl0ud9 on 2008-10-24
What does the swap partition do?
[Look at this thread.]("http://ubuntuforums.org/showthread.php?t=185312")

You do need a swap partition and a root partition for Ubuntu. The swap partition should probably be double the size of your ram.

For partitioning, the program GParted is on the live cd. You can find it under the system menu listed as Partition Editor.

---

### Post by Kellemora on 2008-10-24
Hi Corey

I'm a noob too, so my response may be wrong.
If you let Ubuntu set itself up it might make the Swap partition automatically, but then that might only be if you give it the whole disk, not just a partition.  In your case, you would want to only give it a partition.
So, when you start the Ubuntu install it should let you select to open a program called GParted which will help you with the partitions.  You shouldn't have to do much other than set the ROOT for the Ubuntu install and add a small /Swap partition, which is usually like double the size of your RAM unless you are over a gig, then I think you can hold the swap at a gig and never run out.
But like I said, I'm a noob too!
Although all of my machines are triple boot, I don't have Doze on any of them, so was starting with a clean hard drive each time, and Ubuntu made the necessary files it required.  Then I just shrunk the main partition down to hold 2 more OS's.

There is a disk you can download called SuperGrub that I hear works well with Vista and other Doze machines.  I would also download the stand alone GParted and make a bootable disk from it as well.  Just seems to work better.

TTUL
Gary

---

### Post by blackened on 2008-10-24
I would suggest doing the partitioning with vista's disk manager, then installing Ubuntu in unallocated space.

A decent guide is [here]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1"). Ignore page 4, it's unnecessary to initially bother with a different bootloader.

---

### Post by bjornie on 2008-10-24
I have sometimes found it useful to use a swapfile instead of a whole partition. Performence wise there is no difference if you only have one hard drive, since the drive only can read or write to the disk one at a time.

Just my $0.02 :)

---

### Post by CoreyB. on 2008-10-24
I attached my a screenshot from Vista's computer manager.  I zipped it because the horizontal size of the jpeg was too large, I hope you guys can unzip it.  I don't really use the Recovery partition.  From what I understand I can back up windows with DVDs? Is that correct, if so could someone tell me how?  I think I'm going to give Ubuntu 50 GB.

---

### Post by louieb on 2008-10-24
Can't really tell what type of partitions you have from the screen shot. (logical,extended or primary)  
Could give a better answer if you would post the partition table.
Boot the Ubuntu Live CD. 
open applications>accessories>terminal
```
sudo fdisk -l
``` lowercase L at the end.
Just cut and paste the output  in your next post,

If you would like to see graphical view you can open system>administration>partition editor.

---

### Post by CoreyB. on 2008-10-24
I don't actually have Ubuntu installed yet (waiting for 8.10 final).

---

### Post by Victormd on 2008-10-24
If you're going to do any partitioning, use the Vista disk manager to do so. Vista doesn't like Gparted, so if you use it, you might mess up your windows install. Page 2 of the guide posted by Blackened will get you on your way. For the swap, you only need 512MB, but, if you want to hibernate your laptop, it needs to be at least the same size as your RAM (I use the size of my RAM + 256MB just to be on the safe side...).

Partition everything in Vista before starting the Live CD, then use MANUAL when given the option in the partition editor portion of the install (this is a simplistic statement :))...

Post back if you need more detailed help.

---

### Post by CoreyB. on 2008-10-24
> **Victormd said:**
> If you're going to do any partitioning, use the Vista disk manager to do so. Vista doesn't like Gparted, so if you use it, you might mess up your windows install. Page 2 of the guide posted by Blackened will get you on your way. For the swap, you only need 512MB, but, if you want to hibernate your laptop, it needs to be at least the same size as your RAM (I use the size of my RAM + 256MB just to be on the safe side...).

Partition everything in Vista before starting the Live CD, then use MANUAL when given the option in the partition editor portion of the install (this is a simplistic statement :))...

Post back if you need more detailed help.

I have 3 GB RAM, so i'll do 3.25 GB for the swap.  I read that Ubuntu uses a different filesystem than Vista.  Should I just resize my Windows partition to make room for Ubuntu with Vista and leave unpartitioned space, or should I also format it with Vista?

PS: As you can see from my previously attatched image, the Recovery (D:) partiton is before the Windows (C:) partition, I don't use the Recovery partition, if I remove that partition, can I somehow slide the C: drive over, or have it consume the unpartitioned space from my Recovery partition? Thanks

---

### Post by northern lights on 2008-10-25
You should leave unallocated space.

---

### Post by CoreyB. on 2008-10-25
> **bjornie said:**
> I have sometimes found it useful to use a swapfile instead of a whole partition. Performence wise there is no difference if you only have one hard drive, since the drive only can read or write to the disk one at a time.

Just my $0.02 :)

How could I do that, that sounds like the way I want to go.  What are the bad things about it?  Is it easy to set up?

---

### Post by Duck2006 on 2008-10-25
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Victormd on 2008-10-25
> **CoreyB. said:**
> I have 3 GB RAM, so i'll do 3.25 GB for the swap.  I read that Ubuntu uses a different filesystem than Vista.  Should I just resize my Windows partition to make room for Ubuntu with Vista and leave unpartitioned space, or should I also format it with Vista?
Leave the unpartitioned space (enough for the file system and swap)

> PS: As you can see from my previously attatched image, the Recovery (D:) partiton is before the Windows (C:) partition, I don't use the Recovery partition, if I remove that partition, can I somehow slide the C: drive over, or have it consume the unpartitioned space from my Recovery partition? Thanks

Yes, you can do that, just resize the C to fill the 10GB. You should also look into a good defrag tool to move all the files to the beginning of the drive when creating the new partition/unallocated space to install ubuntu (vista partition editor doesn't do that automatically), so you can choose a larger partition size if desired (I like [Jkdefrag]("http://www.kessels.com/Jkdefrag/")).

---

### Post by CoreyB. on 2008-10-25
> **Duck2006 said:**
> [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I looked at the FAQ, I really don't still understand how to make a file instead of a partition, must be more of a newb than I thought.  Could someone put in detailed instructions how to make a swap file instead of a partition, I have no prior experience with Linux, let alone Ubuntu, and haven't installed it yet (waiting for 8.10).  Is the Swap partition made automatically when Ubuntu is installed?

---

### Post by Duck2006 on 2008-10-25
Post number 6.

[http://ubuntuforums.org/showthread.php?t=54307](http://ubuntuforums.org/showthread.php?t=54307)

---

### Post by drowner on 2008-10-25
> **CoreyB. said:**
> I looked at the FAQ, I really don't still understand how to make a file instead of a partition, must be more of a newb than I thought.  Could someone put in detailed instructions how to make a swap file instead of a partition, I have no prior experience with Linux, let alone Ubuntu, and haven't installed it yet (waiting for 8.10).  Is the Swap partition made automatically when Ubuntu is installed?

Yes, the swap partition is generally made automatically, unless you choose a manual install.


If you wish to Dual-boot vista and Ubuntu, your first two steps will be to:

1. Back up any important information
2. Use the partitioning utility in Vista to shrink the Vista partition, and leave as much space as you like for the Ubuntu installation.

---

### Post by Duck2006 on 2008-10-25
> **drowner said:**
> Yes, the swap partition is generally made automatically, unless you choose a manual install.


If you wish to Dual-boot vista and Ubuntu, your first two steps will be to:

1. Back up any important information
2. Use the partitioning utility in Vista to shrink the Vista partition, and leave as much space as you like for the Ubuntu installation.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Helios1276 on 2008-10-25
> **drowner said:**
> Yes, the swap partition is generally made automatically, unless you choose a manual install.


If you wish to Dual-boot vista and Ubuntu, your first two steps will be to:

1. Back up any important information
2. Use the partitioning utility in Vista to shrink the Vista partition, and leave as much space as you like for the Ubuntu installation.

The Vista partitioner is limited unless you turn off Pagefileing and System restore points before you try to shrink the Vista Partition.

---

### Post by drowner on 2008-10-25
> **Helios1276 said:**
> The Vista partitioner is limited unless you turn off Pagefileing and System restore points before you try to shrink the Vista Partition.

Oh ok. Is this why sometimes Vista may be taking up only 20gb of a 200gb disk, but won't let you free up more than 60gb of space, or similar?

---

### Post by Helios1276 on 2008-10-25
> **drowner said:**
> Oh ok. Is this why sometimes Vista may be taking up only 20gb of a 200gb disk, but won't let you free up more than 60gb of space, or similar?

Exactly, it limits the amount of space you can free up. Personally, I just turned off the relevant stuff until I had carved up the drive how I wanted it and then turned everything back on again. You would want to back stuff up before though.

---

### Post by CoreyB. on 2008-10-26
> **Duck2006 said:**
> Post number 6.

[http://ubuntuforums.org/showthread.php?t=54307](http://ubuntuforums.org/showthread.php?t=54307)

Ok the code says:

sudo dd if=/dev/zero of=/swapfile bs=1024 count=$((16*65536))
sudo mkswap /swapfile
sudo swapon /swapfile

I have 3 GB RAM.  I read on the Swapfile FAQ to make the swap twice as big as the RAM you have.  What should I put in place of the 1024 and the 16*65536?

---

### Post by CoreyB. on 2008-10-26
Here is a quote from the Swap FAQ:

Hibernation needs swap 

The hibernation feature (suspend-to-disk) writes out the contents of the memory to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size. The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition, and can not use a swap file on an active file system.

Does that mean if i use a swap file, I won't be able to use hibernation?  Does hibernation require a swap partition?

---

### Post by Xiong Chiamiov on 2008-10-26
> **louieb said:**
> Can't really tell what type of partitions you have from the screen shot. (logical,extended or primary)  
Could give a better answer if you would post the partition table.
Boot the Ubuntu Live CD. 
open applications>accessories>terminal
```
sudo fdisk -l
``` lowercase L at the end.
Just cut and paste the output  in your next post,

If you would like to see graphical view you can open system>administration>partition editor.

Of note is that this would still be useful, and does not require you to install Ubuntu, just to boot it off of the CD.

---

### Post by CoreyB. on 2008-10-26
> **Xiong Chiamiov said:**
> Of note is that this would still be useful, and does not require you to install Ubuntu, just to boot it off of the CD.

I don't have the Live CD yet, I am waiting for 8.10, is their a way I could get the table in Vista?

---

### Post by northern lights on 2008-10-26
> **CoreyB. said:**
> Does that mean if i use a swap file, I won't be able to use hibernation?  Does hibernation require a swap partition?
While I really don't see why you wouldn't want to use a partition, hibernation would work with a file also.

---

### Post by CoreyB. on 2008-10-26
> **northern lights said:**
> While I really don't see why you wouldn't want to use a partition, hibernation would work with a file also.

On my laptop there is the Windows partition, the Dell Media Center partition, a Recovery Partition, and a 71 MB parition that has no name or letter and says 'Healthy EISA Configuration'.  These are all listed as primary partitions, it doesn't give me an option to delete the last one I mentioned anyway.  If I have to I will delete the Recovery Partition since I don't use it anyway.  I would have trouble using a Swap partition because I don't know if I would be able to have that many partitions.

If someone would tell me how to list a parition table using Vista, I gladly would.  Also in a previous post, I'm still not sure what to put the numbers for for the code to make the swap file.  Any advice would be greatly appreciated.

---

### Post by louieb on 2008-10-26
Don't know any way of getting the the type of information I need out of Vista.  Unless you want to buy Partition Magic or Acronis® Disk Director 

But for the moment lets assume you have 4 primary partitions. The image you attached says 3 are primary partitions. and I am assuming the eisa partition is a hidden primary partition. 

Delete one and in its place create an extended partition. On a SATA drive an extended partition can be sliced up into as many as 15 logical partitions. (If the drive is IDE you have even more, the 15 logical is a SATA limit).  Unlike some other operating systems Linux installs and runs in a logical partition just as easy as a primary partition install. 

The real problem is one of space. Making enough contiguous room available.

---

