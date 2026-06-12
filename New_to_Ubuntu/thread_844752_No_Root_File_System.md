---
title: "No Root File System"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by DDurcsak on 2008-06-29
Screen 4 of 7 of the Ubunto 8.04 installation shows me my available HDs.

I've configured my primary C: Drive with a partition to all for the Ubunto installation.  The NTFS side has WIN XP running on it and the FAT32 is open for Ubunto...at least that what I thought.

The screen reads:

/dev/sda
     /dev/sda1  NTFS
     **/dev/sda2  FAT 32**

I have a second data drive that is also listed and partitioned but for expediency I wont go into those details.

The problem is that the when I choose /sda2, the install drive, all I get back is, " No root file system is defined.  Please correct this from the partition menu"...ANy ideas as to what this tell me?....Should I be choosing /dev/sda

Thank you

---

### Post by TransitMan on 2008-06-29
You need to make the /dev/sda2 the / which is the root filing system. 
Then it needs to be formatted in either ext2 or ext3. You will lose the FAT 32 partition for the Ubuntu partition.
Also, you don't indicate on the size of the FAT 32 partiton.

---

### Post by neurostu on 2008-06-29
You need to format one of the drives to EXT3 and then set the mount point as "/" then it will install.

---

### Post by bluepowder7 on 2008-06-29
i'm not sure what screen 4 is like, but you should highlight the partition you want to use, click EDIT PARTITION, and edit the values.  tell it to format that partition, and tell it to use it for / [root].  and tell it to use ext2, ext3, jfs, or xfs.  i personally use jfs, but plan on moving to xfs on the server (less wasted space compared to ext2/3)

---

### Post by king leoric on 2008-06-29
It means you haven't selected a root partition drive for ubuntu installation. Linux installation needs atleast two independent partions.
"/" partition and swap. 

You could configure /dev/sda as Extended partition and inside, you can now make logical partions for root and swap and also home.

Hope it helps:)

By the way, I used reiserfs:-)

---

### Post by DDurcsak on 2008-06-29
Thank you...Size of the /sda2 is 140MB..figured that this was large enough to handle the modest use i'll give it

---

### Post by neurostu on 2008-06-29
140MB????  That is WAY TO SMALL! the root filesystem is the ROOT of the installation. The OS and your personal files are all stored under that. 

I would HIGHLY recommend that you have atleast 10 GB under your root file system.

I would be surprised if you could even get ubuntu to install with a root directory of only 140MB. 

Actually [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)  The system reqs are 4gb minimum!

---

### Post by king leoric on 2008-06-29
> **DDurcsak said:**
> Thank you...Size of the /sda2 is 140MB..figured that this was large enough to handle the modest use i'll give it

Dude, your wasting you 140 mb. You can add for ubuntu partition.

How big is you HD anyway? better use 5gb or more for you root partion. but better more space for ubuntu.

---

### Post by bluepowder7 on 2008-06-29
i'm seriously hoping he mistyped and meant 140GB.  it's not the 90's anymore, anyhoo...

---

### Post by DDurcsak on 2008-06-30
WOW...this is a tough group.   You have one bottle of Scotch and type a few things wrong and everyone jumps on you...

---

### Post by philinux on 2008-06-30
I've had Ubuntu Hardy running a while and installed loads of stuff. My root is now 5 gig. So you could say just allocate 10 gig for the whole system.

---

### Post by bluepowder7 on 2008-06-30
i'm mostly doing fine with an 8gig partition for / [root], which also has /home on it.  this covers all my software installs and temporary files during video encoding, but i should note that i have my actual files (docs, pics, vids, etc) stored on a completely separate file-n-print-server machine with around 1.1TB of mass storage - the benefits of which are way more space to begin with, the ability to easily "grow" it, and total separation from my OS which i have a tendency to bork.

if you're keeping your pics and docs in your /home directory, then you should make the partition bigger by whatever you'll need.

---

