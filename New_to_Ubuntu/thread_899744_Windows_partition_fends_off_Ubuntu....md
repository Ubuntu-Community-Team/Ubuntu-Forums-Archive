---
title: "Windows partition fends off Ubuntu..."
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Myros00 on 2008-08-24
Okay, awesome, title, you gotta admit that much :P

Anyway, yes, another noob here (hides behind his desktop). This is a rather strange problem, I've tried running a search, but I didn't quite find a problem similar to mine, so here it goes...

I run Ubuntu liveCD, I decided to install, now here's the tricky part, during the partition page, I was presented with my External Western Digital MyBook external drive (1 TB), that is, when the first option is selected on that page. :mad: Seeing that as strange, I rebooted to Windows, and since my External HD is FAT32, I decided that was the issue. I changed the FileSystem of my windows partition to FAT32, rebooted to Ubuntu Live, and this time, I unplugged my external HD.

However, this time around, I was given the option to partition my E DRIVE! Okay, seriously, this is simply infuriating. I selected the manual partitioning option, and I found that by clicking on Drives E and J, which are partitions on the same HDD, I could set a new size for the partition, however, I'm not allowed to do so with the Windows partiton (which is Drive C!)

A picture is worth a thousand words, so here it goes:
[http://img185.imageshack.us/my.php?image=screenshotpy7.png](http://img185.imageshack.us/my.php?image=screenshotpy7.png)
Basically, when clicking on the C drive, all I get in the edit partition option is: "Use as", "Format the partition", "Mount Point". "New partition size" isn't available.

I also have a few questions regarding a possible workaround for this issue (if it cannot be solved, I guess?). But due to being verbose as it is, I'll stop now :P

---

### Post by rossjman1 on 2008-08-24
I don't understand, can you please explain it without using the terms "C:\ drive". Can't you just install in the free space?

---

### Post by halitech on 2008-08-24
are you looking to install to your entire hard drive?

---

### Post by coffeecat on 2008-08-24
> **Myros00 said:**
> I changed the FileSystem of my windows partition to FAT32

How did you do that? I did not think it was possible to change a Windows partition from NTFS to FAT32 without reformatting it. Whatever - perhaps something went wrong when you did this. If you look at your screenshot, the Used column is showing (unknown) for /dev/sda1 (which I presume is your C: drive - correct?). The partitioner should have no problem showing how much is used in a FAT32 partition which makes me suspect something is not right with that partition, and that is perhaps why you cannot resize it - the partitioner is not reading it properly.

Two suggestions:

1 Boot into the live CD and instead of opening the installer, go to System > Administration > Partition Editor. That's a stand-alone partitioner and fairly easy to use. See what you can manage with that, although I suspect you'll get the same issue as the underlying code will be the same as with the partitioner in the installer.

2 See if you can convert your Windows partition back to NTFS. I believe this is possible in Windows. Then run a chkdsk in Windows. Then defragment the C: drive. Then boot into Windows twice. This should clean up your C: drive. Now try the Ubuntu partitioner.

---

### Post by zamadatix on 2008-08-24
i got lost in what oyur problem was can you give a simplified version/ and there is 3rd party software for doing a ntfs to fat32 though it doesnt always work and the best way is just torenstall as fat32 really

---

### Post by Myros00 on 2008-08-24
@Rossjman: Sorry about the confusion, but as previously stated, I'm a Linux newb :p I think the screenshot below will help clear things up.

@Halitech: No, dual-boot is the direction I'm trying to go. :-)

To be very clear and blunt, my issue is that the Ubuntu installation does NOT detect my Windows drive as a primary option. It either detect my E drive (which is a partition) OR my 1 TB external HDD.

@Coffecat: Thanks for your reply :-)
I ran chkdsk /f two times so far, and Disk Defragmented so many times, to the point that the Defragmenting takes less than 30 seconds now (I'm guessing nothing more can be done with it). However, I do have some files hanging a bit beyond the middle of the disk (according to the defragmenter graphs) So I'm really worried about screwing this up...

Is there any chance of installing Linux in /dev/sda2's unallocated space, and making it dual boot with XP?

Here is a picture of the partitioner in Linux, this may help clear things up a bit :-)

---

### Post by zamadatix on 2008-08-24
during install you should just be able to go to manual and click that partition and install. as long as you dont plan on going more than halfway down on windows size you should be fine but if you are try a different defragementing program (like freeware defraggler).

---

### Post by estyles on 2008-08-24
Umm... I think you're saying that you want to install Linux on the *same* partition as Windows?  You can't do that.  Or, you can, but you'll delete Windows.  I'm still confused when you say C: drive and E: drive whether you're talking about the partitions or the hard drives.

On your screenshot, you've got a ~65 GB unallocated space - you should use part of that.

---

### Post by zamadatix on 2008-08-24
[QUOTE=]Is there any chance of installing Linux in /dev/sda2's unallocated space, and making it dual boot with XP?[/QUOTE]


i figured from this he wnated to instlal on unformatted space but i also thought he said that it owuldnt detect his windows partition or hsi hdd... but then goes on about rive letters which is confuseing...

---

### Post by jerome1232 on 2008-08-24
> **Myros00 said:**
> 
Is there any chance of installing Linux in /dev/sda2's unallocated space, and making it dual boot with XP?

You could turn the unallocated space on sda, into sda7 ext3 sda8 swap and install ubuntu to sda7.

---

### Post by zamadatix on 2008-08-24
since he only is using 1 primary partition and a logical wouldnt it make sense jsut to shrink the ntfs and use the unallocated as a primary? and i didnt know you couldnt install something onto unallocated space when the logical partition is a differnt format. i always though when it was unallocated you could put anything on it regardless of the logical partitions format... good thing i didnt try to install another linux on mine.

---

### Post by SnappyU on 2008-08-24
One thing I don't quite understand.  You mentioned that you changed your NTFS partitions to FAT32 format, but the screenshots all show your windows partn as NTFS. Ideas? :)

---

### Post by zamadatix on 2008-08-24
maybe it was said backwards? (the person seems to have taken a break...)

---

### Post by Myros00 on 2008-08-25
Hello, guys.,

I was asleep, sorry. It was approximately 2am when I posted the thread. :p

@Snappyu: If you look at the first screenshot I posted, it does list it as FAT32. I used PartitionMagic to convert the Primary partition. But, after Coffecat's post, I proceeded to switch it back to NTFS.

@Jerome/Estyles: yep, that's exactly what I was asking, but would Ubuntu dual-boot with XP then? And Estyles, that's exactly why I hesitated with the installation. When I picked to resize the Windows partition, it had a box which was apparently selected in the column "Format", so that sort of scared me off :p

@Zamadatix: 
> during install you should just be able to go to manual and click that partition and install. as long as you dont plan on going more than halfway down on windows size you should be fine

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

As stated in my first post, some files still remain a little after "half" of the partition. Here's a picture from the windows Defragmenter to explain it:
[http://img.photobucket.com/albums/v201/Myros/Defrag.jpg](http://img.photobucket.com/albums/v201/Myros/Defrag.jpg)

Not to mention that with PartitionMagic, it states there's a 1024 cylindrical limit in the 'beginning' of the primary partition, anything existing beyond that would not be 'bootable'.

P.S: When I said my HDD wasn't detected by default, I meant the Guided Resize option during installation wouldn't show my Primary Partiton (the partition with Windows XP installed). That's all. Sorry for the confusion :p

---

### Post by sdowney717 on 2008-08-25
you have unused unallocated space on sda1 where windows is sitting. Just install ubuntu into that space.

---

### Post by Myros00 on 2008-08-25
Umm, what about the files at the end of the disk? I might seperate them, right? (according to the link and screenshot on my previous post)

---

### Post by estyles on 2008-08-25
You can still dual-boot with the OS's on separate partitions, in fact, that's the way you should do it.  There's some way (WUBI) of installing Linux within Windows, but I wouldn't bother with that.  Take the unallocated space and make 2 new partitions.  One should be ~2GB and format as Swap, the other should be at least 10GB, preferrably the rest of the drive if you don't want a separate /home partition, and format it as ext3.  Use the ext3 partition as /

---

### Post by eapache on 2008-08-25
> **Myros00 said:**
> Umm, what about the files at the end of the disk? I might seperate them, right? (according to the link and screenshot on my previous post)

Theoretically the resize tool will move files around as necessary, and won't let you shrink a partition to less than it's used space. In theory. Most of the time that holds true, but manipulating partitions is always a bit touchy.

I would ignore the Windows partition completely, and use the free space that appears directly below /dev/sda6 (in both screenshots). Create a small swap partition (format it as linux-swap) equal to or greater than the amount of ram you have, and format the rest as ext3. Then set the mount point of the ext3 partition as '/'.

---

### Post by Myros00 on 2008-08-25
Thank you VERY much for the reply, estyles and espache!

Thats exactly what i was planning to do, but I was afraid that I wouldnt be able to dual-boot :D

Thank you VERY much, again!

At the moment, I have to go and play some football with friends. By tomorrow, I should report back to this thread and let you know if everything's fine :-)

---

### Post by Myros00 on 2008-08-26
Hey guys.

Last Qs (which should be easy to answer :p), I read that the /home partition's purpose is to store all your settings+preferences (Something like the My documents folder in Windows). If a separate Home partition is created, how much do you recommend its size to be?

The Ubuntu partition (or rather, /root) can be set as 'Logical' for the dual boot scenario? And is a /boot partition necessary (as primary or logical?)

Thanks!

---

### Post by shane19174 on 2008-08-26
About a separate home partition: it depends what you want to do with it. I have a dual boot with Vista, and I share an NTFS partition between the two operating systems where I store all my docs, music, etc. So my home partition doesn't have to be very big. I made mine 3GB, which is big enough for my purposes. If you're not going to share a partition with windows for "my documents" type stuff, though, you should make your home partition as big as you can (again, depending on whether you want to store big stuff like videos, music, etc there).

I don't have a separate /boot partition, but I think you should be able to find a list of advantages easily enough by searching the forums.

Hope this helps,
Shane

---

### Post by halitech on 2008-08-26
> **Myros00 said:**
>  And is a /boot partition necessary (as primary or logical?)

Thanks!

It's not necessary in alot of cases although I had to use one because my motherboard is funky and if I didn't have a 200meg boot partition created as the first partition I got grub errors. Installed with a 200meg /boot and everything works fine

---

### Post by eapache on 2008-08-27
You don't really need separate partitions at all: it is perfectly possible to run with one big / partition. If you aren't sure yet how much you will be storing where, this is by far the easiest setup.

Having a seperate /home or /boot is probably more hassle than you need right now.

As far as I know, there are no restrictions on logical partitions. Grub should handle them just like any others.

---

### Post by Myros00 on 2008-08-30
Hey guys!

Whew, was quite busy the last couple of days >_> Sorry for my absence and lack of replies.

I booted the LiveCD again today, and just as I was about to create the partitions using GParted, I received an error.. Here is what the report has to say:

"GParted 0.3.5

Libparted 1.7.1

Create Logical Partition #1 (ext3, 10.25 GiB) on /dev/sda  00:00    ( ERROR )
     	
create empty partition  00:00    ( ERROR )
libparted messages    ( INFO )
     	
Unable to satisfy all constraints on the partition.

========================================

Create Logical Partition #2 (ext3, 24.41 GiB) on /dev/sda

========================================

Create Logical Partition #3 (linux-swap, 3.42 GiB) on /dev/sda

========================================"

I dont understand what went wrong. All paritions were selected as Logical, with the "Round to cylinders" box unticked (due to that BIOS limitation of only 1024 MB limit).

Any idea on what went wrong?

---

### Post by Myros00 on 2008-08-30
Whew, finally got it up and running. I just used the partitoner provided in the installation, worked like magic :D

Umm, is a CPU usage of 38%-55% normal? It seems to be staying that way whilst using ubuntu. (Just running Firefox and Totem)

Seems like I'll be around those forums for a while :p

---

