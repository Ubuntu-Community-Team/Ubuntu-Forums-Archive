---
title: "Partitioning the hared drive"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by tagreen4 on 2012-04-19
Hi 
I'm considering installing Ubuntu alongside windows 7 and what I would like to do is partition my hard drive into 3 parts, one for my windows OS, one for my Ubuntu OS, and one for my files (It is currently divided into two OS and files).  I believe my friend partitioned my computer for me originally (unless it came partitioned like that) so I have not done anything like that before.  My question is:  Will the Ubuntu installer guide me through making three such partitions or is that more advanced than the basic partitioning the installer does?  Also is that even the recommended way to partition my hard drive?  Lastly some details on how much room I should allow for on each partition would be helpful (It looks like my current partition is 140 GB for each of the two partitions).
Thank you in advance

---

### Post by jerome1232 on 2012-04-19
When you run the installer, it should offer to install alongside Windows, if you select that option it will automatically try to shrink the Windows partition to half it's size and create a new / partition for itself and a swap partition (kind of like a pagefile in Windows). Since you already have a separate partition for files it sounds like this is what you would want yes?

---

### Post by audiomick on 2012-04-19
Jerome is right in principle, but I would suggest looking into the whole business a bit further.

Read through this lot:
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions")

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

I would suggest looking at your partition with a partitioning tool like gparted to see what is really there now. You may find that your Win7 install has already used up the 4 possible primary partitions, in which case you may have to choose to delete one of them, maybe the recovery partition or the manufacturer's tools, or move the files out of your data partition onto an external medium and delete that. The reason for deleting would be to then create an extended partition that can have a large number of logical partitions inside it. Your Linux system partition can be a logical partition.

I always install with a separate /home partition. I find this helps when I have to or want to re-install. I can just re-use the /home partition without formatting it, and all my config files and data is retained.

---

### Post by jerome1232 on 2012-04-19
> **audiomick said:**
> 
I would suggest looking at your partition with a partitioning tool like gparted to see what is really there now. 

Based on the OP's description at most the OP has 3 partitions, the hidden boot partition Win7 likes to make, the Windows System partition, and his data partition. Which leaves room for one extended primary partition and lots and lots of logical partitions inside it.

For a new user I wouldn't recommend a separate /home, many times not enough space is allocated to one partition or the other since new users don't have a good feel for their usage patterns and what is right for them, and either space goes to waste or one partition fills up quickly. Particularly since the op intends to keep personal files on a totally separate data partition anyways.

This is just in my personal opinion and suggestions for what I perceive as a painless method to get rolling. 

One thing I did neglect to mention is although gparted (The tool Ubuntu use's to repartition) works great with ntfs in my experience, it is best to use Windows tools to mess with Windows file-systems. It would be wise to actually temporarily put your page file on the data partition, defrag your system partition, shrink it down to the desired size, and then install Ubuntu, it should stick itself nicely in the unallocated space you created. This would also give you a chance to, as audiomick suggested, give your partition scheme a good look over.

The Windows partition manager can be found under administration tools-computer management-storage-disk management if I recall correctly.

You could even slap a screen shot up of your partitions if you wanted more opinions.

---

### Post by dzponce11 on 2012-04-19
If you want to play it safe, in Windows, download Wubi(Windows Ubuntu Installer) and it can make a virtual partition that won't affect your existing hard drive. It can also install Kubuntu, Xubuntu, and Mythbuntu.

Wubi Link: [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

### Post by audiomick on 2012-04-19
Yes, it is a good plan to use the Windows tool to re-size a windows partition. Gparted will probably do it, but why not use the tool that the manufacturer supplies?.

Remove all unnecessary, old, redundant, embarrassing, whatever other rubbish files. Defrag the drive. Twice is good. Resize the partition to what you want to have. Restart Windows a couple of times and let it run it's disk repair application if it wants to. When it is all happy, you can go ahead with Gparted and/or the Linux install.


There are a lot of machines around, particularly with Win7 installed, that have 4 primaries on them from scratch. One could almost suspect a deliberate attempt to make it difficult to put another system on there...
Have a look at it with gparted, and yes, post a screenshot of it up here and see what people say about it.

Regarding partition sizes: I think Win7 is fairly happy with something between 30 and 40 GB, if there is a separate Data Partition.
For the Linux / partition, the system, around 15 GB should do.
The /home partition is debatable. If you want to let the system do with it as it will, it should be as big as you can let it be, as the the system throws every thing in there by default. If you are going to be using a data partition; saving manually to somewhere other than /home, changing default save paths or using sym links, then you need to find a suitable compromise between /home and your data partition. I've seen people claim they get by with a /home as small as 4 GB, but I think that is a bit extreme.

Swap need to be a bit bigger than your RAM if you want the suspend function to work properly. Otherwise, if you have a half way modern amount of RAM and don't spend your day doing video editing or such like, you can probably leave it at a GB or so.

---

### Post by tagreen4 on 2012-04-19
Thanks guys for all the helpful information.  I'm still sorting my way through it all but I should have more time to take a closer look at your posts this weekend.  I'm now actually considering reinstalling windows first just to clean out my computer completely (and since I graduate I don't need most of the files anymore anyways) and then taking a look at the partition with gparted and working from there.  If there is a more standard/recommended method of installing Ubuntu on a fresh machine let me know, otherwise I'll probably just see what gparted tells me and work from there.  Thanks again.

---

### Post by audiomick on 2012-04-19
> **tagreen4 said:**
> If there is a more standard/recommended method of installing Ubuntu on a fresh machine let me know,...

I guess the most "standard" way is just to let the installer do it's business and don't think about it. What has been posted here is pretty much from the the first step past that onwards, i.e. standard install but thinking about what is happening yourself instead of just letting the thing go through automatically. 

Have a read of that information and see how you go. It isn't that hard to understand, and it helps you understand what is happening in your computer. Have fun with it. ;)

---

### Post by tmaranets on 2012-04-19
If you don't want anything to be affected, try a Wubi Ubuntu installation. It gives you another partition.

---

### Post by dzponce11 on 2012-04-19
> **tmaranets said:**
> If you don't want anything to be affected, try a Wubi Ubuntu installation. It gives you another partition.
Copycat.

---

### Post by tagreen4 on 2012-04-22
I just wanted to thank everybody again for all the help.  I have determined that with finals coming up it is best that I postpone reinstalling win7 and installing Ubuntu for a month, because then I will have more time and I really won't need any of the files on my computer after graduation.  You have all been very helpful so far and once I have Ubuntu up and running I may need to ask for your assistance again.  Thanks a ton.

---

### Post by Bartender on 2012-04-22
If you're going to wipe and reinstall, do yourself a huge favor.  Use a partitioning tool like [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") to create a primary ntfs partition for Windows BEFORE you install Windows.

Here are the basic steps.  After you make sure that you created your Windows recovery discs first of course:

1) Download the latest stable GParted LiveCD (GPLCD) package and burn to a CD.  You can do this in Brasero, or use an app like ImgBurn in Windows.  Creating a bootable CD from the .iso is not the same as  burning a copy of the download!

2) Boot from the GPLCD and wipe all partitions.  Decide how much room you want to give Windows.  Create a New Partition, format it as primary ntfs.

3) The simplest thing to do with the rest of the HDD - the part that will receive Ubuntu - is to create one primary ext4 partition.  You can get fancy if you want and create primary and extended partitions with GPLCD.  I always set up partitions for /, swap, and /home with GPLCD.

4) Get out of GPLCD, boot from your Windows disc.  It'll only see the ntfs partition.  Install.

5) Check to make sure Windows is working, then install Linux to the appropriate partition or partitions.

This is so much easier and more reliable than installing Windows to the whole drive, then hoping that it'll give up space without issues.

---

