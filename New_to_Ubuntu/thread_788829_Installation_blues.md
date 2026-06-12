---
title: "Installation blues"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by pallav on 2008-05-10
I have winxp & win 98 installed on my pc and i am planning to install kubuntu 8.04.

I want to format my hard drive first.then install xp & kubuntu.

What is the best way to do it and how shld i do it

Pallav AHooja

---

### Post by Xiong Chiamiov on 2008-05-10
You want to wipe your hard drive completely, then reinstall XP and install Kubuntu?

I'd launch the Kubuntu CD to format your hard drive, but then exit and install XP first.  We can give you more specific instructions once we determine your skill level.

---

### Post by pallav on 2008-05-10
my skill level at windows would be 7/10

---

### Post by mrdosa on 2008-05-10
Use the winxp cd to format and install windows first. Make sure you format atleast one drive properly for windows. [for ex, if its 160GB HDD you have, delete all the partitions, make a 20GB NTFS partition and install windows on it. Make another 40G NTFS partition for windows [if you need]. Forget about the rest 100g for the moment. 
After you install windows, load the kubuntu live cd. Now proceed to install. Select manual partition, and create another 20G ext3 partition with mount "/" and a swap partition of roughly your ram size.

Now create partitions out of the remaining space in FAT32 format. The reason I say FAT32 is, it can be easily shared by both winxp and ubuntu.
If you are creating say, 1 partitions of the 80 g, mount it as "/somename" 


Thats just a rough explaination. Remember to back up everything though

---

### Post by Xiong Chiamiov on 2008-05-10
Using FAT for storage space is only a good idea if he is needing to transfer files between the 2 OSs frequently.  I occasionally need to grab something from Windows on Kubuntu, and that works just fine.  I don't boot into XP very much at all, so I have no need to grab files from my linux partition, although there are ways of doing so.  I'd prefer to use a filesystem that is journalled and supports large filesizes rather than having the portability, myself.

---

### Post by shifty_powers on 2008-05-10
personally,(but them i'm very thorough with these things), when you've backed up any data you want to keep, i would download dban nuke disc from [here](http://dban.sourceforge.net/). This will format your hard drive into submission and make sure that everything is securely deleted.

then i would boot up with the windows cd. create a partition for your windows installation. (I always create tow partitions for windows. one has the system files AND NOTHING ELSE, and the other all my data and programs. this helps combat the old fragmentation program. and then install diskeeper ;) look on pirate bay if you have trouble with that one :D).

install windows, updates, drivers etc, go into control panel, computer administration, disk management and make a partition for your data and programs, leaving plenty for kubuntu.

(Btw, always install windows first, as it will overwrite grub otherwise and you will have to faff around reinstalling it otherwise).

then pop in the kubuntu cd, and boot up in livecd mode, just to check everything works out of the box ;) click on the install icon on the desktop and follow the instructions. But, when it comes to partitioning, choose the manual option.

it'll be obvious which partitions are your windows ones, and then create four partitions in the free space.

1). mounted as /boot, only need 100 meg for this one. (well you can use less that that but i like to give myself plenty of headroom ;)).

2). mounted as / (that is root partition), this is where most of your programs are installed. I never know how many i will install, so i will always give myself 5-10 gig minimum ;)

3). mounted as a swap partition. depends really, but i usually give it 1-2 gig.

4). mounted as /home and taking up the spare space.

Well, that's how i would do it anyways, sure someone will disagree with me. (sure i remember reading somewhere that the swap partition should be the last one, but never made any difference to me).

Hope that helps ;)

---

### Post by shifty_powers on 2008-05-10
> **Xiong Chiamiov said:**
> Using FAT for storage space is only a good idea if he is needing to transfer files between the 2 OSs frequently.  I occasionally need to grab something from Windows on Kubuntu, and that works just fine.  I don't boot into XP very much at all, so I have no need to grab files from my linux partition, although there are ways of doing so.  I'd prefer to use a filesystem that is journalled and supports large filesizes rather than having the portability, myself.


well tbh, i've found the ntfs3g drivers to work perfectly, though i'm sure someone will pop up with a scare story ;)

and i've always used ext3, although i know some people use reiserfs. not particularly fussed meself ;)

---

### Post by Paqman on 2008-05-10
> **mahender.mandala said:**
> The reason I say FAT32 is, it can be easily shared by both winxp and ubuntu.


So is NTFS, and it's a much better file system than FAT32. FAT32 can't handle large files, and quickly becomes very fragmented.

---

### Post by pallav on 2008-05-12
Thank you for all the help
i have a 40 Gb hardisk and i want to share data b/w the 2 os. shld i use ntfs or fat .how many partitions shld i create?

---

### Post by shifty_powers on 2008-05-12
> **pallav said:**
> Thank you for all the help
i have a 40 Gb hardisk and i want to share data b/w the 2 os. shld i use ntfs or fat .how many partitions shld i create?

entirely up to you on both counts. Ubuntu will now happily read and write both file systems out of the box. NTFS is better for technical reasons i shan't go into, but using fat32 is not a problem.

As for how many partitions, as this purely a data drive that will share between the two os's, it comes down purely to how you want to organise it. Think of partitions in this case as more permanent folders ;)

The simplest way would be to just have one partition, labelled as anything you like. It's not like when you were creating the kubuntu partitions and had to define mount points. Kubuntu will automount it and xp will assign it a drive letter.

Have fun ;)

---

