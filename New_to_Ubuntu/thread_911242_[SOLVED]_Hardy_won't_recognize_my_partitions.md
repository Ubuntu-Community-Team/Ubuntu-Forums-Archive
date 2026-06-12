---
title: "[SOLVED] Hardy won't recognize my partitions"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Jason50153 on 2008-09-05
Hi I am running Ubuntu on a live cd right now and am trying to install it. I have two partitions: one for Windows, one blank one that I want to use for Ubuntu. However when I go to install Ubuntu it won't recognize my partitions. Under the prepare partitions screen it just lists /dev/sda. What should I do. Keep in mind I am new to Ubuntu so I don't really know what I am doing. Thanks.

---

### Post by tuxulin on 2008-09-05
if it shows "/dev/sda" then thats the disk which you probably already know.
so im taking it that you have only 1 disk in your machine.

why not then choose manual setup then next. on the new page it should show
you the two partitions there or is this the part where you do not see the partitions ?

Tuxulin

---

### Post by Elfy on 2008-09-05
If that doesn't appear to show the empty space, look in partition editor in system>admin menu

Maybe download and burn partedmagic - a livecd tool set - with a partition editor on it.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

---

### Post by ingeva on 2008-09-05
> **Jason50153 said:**
> Hi I am running Ubuntu on a live cd right now and am trying to install it. I have two partitions: one for Windows, one blank one that I want to use for Ubuntu. However when I go to install Ubuntu it won't recognize my partitions. Under the prepare partitions screen it just lists /dev/sda. What should I do. Keep in mind I am new to Ubuntu so I don't really know what I am doing. Thanks.

It seems to me that there may be a problem with the partition table. I suggest you use Windows to make a backup of the Windows disk so you can create new partitions on it -- if at all possible.

You need at least three partitions; one for Windows and two for Linux. The third one is the swap partition. Choose "manual" as suggested and size the three partitions according to your needs. Keep the suggested size for the swap partition.
You may want to place the "home" directory on a partition of its own. I recommend that because you can re-install without losing your settings. An experienced user will only re-install the system as an exception, but for a new user it may well be an "easy way out" in the beginning.

After you have installed the partitions using Linux, re-install Windows on the Windows partition (You will have to change partition type and reformat it) and install Linux again.

The reason to do it in this sequence is to have Linux create the grub loader, which it won't do on a "virgin" disk.

If this seems complicated -- Well it is, but I think your problem is a little unique.
Making a backup before you start doing risky things is a good idea anyway.

---

### Post by Jason50153 on 2008-09-05
I went to partition editor and it said that my partition is unallocated with 149.05gb (my hard drive is 160gb).

Do I really need 3 partitions?

Finally how do I use PartedMagic?

---

### Post by Jason50153 on 2008-09-05
Oh I don't know if this helps but in file browser I found something labeled 80GB Media, which contains my XP stuff. Also there is something labeled as New Volume, which contains 72gb.

---

### Post by Elfy on 2008-09-05
> Do I really need 3 partitions?Only if you want to keep windows, which I assume you do.

Is the 72GB partition empty - does it correspond to the blank one in your first post. IF you are at all unsure - open the partition editor on the buntu livecd and post a screenshot - [http://ubuntuforums.org/showpost.php?p=4527031&postcount=4](http://ubuntuforums.org/showpost.php?p=4527031&postcount=4) - now is the time to clear things up :)

Need to get a couple of things cleared up first as it will affect your partitioning -

do you want to use any of the space to share between windows and linux?
do you want to have a seperate /home? - think of it as a linux "docs and settings"
do you have a need to hibernate?
how much ram do you have?

---

### Post by Jason50153 on 2008-09-05
The 72GB partition is empty. I don't want to share between windows and linux. I want to have a seperate /home. I would like to be able to hibernate, unless it will be a huge problem to do this. I have two gb of ram.

---

### Post by Jason50153 on 2008-09-05
Here is a picture of my partition editor.

---

### Post by Elfy on 2008-09-05
There is not 2 partitions there - do you actually have a windows installation that works?

---

### Post by Jason50153 on 2008-09-05
Yes my windows installation works. I know it doesn't have two partitions there, I was just saying I could find the windows partition and other partition somewhere else (in the "Places" menu).

---

### Post by Elfy on 2008-09-05
Well I'm not sure then - does it look the same if you boot partedmagic? If partedmagic sees the 2 partitions do the partition there - make an extended in the 72GB - with a 10GB ext3, 2.2GB swap and ext3  taking rest of space.

What windows is it - id it's vista do the partion work in there. What does windows see in it's disk manager?

When you boot parted magic - if you ethernet you can connecto the net and firefoxx.

I would have to say that there is something not quite right here, what sort of hardware is it - sata, ide.

---

### Post by ingeva on 2008-09-06
I'll repeat what I said before:
If you don't have a backup of your Windows disk and want to save it, make sure you can restore at least your user data.

You definitely need three partitions. Evidently you can't use gparted because there's something fishy there. Use Windows to remove the empty partition completely, making it "free space". Then boot up the installer/live CD. If you're allowed to make new partitions during the installation, make at least two; one for Ubuntu and one for swap area. (If not you're sold and need to start with an empty disk).

I would make another one as well; for the /home directory. This will make your life very much easier later. Depending on how much you're going to install, allocate 10GB or more to the system, just above 2GB for swap, and the rest to /home. Leave the Windows partition alone and unchanged in this process.

You'll be able to access the Windows files from Linux, but not the other way around.

After you have installed, check add/remove programs, make at least one change, and after it has fisished use the Update Manager to get all new updates. They are many and may take some time to download.

---

### Post by Jason50153 on 2008-09-06
I just realized there is some partition that windows xp must have automatically installed called mediadirect (C:). It has 2.5gb total and 1.3gb unused.

So can I have more than four partitions?

---

### Post by Elfy on 2008-09-06
You can't have more than 4 primary partitions on a disc - an extended counts as 1 - you can have many logical partitions inside an extended.

But until you can you get the partitioner to recognise the space you're going to have problems.

Have you tried to do as ingeva has said and deal with the partitioning in windows.

Following on from that - I asked some questions in #12 - are you able to answer them.

---

### Post by ingeva on 2008-09-06
> **Jason50153 said:**
> must have automatically installed called mediadirect 

So can I have more than four partitions?


I have no idea about a mediadirect partition.

You can have 4 main (primary) partitions on one drive, but the best thing to do is to make one primary (usually for Windows) and one extended, that can be divided into as many logical partitions as you want. If there's any limit to the number of logical partitions it's quite high.
If you use Windows to remove the empty partition, you can also use it to create an extended partition. I don't know what the Ubuntu installer will do, but it probably asks the right questions. So far I haven't checked because I haven't had the need.

---

### Post by Jason50153 on 2008-09-06
Okay I deleted the mediadirect partition (after backing it up) and cleared the second partition so it is all free space. I then loaded up the ubuntu live cd and it it finally correctly recognizes my partitions. I still have a few questions though...

First should I have just one primary partition (for windows) and one extended partition (with 3 logical partitions inside of it)? Second if I have 10gb for the system, and then 2gb for the swap and the rest to /home, when I download things will it all go to the /home? Finally I don't know how to make multiple logical partitions in Ubuntu (i can in windows but i don't know if that will work) and i don't know what settings to put. Here is a picture of the settings for editing the partition.

---

### Post by Elfy on 2008-09-06
Woot:)

I would always go for putting everything in an extended - means if you ever need to you could resize and make more primaries.

I've never used that partitioner - I assume it is inside the install procedure, it doesn't appear to be able to let you make an extended.

Personally I think it's more intuitive to use the partition editor in the system >admin menu.

In there you would make an extended partition in the free space, then make 3 logicals inside that extended partition to the sizes you have decided on. It looks similar to the screenshot, there you can see I have 2 logicals inside an extended.

Once the partitins have been made - choose manual partition during installation. Select the partition you have made for / - edit partition, from the drop down menus choose Use as ext3 journalling and Mountpoint of / , repeat for home in the same way and pick mountpoint of /home.

Sorry I can't help with your screenshot - but I've always had mine made before I install :)

---

### Post by Jason50153 on 2008-09-06
Do I put the free space as following or preceding?

---

### Post by Jason50153 on 2008-09-06
Never mind on my last question.

Anyways I installed it and it works!!!

Thank you very much ingeva and forestpixie! I couldn't have done it without you. 

BTW should I give you guys 1 thanks or multiple as this was quite the lengthy process?

---

### Post by ingeva on 2008-09-07
> **Jason50153 said:**
> 
First should I have just one primary partition (for windows) and one extended partition (with 3 logical partitions inside of it)? Second if I have 10gb for the system, and then 2gb for the swap and the rest to /home, when I download things will it all go to the /home? Finally I don't know how to make multiple logical partitions in Ubuntu (i can in windows but i don't know if that will work) and i don't know what settings to put. Here is a picture of the settings for editing the partition.

I think you get it right. However, for Ubuntu to set up GRUB (the Linux boot loader) correctly, the best thing to do would be to re-install Windows, and in that process just make a partition big enough for it. If you need more than one Windows partition (no problem!) use Windows's Disk Manager to create first an extended partition, and then one or more logical partitions inside it, that leave room for you Linux partitions later. If you don't need these partitions, just proceed.

When you install Linux after this, you will find that the disk has one partition called /dev/sda1 or /dev/hda1 (I'm not 100% sure but I think Linux chooses "sda" for SATA disks and USB disks,. and "hda" for PATA. Doesn't reall matter.)
The following partitions (if any) are numbered with higher numbers, normally consecutively. When you use the partition editor from the installer, existing partitions are well marked. Just add more logical partitions. Allocate the first to the system, the second to swap (2GB is normally sufficient) and the third to /home, taking up the rest of the free space.

I let downloaded files go to the desktop, and then I can easily drag/drop them to wherever I want them to be.

After writing this I see that there are other replies but I don't see any conflicts. Nothing is absolute and much is left for you to choose.

I'll just add that the installer's partitioner makes extended partitions as needed; you don't have to bother thinking about it. Just create the logical partitions that you need. I agree with forestpixie that extended/logical partitons are best because they are easier to manipulate. I'm not sure if you can boot from a logical partition unless there's also an activated (bootable) primary partition. Someone here will know.

About thanks: One thank you is good! :)
This forum has been very useful to me and I have learnt a lot because of it. There are many members here who deserve thanks, but in this forum thankyous seem to hang very high! :)

---

### Post by Elfy on 2008-09-07
> BTW should I give you guys 1 thanks or multiple as this was quite the lengthy process?You don't have to give any thanks at all if you don't want to; I'm happy knowing you're all sorted.

What I would like you to do is mark the thread solved :) - use thread tools at the top of the page.

---

### Post by egalvan on 2008-09-07
> **ingeva said:**
> The reason to do it in this sequence is to have Linux create the grub loader, which it won't do on a "virgin" disk.

I'm a little lost, what do you mean by this?
Am I going to have problems installing on a new/empty disk? :confused:

---

### Post by ingeva on 2008-09-07
> **egalvan said:**
> I'm a little lost, what do you mean by this?
Am I going to have problems installing on a new/empty disk? :confused:

No you are not, but if you're a beginner and want to have both Windows and Linux on your computer, it will be easier if you install Windows first.

The GRUB loader will actually be installed in both cases, but if you only have Linux installed you won't see it -- and a Windows installation overwrites it so you won't be able to boot Linux until you fix it.

Better to make evferything work the first time, don't you think?

---

### Post by egalvan on 2008-09-07
> **forestpixie said:**
> If that doesn't appear to show the empty space, look in partition editor in system>admin menu

Maybe download and burn partedmagic - a livecd tool set - with a partition editor on it.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

I agree with forestpixie on PartED Magic. It's small (<50meg), and (in my opinion) better than using an Ubuntu LiveCD for partitioning work.
And it almost always has a more updated partition editor (GParted).
The partedmagic I downloaded a few weeks ago gave support for labels, which the Ubuntu 8.04.1 did not have.

And as I always mention, if you find that you use this software, then consider donating a couple of bucks to the writers. Help keep our choices alive!

---

