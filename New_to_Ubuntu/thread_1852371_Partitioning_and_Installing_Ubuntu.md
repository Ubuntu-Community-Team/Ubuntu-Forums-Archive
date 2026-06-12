---
title: "Partitioning and Installing Ubuntu"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by LittleFatMan on 2011-09-30
Hello, 

I am a newbie and have some newbie questions. Please excuse my newbieness. Thanks.

I am currently running Windows 7 and am trying to install Ubuntu 11.04.

I have created a USB stick to install Ubuntu. I have also shrunk and partitioned a new drive using the Windows 7 software. I wish to install Ubuntu to this new partition.

The problem I am having is that when I go through the Ubuntu installation process, I cannot see the new drive that I have created. In fact, none of the regular drives with their normal letter assignment are shown, rather.

So, where do I go from here? From what I have read, I know that I can use the Ubuntu installation software to prepare a partition to install to, but I don't know how to do that. I would prefer to install Ubuntu on the new partition I have already created.

Thanks for your time.

---

### Post by LowSky on 2011-09-30
Only Windows uses a Letter system for labeling drive mount points.

Linux uses mount points like this: /dev/sda which would translate to C: on a Windows Machine. Hope that makes sense.

---

### Post by Elfy on 2011-09-30
> I wish to install Ubuntu to this new partition.Did windows allow you to format this partition to a suitable format - that is not ntfs?

Boot the liveusb - run a terminal (Ctrl+Alt+T) paste in this command run it and post the results here.

sudo fdisk -l

---

### Post by ksrsubramanian on 2011-09-30
Boot from your USB
Click "Try Ubuntu"
And in the desktop that appears
Go to 
System/Preferences/ Gparted

which can give you the clear picture of what are all the partition your whole Hard disk is having


You can also resize,edit,delete any partition with Gparted


Good luck

---

### Post by LittleFatMan on 2011-09-30
@Lowsky - Yes, that is what I saw instead of the windows drive letters. I tried to reconcile the two by having a look at Windows Explorer and writing down the size of each drive. Then, I thought I could run the Ubuntu setup, see which drive letter is which by comparing the sizes and choose to install to the partition I had created. Except...the sizes were different! Stumped newbie!

---

### Post by LittleFatMan on 2011-09-30
@forestpisie - Thanks, I will do that in about 10 minutes when I arrive home. 

What exactly do I type?

"sudo fdisk -l"

or

"sudo fdisk"

?

Thanks

---

### Post by Quackers on 2011-09-30
If all your current partitions are NTFS Ubuntu will not be installable. It will consider the disc to be full. Try deleting a partition and leaving the free space, which Ubuntu will then be able to use.

---

### Post by Elfy on 2011-09-30
> **LittleFatMan said:**
> @forestpisie - Thanks, I will do that in about 10 minutes when I arrive home. 

What exactly do I type?

"sudo fdisk -l"

or

"sudo fdisk"

?

Thanks

> **Quackers said:**
> If all your current partitions are NTFS Ubuntu will not be installable. It will consider the disc to be full. Try deleting a partition and leaving the free space, which Ubuntu will then be able to use.

The whole thing, that said if all you get are ntfs - which I suspect you will, then you're going to need to do as quackers says.

Further - if after possibly deleting these partitions you created you still have 4 or more partitions then you're going to still be unable to install - come back with the details.

If you have dynamic disks in windows then this could be a problem.

I would also do the partition delete in windows - that tool should tell you if they are dynamic disks - I believe anyway.

---

### Post by LittleFatMan on 2011-09-30
> **forestpiskie said:**
> Did windows allow you to format this partition to a suitable format - that is not ntfs?

Boot the liveusb - run a terminal (Ctrl+Alt+T) paste in this command run it and post the results here.

sudo fdisk -l


arggh! I am trying to do this, to run sudo fdisk and post the results...but I can't even get firefox running! Not a very nice introduction to the world of Ubuntu!

I have previously ran firefox off the USB that I created. Now, I click on Firefox, a tab on the toolbar says "Starting Firefox" for about 10 seconds before disappearing and not opening a firefox window!

Why is this happening and how do I correct it? Are these types of problems common with Ubuntu, the USB live version, or does my luck simply suck?

Thanks to all for the help, I appreciate it, even if I am frustrated!

---

### Post by Quackers on 2011-09-30
It may be a problem with the downloaded iso file or the burned disc. It is not normal for firefox to fail to start.
Open up a terminal and copy/paste forestpiskie's command (without quotes) and hit enter.
Please copy paste the output from that into your next post.

---

### Post by LittleFatMan on 2011-09-30
> **Quackers said:**
> It may be a problem with the downloaded iso file or the burned disc. It is not normal for firefox to fail to start.
Open up a terminal and copy/paste forestpiskie's command (without quotes) and hit enter.
Please copy paste the output from that into your next post.

I can't copy/paste the output into my next post because I can't open up a Firefox window! (I am using my second PC to write this)

Do you think I should download another ISO and make another USB Live?

---

### Post by anieruddha on 2011-09-30
I guess when you install, there is option like 'use existing free space', If this option is available, then delete one partition from windows (usually 20 GB or more). And at the time of installing select option 'use existing free space'

---

### Post by Elfy on 2011-09-30
> **LittleFatMan said:**
> I can't copy/paste the output into my next post because I can't open up a Firefox window! (I am using my second PC to write this)

Do you think I should download another ISO and make another USB Live?

If you're getting issues I Would certainly check the existing iso you burnt from
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

