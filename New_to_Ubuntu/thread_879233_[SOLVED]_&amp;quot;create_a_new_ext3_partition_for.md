---
title: "[SOLVED] &amp;quot;create a new ext3 partition for your root&amp;quot; &amp;lt;-- what?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by shippo752 on 2008-08-03
Ok, so I used [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) as a guide to installing Linux for my macbook, but I got stuck at step 6 ("create a new ext3 partition for your root" ) 

I'm kind of scared to touch any of the partitions, since I'm not sure what's a root :P

it says /dev/stda under device, and underneath that it lists free space, /dev/sda1 fat 32, /dev/sda2 hfs+/ and free space

last free space has 134 MB, while the first has 0.

---

### Post by Paqman on 2008-08-03
Ext3 is just the file system that Ubuntu uses. By way of comparison, Windows uses FAT32 or NTFS and OS X uses HFS.

"Root" just means the start of the Ubuntu file structure, you'll also see it written as /

It's called root because it's the base of the directory tree. For example, my user files are located in /home/paqman. The directory (or folder) "paqman" is inside directory "home", which is inside /.

To install Ubuntu you need to create a new partition on your drive, format it as Ext3, and tell the system to put the root there. That's what "create a new ext3 partition for your root" means.

---

### Post by mevets on 2008-08-03
It seems like you didnt clear space for ubuntu or tried unsuccessfully. You could downsize your hfs+ (sda2) partition so your last free space would be large enough to fit ubuntu on there. 10gb is a good number. Format the last free space as ext3 and set it to mount as "/" or root. This needs to be done because ubuntu needs to know where to put all the files.

---

### Post by shippo752 on 2008-08-03
So do I just select the "free space" partition and make that the new partition, and mount it on "/"? 

Or do I select /dev/sda and make that the partition? 

I have a gut feeling not to touch the hfs :P

---

### Post by shippo752 on 2008-08-03
Ohhhh, okay, thanks mevets :D 
I think I get it now

---

### Post by shippo752 on 2008-08-03
Oh but wait, so I resize the hfs to say 109690 MB from 119690 (I'm assuming that that's 10 GB) and then resize the free space to 10 GB? 

Will that screw up the files on my Mac OS?

---

### Post by Paqman on 2008-08-03
As long as the HFS partition still has plenty of unused space it'll be fine. 

That page seems to suggest that Bootcamp can't handle a drive with more than two partitions. What's on the FAT32 partition? Can you do without it?

---

### Post by shippo752 on 2008-08-03
I was told that the FAT was like the table of contents of whatever's on the hfs partition, so I probably shouldn't touch that one.

---

### Post by Paqman on 2008-08-03
> **shippo752 said:**
> I was told that the FAT was like the table of contents of whatever's on the hfs partition, so I probably shouldn't touch that one.

Without knowing more about Macs than I do, I can't say that's wrong, but it sounds a little odd. How big is the partition, and how how full is it?

FAT32 is just an old file system that's still used sometimes because everything can read it. USB sticks are all FAT32, for example.

---

### Post by SunnyRabbiera on 2008-08-03
Actually your partitioning should have at least three partitions, one your HFS partition, one your main partition, and one linux swap partition.
Its a good thing that HFS is a flexible filesystem, nothing like NTFS but be careful none the less.

---

### Post by shippo752 on 2008-08-03
Okay, so when I tried resizing the hfs partition to leave 10 GB for the free space partition, I got this error message saying "support for checking hfs+ file systems is not implemented yet"

---

### Post by Paqman on 2008-08-03
> **SunnyRabbiera said:**
> Actually your partitioning should have at least three partitions, one your HFS partition, one your main partition, and one linux swap partition.


I thought the same, but the instructions for Mac don't say anything about a swap, and specifically says that Bootcamp can't handle more than two partitions. Presumably you're limited to using a swapfile. I've never tried that, but I don't believe it's a big deal.

---

### Post by shippo752 on 2008-08-03
I'm not using BootCamp though :/

---

### Post by Paqman on 2008-08-03
> **shippo752 said:**
> I'm not using BootCamp though :/#

Ah well, just ignore me and carry on then.

Is that error message preventing you from resizing your HFS partition, or is it just a warning? I suspect it's the latter. You have backed up your OS X installation though, right?

---

### Post by shippo752 on 2008-08-03
Is there any way to resize a partition without having to use Boot Camp? 

By the way, the FAT32 partition is 209 MB and is completely filled.

---

### Post by shippo752 on 2008-08-03
The message is preventing me from resizing. 
When you say backing up the OSX, do you mean do I have the OS disk? Yes I do, but I've had to use the restore OS thing before, so I dunno if I can use the disk .

---

