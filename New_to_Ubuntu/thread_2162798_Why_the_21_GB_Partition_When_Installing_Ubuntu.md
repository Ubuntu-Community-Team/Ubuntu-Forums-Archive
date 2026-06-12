---
title: "Why the 21 GB Partition When Installing Ubuntu?"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by Smallwheels on 2013-07-16
I just read the thread How To Create /home Partition When Installing Ubuntu? at this link: [http://ubuntuforums.org/showthread.php?t=1917137](http://ubuntuforums.org/showthread.php?t=1917137) . 

I read the Gparted tutorial and even watched a couple of videos about using Gparted. These resources gave good information but I don't understand some things. 

First of all why does Ubuntu create a 21 GB file and one that takes up the remaining space of my hard drive? I have a 320 GB hard drive. 

In the Gparted instructions it mentions that all Ubuntu Live CDs have Gparted already installed. One should just select the advanced button to set up partitions. In the thread about installing Ubuntu a forum poster says it is better to set up partitions ahead of time using a Gparted Live CD. Isn't using the Ubuntu Live CD in the advanced mode doing the same thing? 

I would like to know how to label my partitions. One tutorial says to use only primary partitions if I'm creating four or less. Gparted says for Linux it can all be done on extended logical partitions. One person in the thread suggests using at least four partitions but doesn't recommend any type. Why should the root (/) be separated from the (/home) partition? I'll need to create one for the boot but really don't know the sizes I should make for any of these. I don't even know the size of the Ubuntu 13.04 OS. I probably should make the boot one a bit bigger than the actual size because if I keep updating the OS it probably will need more space right? 

Here is what I want to do with my Ubuntu only installation on my HP computer with an AMD 2.3 GB Sempron LE 1300, 2 GB RAM and 320 GB hard drive; I intend to mostly stream video and create videos using several video applications. I'll use either Libre Office or Open Office to make presentations with lots of slides. I'll be using Audacity to combine separate audio feeds into my videos. I'll also sometimes be using a screen capture program in my productions. 

How many partitions would be optimum and at what sizes? In one post someone suggested that at least one partition should be used to double the RAM. How does that work? 

I'm open to suggestions and ready to go. How many do I need? What sizes should they be? What should I name them? If I should use a separate Gparted Live CD to prepare the hard drive instead of the one built into the Live CD (I'm using an Ubuntu Live USB) why should I do it that way? What is the difference?

Thank you.


Smallwheels

---

### Post by hansdown on 2013-07-16
Hi Smallwheels .

If you wish to install "only" ubuntu, simply choose

> use entire drive

or what it says.

---

### Post by su:bhatta on 2013-07-16
If I am not mistaken SmallWheels, you want only Ubuntu on your system, hence just select  'erase disk & install Ubuntu'

This page lists graphical installation:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

These two pages give details for partitioning in Ubuntu installation:

[https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition?highlight=%28\bCategoryInstallation\b%29](https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition?highlight=%28\bCategoryInstallation\b%29)
[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics?highlight=%28\bCategoryInstallation\b%29](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics?highlight=%28\bCategoryInstallation\b%29)

and this page lists all help regarding 'Category Installation'

[https://help.ubuntu.com/community/CategoryInstallation](https://help.ubuntu.com/community/CategoryInstallation)

I have found sticking to help.ubuntu.com for these issues are beneficial....

---

### Post by su:bhatta on 2013-07-16
For partitioning Schemes this page lists down & explains it quiet well:
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by Smallwheels on 2013-07-16
Yes I intend to use the whole drive for Ubuntu because I WON'T EVER USE A MICROSOFT OS AGAIN! OK maybe that was a bit of an outburst but I really hate that compay since Vista. I have no intention of dual booting with another GNU/Linux distribution because I like to find something that works and then get to work.

I recently moved and before the move I wanted to backup all of my machines just in case they got damaged in the move. When I went to backup the files in Vista it wouldn't boot. That was my last straw with Microsoft. From now on I will be free of that company. Maybe some of you feel the same way. 

Anybody willing to give explicit answers to my questions please do reply. I've been sent to tutorials and threads with information in the past. What I find is that I learn things but rarely are all of my questions answered. I'll look at the information at the links provided but I'd also like for direct answers to my questions, especially how to increase my RAMs ability to do its job using another partition.

---

### Post by carl4926 on 2013-07-16
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf)

You sound familiar
[https://forums.opensuse.org/english/other-forums/community-fun/488723-thread-closed-re-microsoft-novell-open-suse-collaboration-isevil.html](https://forums.opensuse.org/english/other-forums/community-fun/488723-thread-closed-re-microsoft-novell-open-suse-collaboration-isevil.html)

---

### Post by mastablasta on 2013-07-16
no need for extra partitions. as mentioned just select to use the whole drive and installer will create necessary partitions for you. same thing happens if you install to free disk area.

what you talk about - ram increase - is the so called swap partition (/swap). it is like pagefile in windows. basically when you run out of RAM hard disk is then used. ofcourse disk is A LOT slower than ram so this slows down the whole OS. however it may come in handy in some cases. especially when you run out of ram :-) again this part is created automaticly if you use the whole disk to install the OS.

i am not sure about 21GB file. are you using wubi to install it? that would be the wrong way to do it.

---

### Post by Smallwheels on 2013-07-16
> **carl4926 said:**
> [https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf)

You sound familiar
[https://forums.opensuse.org/english/other-forums/community-fun/488723-thread-closed-re-microsoft-novell-open-suse-collaboration-isevil.html](https://forums.opensuse.org/english/other-forums/community-fun/488723-thread-closed-re-microsoft-novell-open-suse-collaboration-isevil.html)

Yes and I use the same name across forums. I was trying Open SUSE and it was coming along. Then I found the video about Novell partnering with Microsoft and that was it for me. We're entitled to our opinions and my opinion of Microsoft is that it is an unethical company that stole money and time from millions of people around the world. They knew Vista was garbage yet they put it out there as a finished product. I know I'm not the only one who now hates them and doesn't want to use their software.

---

### Post by carl4926 on 2013-07-16
> **Smallwheels said:**
> Yes and I use the same name across forums. I was trying Open SUSE and it was coming along. Then I found the video about Novell partnering with Microsoft and that was it for me. We're entitled to our opinions and my opinion of Microsoft is that it is an unethical company that stole money and time from millions of people around the world. They knew Vista was garbage yet they put it out there as a finished product. I know I'm not the only one who now hates them and doesn't want to use their software.

I'd suggest you let us see a screen of your partitions
Because openSUSE defaults to a separate /home partition. Ubuntu does not.

---

### Post by 3rdalbum on 2013-07-16
Vista is not bad, I prefer it to 8.

Installing Ubuntu is as lot easier than you think. Don't worry about manual partitioning, just tell the Ubuntu installer to use the whole disk. It will create a partition for files and the operating system, and a second partition for swap. This will all be fine without any need for adjustment. It's that easy.

---

### Post by Smallwheels on 2013-07-16
> **3rdalbum said:**
> Vista is not bad, I prefer it to 8.

Installing Ubuntu is as lot easier than you think. Don't worry about manual partitioning, just tell the Ubuntu installer to use the whole disk. It will create a partition for files and the operating system, and a second partition for swap. This will all be fine without any need for adjustment. It's that easy.

I liked Vista better than XP for a couple of days but too many things just wouldn't work. For instance the spell checker wasn't working in the mail application. Even though I turned it on it just wouldn't work. To get it to work a tech support person told me the way to fix it was to change the language from English to something else and save the settings. Then go back and switch it to English. That was insanely stupid but it worked. I bet the guys and gals in Redmond are proud of that one. 

I documented being on the phone with tech support for over 40 hours before just giving up on Vista. What would that be worth to somebody? 

Back to business. Does the automatic setup include a separate partition for the /home file instead of putting it into the root partition?

---

### Post by Smallwheels on 2013-07-16
I forgot to add the information about where I got that 21 GB. In the Live USB mode I observed on the left column of the dock two hard drive symbols. One was about 296 GB and the other was 21. Add those together and it doesn't equal 320. Was that the prospective division that would be placed on my hard drive were I to install it from the Live USB? If not then what was that?

---

### Post by coffeecat on 2013-07-16
> **Smallwheels said:**
> I forgot to add the information about where I got that 21 GB. In the Live USB mode I observed on the left column of the dock two hard drive symbols. One was about 296 GB and the other was 21. Add those together and it doesn't equal 320. Was that the prospective division that would be placed on my hard drive were I to install it from the Live USB? If not then what was that?

If you saw two hard drive icons, one ~296GB and the other 21GB, in the launcher on the left of the screen, these represent partitions already present, not partitions that the installer will create. Perhaps the 21GB partition is a Windows recovery partition?

Post a screenshot of the Gparted window from the live session and we can see what your current partition layout is like. Also, your HD is 320GB (base 10), but Gparted (and I believe the Launcher) give sizes in GiB (gibibytes - base 2), so you need to convert one to the other before adding up the figures. Whatever - 320GB = 298.02 GiB so something doesn't add up. A Gparted screenshot might clear this up.

---

### Post by 3rdalbum on 2013-07-16
The automatic partitioning does not create a separate /home. It's not necessary really, anymore. If you want a /home partition you have to go into the manual partitioning. A /home partition has few benefits these days - in the past, you needed one in order to save your files and settings if you did a clean install of a newer version of Ubuntu, but that is no longer the case - you can preserve your /home even when it is on the same partition as /

You could go with 25 gigs for / and the rest for /home. I don't bother with swap, but if you need it you can make it twice the size of RAM. I don't bother with swap because I never fill more than a gig of RAM anyway.

296 gigabytes plus 21 gigabytes is 317 gigabytes. As soon as you format a hard disk you lose a certain percentage of space, more so for each partition as each partition is formatted separately. That sounds about right for a 320 gig drive.

You can let Ubuntu do the partitioning for you automatically, or you can worry over the details yourself. The defaults are perfectly fine and I'm a big believer in computers making our lives easier, not giving us extra things to worry about. I have a separate /home but it is on a different physical disk for speed reasons. My other computers stick with the default "erase hard disk".

---

### Post by grahammechanical on 2013-07-16
If we are installing to a hard disk with no other OS on it or if we are willing to remove the existing OS, then Ubuntu will install itself in a single partition (a primary partition). It will also create another kind of primary partition called an extended partition and in there it will create a logical partition for the swap partition. I do not know the default sizes for these partitions. But Ubuntu can install in a partition of less than 6GB.

The OS/file system is given a mount point of / (root) and inside of there will be the /home folder where the users configuration files and data are kept. So, in normal use less than 6GB would be very restrictive.

Some of us prefer to keep /home on its own partition. If we need to reinstall then the new installation will not wipe out the configuration files or the data in /home partition. In this situation a /partition of 10GB - 20GB or even up to 25GB is thought adequate. It all depends on how large any additions programs that you need to install are. The rest of the disk (except swap) is used for the /home partition. What else would you do with all that space? If you want to stream videos then you will surely need as much disk space as possible.

Others among us also have our data on another completely separate partition or even disk. We do not mount it during installation but it will be picked up by file manager when we log in. 

Most of this is a matter of personal preference. If you want as much space as possible for video storage then you can reduce the size of / to 10GB. You can un-install some of the applications that you do not intend to use through the software centre. That will create more space for any special applications that you need to install for video streaming.

If we have /home as a folder under / and we need to re-install it is possible to do it without over writing the configuration files in /home by not marking the partition to be formatted. Then only the system folders and files will be over written. The install will even pick up your user name and password without you needing to re-enter them.

Some people choose to have a separate /boot partition but then as the Linux kernels are updated that small partition becomes full and there is a problem. It is not necessary to have a separate /boot. This kind of thing dates back to the early days of Linux when all the basic system folders were actual partitions.

In the old days the size of the swap partition was said to be half the size of RAM. Today, with suspend and hibernation it is thought that the swap partition size should be double at least the size of RAM.

I have never noticed an option to label partitions during an installation but afterwards the Disks utility will do that. But be careful. The Disks utility in 13.04 will effectively label existing partitions. But when I tried to label partitions using older versions of Ubuntu I got a warning that the action would remove all data in the partition. So, I say be careful because I do not know what version of Ubuntu you intend to install.

Regards.

---

### Post by mastablasta on 2013-07-16
i think /boot is still needed on some new laptop (possibly desktops) due to UEFI. i remember i saw a lenovo laptop that had ubuntu working out of the box perfectly as long as you created a boot partition on it. at least i think it was because of UEFI (replaces BIOS on new maschines).

also FYi i have Xubuntu installed on 8 Gb. ok it doesn't leave me much space for programmes and updates, but it's there. i've added a few server tools so i can test websites and browse suspicios ones.

---

### Post by Smallwheels on 2013-07-16
So some of my questions have been answered and that is very good. I want to install 13.04. I will probably upgrade at the next release and if I like 14.04 and it becomes an LTS I'll move to that one. I was happy with 10.04 LTS for a year or so. 

When I complete any work project it will be stored on an external hard drive or even a CD ROM. I don't fill up hard drives like some people. If I added together the sum total of all personal files on three computers over eleven years it would equal less than 200 GB. So  disc space won't ever be a problem for me. 

I guess I'll just load Ubuntu as is from the Live USB and examine it later. When I eventuallly upgrade in a few months I'll then get more into this. I've learned a lot from reading the instruction manual from Gparted and forum replies. In the comming months I'm sure I'll learn more about it. With experience under my belt I'll know what I need and want from the OS and choosing the configuration will be straight forward. 

I'll be back with more questions soon once I get it installed. In the Live USB the VLC player was having problems. If I'm lucky they will go away once 13.04 is installed on my drive. 

Thank you. 



Smallwheels

---

### Post by carl4926 on 2013-07-16
> [COLOR=#000000]In the Live USB the VLC player was having problems. If I'm lucky they will go away once 13.04 is installed on my drive. [/COLOR]Depends what you are doing. But the restricted extras can be installed in live mode

---

### Post by Smallwheels on 2013-07-16
I installed the restricted extras in the Live USB version and it worked. I've loaded 13.04 now and some things aren't working as well as the Live USB. I'll post a new thread soon if I can't work things out.

---

### Post by Bashing-om on 2013-07-16
Smallwheels;
To add, when you get the installation process simplified.

[quote=Smallwheels]Here is what I want to do with my Ubuntu only installation on my HP computer with an AMD 2.3 GB Sempron LE 1300, 2 GB RAM and 320 GB hard drive;[/quote]

We have the same hardware on my wife's machine... I found later versions to be laggy on it... installed Lubuntu 13.04 ... runs fabulous !

[INDENT][INDENT]hey, just a heads up[/INDENT][/INDENT]

---

