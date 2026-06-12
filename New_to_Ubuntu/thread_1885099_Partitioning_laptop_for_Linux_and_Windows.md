---
title: "Partitioning laptop for Linux and Windows"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by ubni on 2011-11-22
Dear Ubuntu Community,

I have a [HP 8540w EliteBook]("https://www1.ethz.ch/neptun/hardware/modelsPC/h10_modelle3") and would like to run Ubuntu alongside Windows and later Mac OS with one of the [platform virtual machines]("https://secure.wikimedia.org/wikipedia/en/wiki/Comparison_of_platform_virtual_machines"). I want these three OS since I am learning to code with [Python]("http://python.org/") and I want to make sure that the code I write works on all three OS and is platform independent. To be able to test this I like these three OS running on the laptop. For now I am not worried at all about the Mac OS and will attend to that at a later date since I will only run this in a virtual machine.

So far I have been using Windows, XP and 7. Since I see many advantages using Ubuntu for several things I cannot do with Windows and my need for coding and testing the code on these three platforms I would now like to learn to use Ubuntu next to Windows.

When working with Windows I always keep the OS, drivers, software installations on C: and my work data on D:. I regularly [image the OS onto an external hard drive]("http://www.macrium.com/reflectfree.aspx"), so to speak partition C:, to be safe from hell.

My questions now are how can I understand the two OS working next to each other on one hard drive with several partitions. For this I have drawn out a very simple graphic of how I would logically think this would work. Since I have absolutely no experience with Ubuntu please do not mind if this is completely wrong.

The top row represents the hard drive as I have it now and the bottom row represents the hard drive as I would imagine it running Ubuntu and Windows on it. Of course the drive letters represent the single partitions, that is why I did not include vertical separator lines in the graphic.

[IMG]https://lh5.googleusercontent.com/-8zMH5MHzHkk/TzsHlF4BmCI/AAAAAAAABXA/r0gkfQCjYc0/s0/[/IMG]

Before I start with the correct partitioning of the hard drive I would like to know how the two OS will be placed onto the partition and how much space I should ideally assign to them. All the work data from the drive has been saved externally and I will actually [DBAN]("http://www.dban.org/") the whole drive before starting to work with the two OS next to each other. As you can see I am really willing to do and learn this correctly from the beginning.

As far as I understand under Windows I install the OS and the drivers, make a first default OS image, then install the software I like including all settings and preferences, make another OS image and start working with the laptop. This method has proven to be very productive and safe for me for years so far.


[LIST=1]
[*]Can I understand this under Ubuntu similarly? From what I think, and please do correct me if this is not the case, the Ubuntu OS will surly be installed on a separate partition like shown in the bottom row of the above graphic, no?
_
[*]What about my work data that I keep on D: respectively on E:. Can I access that data from the Ubuntu OS as well or does Ubuntu keep all the OS files and the work data in one partition, similarly to having all your work files on C: My Documents under Windows, and then when something messes up not only the OS but the whole work data is gone as well?
_
[*]You can see that I would clearly like to separate the OS from the work data. Is this possible with Ubuntu as well and how can I prepare the partitions correctly to achieve such a setup? Is such a setup actually advisable when running Ubuntu?
_
[*]What about the drivers for my laptop model? Under Windows I have meticulously organised all the drivers that I need for the laptop, burnt them onto a CD and can install them fast once I have installed the OS. Is something like this possible with Ubuntu as well? Where do I get the drivers for my laptop under Ubuntu? Is my laptop at all compatible to run Ubuntu or will I have to accept deductions, like not being able to properly use the graphics or sound card with it for example?
_
[*]Last not least, similarly to imaging the OS under Windows once I have reached a satisfactory state of the OS, can this be done under Ubuntu as well? I like to have images of the working setup under Ubuntu so that I do not have to worry about making mistakes and can quickly revert to the initial setup and state of the OS when something goes wrong.
_
[*]What do I install first, Ubuntu or Windows and why?
_
[*]Keeping in mind the bottom row and that I like to be able to access my work files from the Windows OS as well as from the Ubuntu OS how much space do I approximately need to assign to the pure Ubuntu OS on the hard drive?
_
[*]When I install software under Ubuntu, will that install onto the Ubuntu OS partition? Meaning do I need to leave more space on the Ubuntu OS partition when I later like to install software onto it?
[/LIST]
I hope that these question are not too much to ask in the absolute beginners forum. These are the questions that I have and I think in order to do all this correctly I need to have some sort of idea of what I am doing before I actually go ahead and half-knowingly slap on Ubuntu onto the laptop only to later discover that it does not work out the way I want it to work or the way it is supposed to work.

I am very thankful for informative and helpful replies, links to tutorials and explanations, ideally with graphics illustrating the partitioning. I have gotten myself a [1100+ pages book on Ubuntu/Linux to learn all this properly]("http://openbook.galileocomputing.de/ubuntu/") as well and am starting to dig into it. However if someone could illustrate to me how all this will work together I would have a starting point and could and will use the book as a reference when I need more and detailed explanations.

Thank you very much for any replies partly or whole answering my questions. I salute the Ubuntu Community and hope to prosper and have as much fun with the OS as all the cracks out there online and offline are telling me it really is.

Regards,
Ubni

---

### Post by Megaptera on 2011-11-22
I think you're on the right line but I found your posting too long - sorry! Anyway, I think these will help:
[http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/](http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/)

[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by ubni on 2011-11-22
Thanks for your reply. Well in that case I will make it really simple.

Before I go Linux and into partitioning I need to make sure the machine supports it.

How can I find out if my laptop is compatible with Ubuntu?

Detailed hardware information about my laptop can be found at this link:

[https://www1.ethz.ch/neptun/hardware/modelsPC/h10_modelle3](https://www1.ethz.ch/neptun/hardware/modelsPC/h10_modelle3)

Thank you.

---

### Post by Mark Phelps on 2011-11-22
> **ubni said:**
> 
Before I start with the correct partitioning of the hard drive I would like to know how the two OS will be placed onto the partition and how much space I should ideally assign to them.
Linux does not use the Windows concept of drive letters, but like Windows, it will install the OS and apps within the same filesystem.  If you want to SHARE data between Windows and Ubuntu, then create a separate DATA partition, and format it NTFS -- since both can read & write to NTFS file systems.

> As far as I understand under Windows I install the OS and the drivers, make a first default OS image, then install the software I like including all settings and preferences, make another OS image and start working with the laptop. This method has proven to be very productive and safe for me for years so far.
 Good approach -- this is exactly what I've done for years.


> 1) Can I understand this under Ubuntu similarly? From what I think, and please do correct me if this is not the case, the Ubuntu OS will surly be installed on a separate partition like shown in the bottom row of the above graphic, no? Yes, for best results and performance, install Ubuntu into its own partitions.
> 2) What about my work data that I keep on D: respectively on E:. Can I access that data from the Ubuntu OS as well or does Ubuntu keep all the OS files and the work data in one partition, similarly to having all your work files on C: My Documents under Windows, and then when something messes up not only the OS but the whole work data is gone as well?
To the degree you can, keep your work data on the separate DATA partition -- not in Ubuntu, not in Windows.  Ubuntu can read/write Windows partitions, but you really don't want to be making changes to the Win7 OS files from inside Ubuntu.  That is asking for trouble.  Windows can read Ubuntu, but you should not be trying to change Ubuntu files from inside Windows.
> 3) You can see that I would clearly like to separate the OS from the work data. Is this possible with Ubuntu as well and how can I prepare the partitions correctly to achieve such a setup? Is such a setup actually advisable when running Ubuntu? You can create a separate /home partition for storing personal data, and while it functions similar to My Documents in Windows, it's not the same implementation.
> 4) What about the drivers for my laptop model? Where do I get the drivers for my laptop under Ubuntu? Is my laptop at all compatible to run Ubuntu or will I have to accept deductions, like not being able to properly use the graphics or sound card with it for example? Unlike with Windows, you don't install drivers from a CD or download them; instead, when Ubuntu is installed, it scans the hardware and downloads the drivers needed.  A good approach is to boot from the Ubuntu desktop CD, selecting Try Ubuntu, and see how well it works -- from the standpoint of detecting hardware and installing drivers.   Every PC is different, so there's no guarantee that anything will work before you try it.
> 5) Last not least, similarly to imaging the OS under Windows once I have reached a satisfactory state of the OS, can this be done under Ubuntu as well? I like to have images of the working setup under Ubuntu so that I do not have to worry about making mistakes and can quickly revert to the initial setup and state of the OS when something goes wrong. Again ... we think alike here, and I regularly image off the Ubuntu install using Clonezilla to an external drive. Takes 10 minutes to do the imageing and verification, and less to restore.
> 6) What do I install first, Ubuntu or Windows and why? Win7 -- because Ubuntu will detect Win7 when you install it second.
> 7)Keeping in mind the bottom row and that I like to be able to access my work files from the Windows OS as well as from the Ubuntu OS how much space do I approximately need to assign to the pure Ubuntu OS on the hard drive?
Spaces:
30GB - Win7 OS
10GB - Ubuntu (without /home)
10GB - Ubuntu /home
Remainer -- NTFS data partition  

(others may have different suggestiuons)
> When I install software under Ubuntu, will that install onto the Ubuntu OS partition? Meaning do I need to leave more space on the Ubuntu OS partition when I later like to install software onto it? You set up the partitions manually during the installation.  Ubuntu then automatically writes the files into the proper partitions during the install.  Spaces provided above should me more that sufficient -- provided most of the large data files are put into the DATA partition.

---

### Post by oldfred on 2011-11-22
i liked Herman's site that Megaptera linked above. He has lots of detail. Do not worry about difference in versions. Process is the same for install with slight screen differences.

Most HP's use all four primary partitions. Windows has to boot from a primary and Windows 7 uses two. A hidden 100MB boot/repair partition and the main install. HP then had the vendor recovery and a utilities partition. 

You should make a Windows repair CD, just in case you have to  repair Windows. You said you have good backups which is essential.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)


Linux usually includes all the drivers you need, sometimes it has to download wireless or video drivers and you need to install with a Ethernet connection, not wireless. Test liveCD to make sure your system works ok. With nVidia as separate card, I have to use nomodeset on first boot after install, not sure if that is the same for an internal nVidia chip or not.

If all your data is in a separate NTFS data partition, you do not need a large system partition. I generally suggest 10-20GB, but I use 25GB since I have space on my drives. swap can be 2GB or the size of RAM in GiB if you want to hibernate(but you do not really need to hibernate as it boots very quickly).

---

### Post by ubni on 2011-11-22
Thank you all for your replies. Coming here has indeed proven to be a first very helpful step. Thanks!

I will thoroughly read through the information supplied and then come back here to confirm what worked and what did not work.

---

### Post by ubni on 2012-02-14
Again thanks for the links! I have read through some of the info provided and have come up with this partition scheme.

The list is also the exact order on the HDD meaning I start with SWAP for example since it is recommended to use about [1.5 or 2 times]("http://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/") the amount of RAM for SWAP and have it at the start or end of the HDD for good speeds.


[LIST=1]
[*]SWAP 16GB since there is 8GB RAM on the laptop (is this too much?)
[*]Linux ROOT 20GB
[*] DATA NTFS
[*] Windows 7 40GB
[*] Linux Home 20GB
Here I would like ideally to save the Linux OS images. How big is a typical Ubuntu OS image made with Clonezilla please?
[/LIST]
 
All this I would do with Gparted, then install Windows onto the 4th partition (primary).

Do the Linux SWAP and Home partitions need to be primary as well or only the ROOT and SWAP and Home can be logical?

Again I have put Home at the end for good speeds. Is this really so vital for the OS? Why are the speeds at end and start of the HDD so much better?

I guess with this scheme I would be ready to go and run a first test.

Note there is no data on the HDD and I will wipe it with DBAN before installation. I do not keep any manufacturers "own" partitions like recovery and the additional software either on the HDD that came with the laptop.

What do you think?

---

### Post by oldfred on 2012-02-15
You can have Windows in sda4 since it is a primary, but Windows does not know about Linux partitions and sometimes gets confused if not the first partition. I would just make Windows sda1 if starting from a total new install. It is just a tad easier to Install Windows first as it automatically overwrites the MBR, and you would have to reinstall grub2's boot loader to the MBR if you install Windows second.

All Linux partitions can be logical. The default install of Ubuntu to a empty drive is / is primary & swap is logical. I prefer to use one or two primary partitions, then use the rest as logical. Then you have  a spare primary or two in case you need it later. I always make rest of drive the extended even if I do not fill the extended with partitions. I left 100GB unallocated and now keep adding 25GB for new / partitions so I can test or try a new install.

---

### Post by ubni on 2012-02-15
Please delete this reply, thank you. The reply I posted did not have to do with the original thread name any more.

---

### Post by oldfred on 2012-02-15
The extended partition is a primary partition and is just a container for all the logical partitions. Since it can be any of the four primary you could make sda2 the extended and not create sda3 nor sda4 as primaries. The first logical is always sda5 so you still have the "space" in the partition table for the remaining primary partitions.

You cannot use one /boot partition for multiple installs. I do not recommend separate /boot unless you have a very old system with the BIOS limit that you can only boot from the first 137GB or a server type configuration with RAID or LVM. 

If planning multiple / (root) partitions for multiple installs it may be better to keep /home inside the root partition and just have one data partition. Then the data is easily shared if distributions are in the same family (all Debian) or are configured with UID & GIDs at are the 1000 as Ubuntu uses.

Attached is a screenshot of my LapTop. It is not optimal but gives an idea of how it is set up with dual boot. It started with just XP and I added Ubuntu.

---

### Post by ubni on 2012-02-15
I thought it would be a good idea for people new to Linux to draw out the partitioning scheme before actually going about installing anything.

This is a first draft of trying to install two Linux distros and Windows on one HDD.

[IMG]https://lh6.googleusercontent.com/-W4nELj4VWWk/Tzw_gSywj-I/AAAAAAAABXU/w_IeRwVCpNw/s0/[/IMG]

I would very much appreciate it if other people could let me know their  recommendations or variations of above scheme. There are lots of  important things to know about all this but before actually going into  all that detail I thought it might be best to visualize what is going  on. In the end I hope to present to the interested Linux beginner a working graphic of a typical multiboot or triple OS install. So if this first try is not correct you will find the correct one at the end of the thread eventually.

One thing I am still trying to find out what the partitions will be named by Linux since this quote [from this post]("http://ubuntuforums.org/showpost.php?p=1646977&postcount=1") properly confused me. Ideally I would like to create a little graphic showing those drive descriptions as well. So to speak try and reach a solid partitioning scheme for two Linux distros and Windows.

"**_Note_: /dev/sda4 = Entire Extended partition. sda4 is  "theoretical" in that it can not be mounted as such, but it "takes up a  number".**[INDENT]**This is true for both Linux and grub speak !**"
[/INDENT]No idea what to make of that. What I would guess is that they would be in the sda1 being ROOT1 to sda7 being BOOT, but why skip sda4?

---

### Post by oldos2er on 2012-02-15
Closed, duplicate.

Edit: Re-opened. Sorry for any confusion!

---

### Post by ubni on 2012-02-15
Here is a reply to this thread:

[QUOTE=JKyleOKC]Apparently both copies of your thread were removed; here's the reply I tried to send you:

The Main Boot Record (MBR) only has space for four partition table  entries. The "extended" partition type was invented to allow more; a  drive can have only one extended partition, which is actually a small  area containing additional partition table entries for the "logical"  partitions, but which is shown in partition listings as occupying all of  the space assigned to the logicals, plus its own small storage area.

By convention, Linux defines the four "primary" (or three primary and  one extended) partitions as /dev/sdX1 through /dev/sdX4 (where X is the  letter assigned to the whole drive, starting with "a"). If all four are  assigned, the extended one becomes sda4. The logical partitions it  contains always start at sdX5 and go up from there.

If you create only a couple of primary partitions plus an extended one,  they will be sdX1, sdX2, and sdX3 (which will be the extended one. You  could specify all the rest of the drive to be part of the extended  partition, and then add logical partitions in that area at any time  later.

I'm not sure that you will be happy with your proposed layout; having  only 10 GB in each home partition might make things very tight, since  almost everything you do will be stored in your home directory and if  you have more than one user defined, all of their home directories will  be inside the single home partition. However it doesn't look bad  otherwise.[/QUOTE]

Thanks for your reply. Oohhh yes now I get it. The fourth point on the HDD being the Extended partition is where the other partitions start. 4 is the beginning of the new chain, extending the HDD. It makes perfect sense now. Wow, this was easy but yet I could not find an answer. Thanks!

There is enough space on the HDD so I am going to increase the home partitions to 20GB each, or should I even use more for it? Can I store system images of the particular Linux distro on the DATA partition as well or am I better advised to put it in the HOME partition for that distro? I like to regularly image the OS to be able to revert changes or errors easily.

10GB for each ROOT should be enough, same as 1GB for boot, am I right? I think I will also increase the SWAP to 16GB since the space is there.

I have tried to predict what the partitions will be labeled by GParted. I have used GParted before but not to do this. Perhaps new users can visualise better what will be going on when GParted is being used.


Here is a new draft.

The first row is the exact order that I think the partitions will actually appear on the drive. I am not sure if I can have a Pimary partition inside the Extended partition. However I think I got the partition naming in Linux right, no?

What about the speed? Would it be better to have the Data partition next to Windows in the middle of the drive and push Home1 and Home2 further to the end of the HDD? Is this really that much of a difference?

[IMG]https://lh5.googleusercontent.com/-WkYA017MZMA/Tzxqe_zlttI/AAAAAAAABXs/PUpVIC1zeRY/s0/[/IMG]

---

### Post by JKyleOKC on 2012-02-15
I don't know whether it's still true, but in past versions of Windows, it was absolutely required that the Windows system be in a primary partition, and its preferred position was at sda1. Your swap partition can be a logical one with absolutely no problem, as can both of the Linux system partitions.

I no longer dual boot (except for my seldom-used laptop) so my approach may not help you at all, but here's the setup I'm using on my main box here: ```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a20d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080       60181   434574315   83  Linux
/dev/sda3           60182       60801     4980150   82  Linux swap / Solaris

```I have the system at sda1, /home on sda2, and swap on sda3. The swap is almost 5 GiB (my RAM is 3 GiB) and is never used. My home directory contains quite a few virtual disk files, totaling more than 170 GiB, which is where I run my Windows applications, with a separate virtual machine for each group of apps.

Your needs will be considerably different, but this may help you get an idea of what can be done. The total size of your drive will have a lot to do with how you parcel it out, of course!

---

### Post by Blueyak on 2012-02-15
Hi!

You were asking what other people do in regards to partitioning.  I've set up Linux on a number of Windows netbooks at my home.  Usually, the netbooks come with either 3 or all 4 of the primary partitions already taken (Windows uses the extra partitions for various aspects of the system restoration process should one have to completely reinstall Windows on the netbook).  If all 4 primary partitions are already taken by Windows, I've had to delete one that isn't critical (i.e. HPTOOLS) and then use that one to make an extended partition that I can put Linux on.  Then I make 3 logical partitions (ext4 file system) under the extended partition.  I use gparted to resize the windows partition to what I need (i.e. 180GB of a 500GB drive so I can use the Windows for games and a few things).  I used to set the root partition as the first logical one which made it right beside the Windows one.  But if I later want to resize my home partition (i.e. take some GB from the Windows partition and give it to my home partition), this is easier if the home partition is next to the Windows partition.  After the home partition, I use the next logical partition for the root (about 20GB), and then the last logical partition for the swap (about 4GB or twice as much as my RAM).  The size of the home partition is whatever is left over after the 180GB Windows partition, the 20GB root partition and the 4GB swap.  With a 500GB hard drive, that was a little under 300GB.

---

### Post by ubni on 2012-02-16
> **Blueyak said:**
> Hi!

You were asking what other people do in regards to partitioning.  I've set up Linux on a number of Windows netbooks at my home.  Usually, the netbooks come with either 3 or all 4 of the primary partitions already taken (Windows uses the extra partitions for various aspects of the system restoration process should one have to completely reinstall Windows on the netbook).  If all 4 primary partitions are already taken by Windows, I've had to delete one that isn't critical (i.e. HPTOOLS) and then use that one to make an extended partition that I can put Linux on.  Then I make 3 logical partitions (ext4 file system) under the extended partition.  I use gparted to resize the windows partition to what I need (i.e. 180GB of a 500GB drive so I can use the Windows for games and a few things).  I used to set the root partition as the first logical one which made it right beside the Windows one.  But if I later want to resize my home partition (i.e. take some GB from the Windows partition and give it to my home partition), this is easier if the home partition is next to the Windows partition.  After the home partition, I use the next logical partition for the root (about 20GB), and then the last logical partition for the swap (about 4GB or twice as much as my RAM).  The size of the home partition is whatever is left over after the 180GB Windows partition, the 20GB root partition and the 4GB swap.  With a 500GB hard drive, that was a little under 300GB.

Can you make a screenshot of the the partitioning you use in GParted or something else please?

---

### Post by oldfred on 2012-02-16
I posted my laptop in your old thread before you created this new one.

This is my sdc drive. I have Windows in sda1, so it is not quite the same. You will see a lot of system partitions and two data partitions, one NTFS and one ext3.

---

### Post by ubni on 2012-02-16
The old thread is about 2 OS, this is about 2 and more, hence I made the new one and deleted the reply I originally posted and made a new thread. It did not fit the topic description any more. Only reason I made this one. Sure if you like to merge them please do so, but I think this one really is about 2 and more OS on one HDD.

Considering this theory is based on one HDD I have come up with the following:

[IMG]https://lh4.googleusercontent.com/-OP3ic34LjC0/Tz2Gqqo41LI/AAAAAAAABYE/0ab7rYP9vb4/s0/[/IMG]

By now I also know Windows has to be sda1 and there is no need for a separate /boot partition since GRUB 2 is loaded first in the MBR (Master Boot Record) and can access the various /boot sections of the corresponding /root to boot the OS. This is at least from what I understand now. Please do correct me if I am wrong.

---

### Post by haqking on 2012-02-16
From a performance point of view, if swap is to be used (and i mean if the system will actually use it alot) then it is best to have it near the beginning of a drive, especially if it is a mechanical HDD and not a SSD

but depends on how much it is used really

---

### Post by ubni on 2012-02-16
Thanks for the screenshot. I think I have understood your setup except one point.

Why do you have sda2 as /shared? Is that in fact the /home?

Since using one /boot partition for multiple installs is not possible ([well it is but in different circumstances and for a much more advanced setup]("http://maketecheasier.com/quick-guide-to-linux-partition-schemes/2009/12/17") building custom kernels I think) what is it GRUB does then and how does one not end up with multiple GRUB menus and /boot partitions but just one menu?

After a quick look at the GRUB site I found this:

> "Briefly, a *boot loader* is the first software program that runs when a computer starts. It is responsible for loading and transferring control to the operating system *kernel* software (such as [the Hurd]("https://www.gnu.org/software/hurd/hurd.html") or Linux)." from [GRUB Intro]("https://www.gnu.org/software/grub/index.html")So GRUB 2 and /boot are have no need to be on separate partitions, right? I think now I get it!! Excuse me but you can see I am an absolute beginner. GRUB 2 is even before the first partition on the HDD,  if I am correct in the first 63 sectors of the actual HDD where the MBR, Master Boot Record resides? Or something similar?

If this is correct then it is sure advisable to have /root (or simply called "/") together with /boot and others and no need for extra partitions at this level of experience, right?

Then this only leaves /home that I definitely want to keep separate from /root or simply " /" to be able to not loose my settings when re-installing the OS as well as to store the OS image files done with Clonezilla for example.

Last thing left is Swap and Data.

Here is another graphical draft. I hope I don't annoy you with those graphics, I find them tremendously helpful for understanding what I am going to to. Perhaps they help other beginners too.

Note this is only a dual boot partitioning scheme. Linux and Windows on one HDD.

[IMG]https://lh5.googleusercontent.com/-yk0-d1woV6A/Tz2LNRxaENI/AAAAAAAABYw/gM0IZpo7kOc/s0/[/IMG]

---

### Post by ubni on 2012-02-16
> **haqking said:**
> From a performance point of view, if swap is to be used (and i mean if the system will actually use it alot) then it is best to have it near the beginning of a drive, especially if it is a mechanical HDD and not a SSD

but depends on how much it is used really

This is what is also written [in the book I have]("http://openbook.galileocomputing.de/ubuntu/") but can Swap be sda1? Does Windows not occupy this spot? I need to have Windows on the HDD and not in a virtual environment unfortunately, so that is why I put it in a partition. If I can squeeze Swap onto sda1 somehow let me know please.

Otherwise what you are saying is that Swap might be good on sda2? And move the rest further down? That would make sense, no?

On what condition does Swap get used a lot?

I would guess for audio or video processing, encoding video and for Suspend-to-Disk, so to speak standby for the Linux OS, no?

Thanks for your reply about the speed. I don't see many people mentioning it when it comes to partitioning. Perhaps not at beginner level, not sure. Thanks for the input!

---

### Post by ubni on 2012-02-16
What I forgot to ask was if my theory about GRUB 2 being inside the MBR accessing the various /boot partitions and Windows of the various corresponding OS is correct?? If I am fine on that I guess I have started to grasp the basics a little bit. Thanks.

---

### Post by haqking on 2012-02-16
> **ubni said:**
> This is what is also written [in the book I have]("http://openbook.galileocomputing.de/ubuntu/") but can Swap be sda1? Does Windows not occupy this spot? I need to have Windows on the HDD and not in a virtual environment unfortunately, so that is why I put it in a partition. If I can squeeze Swap onto sda1 somehow let me know please.

Otherwise what you are saying is that Swap might be good on sda2? And move the rest further down? That would make sense, no?

On what condition does Swap get used a lot?

I would guess for audio or video processing, encoding video and for Suspend-to-Disk, so to speak standby for the Linux OS, no?

Thanks for your reply about the speed. I don't see many people mentioning it when it comes to partitioning. Perhaps not at beginner level, not sure. Thanks for the input!

the swap partition can be anywhere you like (preferably at the beginning of the disk, on a fast disk and preferably a seperate disk to the OS (if it is to be used alot)

Swap gets used when not enough memory, however this is not the only reason so even if you have lots of memory always good idea to have some swap IMO (though it is often debated)

I have 16Gb Ram so i use x.5 swap (as i dont need hibernation on my main system) and on my laptops with lesser ram i tend to use same size +1 or double the amount.

Swap is used not for just big programs but also sometimes for sleeping processes.

bootloader files for windows need to be on a primary, but windows itself can be installed on a logical partition, the boot.ini has ARC naming to point to locations similar to grub and lilo, windows install does not support logical creation for installtion though, so you need to make them first, install to the logical and then edit boot.ini to point to correct location

---

### Post by cariboo on 2012-02-16
Merged two threads on the same subject.

---

### Post by mazato on 2012-02-16
> **ubni said:**
> 

On what condition does Swap get used a lot?



Swap gets used  when memory is low, this usually happens when running RAM hungry apps like video editing applications, when there are memory leaks in an application and some other reasons.

---

### Post by haqking on 2012-02-16
> **mazato said:**
> Swap gets used  when memory is low, this usually happens when running RAM hungry apps like video editing applications, when there are memory leaks in an application and some other reasons.

not always just for low memory.

It can be used to swap out pages that are no longer needed by an application such as initialisation processes or sleeping processes

also you can use a swap file as well as a partition

oh and of course from 2.6 kernel you can also tweak the swappiness ;-)

---

### Post by mazato on 2012-02-16
> **haqking said:**
> not always just for low memory.

It can be used to swap out pages that are no longer needed by an application such as initialisation processes or sleeping processes


a process called paging :b

> **haqking said:**
>  also you can use a swap file as well as a partition 

also you  can set your swap among several disks to increase performance

> **haqking said:**
>  oh and of course from 2.6 kernel you can also tweak the swappiness 

aaaaahhhhhhhhh, sweet swappinnes, this is why I love my kernel!

---

### Post by Blueyak on 2012-02-16
> **ubni said:**
> Can you make a screenshot of the the partitioning you use in GParted or something else please?

Sure... the following is a screenshot of gparted showing my current partitioning.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212819&stc=1&d=1329445164[/IMG]

sda1 and sda2 are both partitions reserved by Windows for a system restore.  sda3 is my working Windows partition.  sda4 is my extended partition for Linux (it's encrypted).  Logical partition sda5 is my Linux home partition.  Logical partition sda6 is my Linux root partition.  And logical partition sda7 is my Linux swap partition.

---

### Post by shizz on 2012-03-08
Hi guys, great thread. Just wondering, What's the benefit of having the /home in a separate partition and not just linking the folder to the DATA partition?

Currently I have a DATA partition which I use for all of the User folders in windows, like My documents etc. I have also linked the Documents folder, music, pictures etc. that are in my Ubuntu home to these same folders in the DATA partition. This way I can easily access files in both operating systems.

Is there a big benefit in keeping them separate? Or can I say mount the /home in a separate partition but still link those folders to the DATA partition? Would this be a good Idea?

---

### Post by oldfred on 2012-03-09
I suggest a separate /home for new users so data is separate and new clean installs is a bit easier. It is just a start on separating data from system. But then a more advanced configuration is to have separate data partition(s). You do have to understand partitioning and mounting a data partition. Then also linking or bind to show data folders in /home. Whether /home is another partition or not then is less important. My /home is so small as I aggressively move all data including some of the hidden folders to my data partition that I keep it in my / (root). Others may have different opinions. :)

---

### Post by shizz on 2012-03-09
> **oldfred said:**
> I suggest a separate /home for new users so data is separate and new clean installs is a bit easier. It is just a start on separating data from system. But then a more advanced configuration is to have separate data partition(s). You do have to understand partitioning and mounting a data partition. Then also linking or bind to show data folders in /home. Whether /home is another partition or not then is less important. My /home is so small as I aggressively move all data including some of the hidden folders to my data partition that I keep it in my / (root). Others may have different opinions. :)

Is the /home where applications are installed? I don't think so just wondering. Also, if you have this home partition and then say re-install ubuntu and you designate this partition as /home, will the installation over write the partition and start new or leave it as is but link to it as the /home in the system?

---

### Post by oldfred on 2012-03-09
If you have installed a lot of apps you should export a list with dpkg or synaptic.

The /home has all your apps settings as well as your data unless you have moved it elsewhere. New install, if you do not reformat, will then reuse all the old settings. New apps my update some settings for a new version, so you cannot always try to reinstall or reuse a newer /home  in an older version. Backups then are still important.

---

### Post by shizz on 2012-03-09
ok so what I gather from what you said is that when reinstalling, it's fine to direct the OS to your /home partition but obviously backup in case anything goes wrong.

This sounds like a good idea, I might try it out in April, but I do like completely sharing the DATA partition between both OS's. Can you think of anything that could go wrong with that set up?

---

### Post by oldfred on 2012-03-09
I just install a new / (root) since I have room on my drive. I only copy some settings from /home from my old install to my new and can still boot into my old install in case I miss something.  My new 60GB SSD have two 30GB partitions, so I can alternate installs. And I still have /mnt/data & /mnt/shared on my rotating drives.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by ubni on 2012-06-03
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212819&stc=1&d=1329445164[/IMG]

Given this image of a partitioning scheme (thanks [Blueyak]("http://ubuntuforums.org/member.php?u=1187910")!) and wanting to have 2 Linux distros next to Windows all on one HDD I could do the following, no?

sda1 Primary NTSF 100MB System Reserved (Windows 7 needs this)
sda2 Primary NTSF  80GB Windows OS

sda3 EXTENDED     "theoretical"

sda4 LOGICAL NTSF DATA for Windows and both Linux distros

sda5 LOGICAL EXT4 ROOT of first Linux distro
sda6 LOGICAL EXT4 HOME of first Linux distro
sda7 LOGICAL LINUX-SWAP of first Linux distro

sda8 LOGICAL EXT4 ROOT of second Linux distro
sda9 LOGICAL EXT4 HOME of second Linux distro
sda10 LOGICAL LINUX-SWAP of second Linux distro

For now I won't care for the SWAP to be either at the end or the beginning of the HDD. I just really want to get going with this and think it can be done like that.

Please do correct me if this is wrong, since I would not really like to resize/change the partitioning once I have them filled with data or the installations.

I have read through this thread many times now and would hope for a green light with the above lined out scheme. What do you think?

Thanks for your help.

---

### Post by Miljet on 2012-06-04
> sda1 Primary NTSF 100MB System Reserved (Windows 7 needs this)
sda2 Primary NTSF 80GB Windows OS

sda3 EXTENDED "theoretical"

sda4 LOGICAL NTSF DATA for Windows and both Linux distros

sda5 LOGICAL EXT4 ROOT of first Linux distro
sda6 LOGICAL EXT4 HOME of first Linux distro
sda7 LOGICAL LINUX-SWAP of first Linux distro

sda8 LOGICAL EXT4 ROOT of second Linux distro
sda9 LOGICAL EXT4 HOME of second Linux distro
sda10 LOGICAL LINUX-SWAP of second Linux dissda1 

You are getting very close.

You do not need more than one swap partition. You can have ten different Linux versions installed and they will all use the same swap.

Your numbering scheme is slightly off. You will not have an sda4 if sda3 is your extended partition. As has been mentioned previously, logical partition numbers always begin with sdX5. So what you are showing as sda4 will actually be sda5, sda5 will be sda6, and so forth.

---

### Post by ubni on 2012-06-04
Wicked!! Thanks for your reply!!

Yes once I hit Apply in GParted I saw that my numbering is a bit off. 

I can still change the partitions and double the amount of Swap towards the end of the HDD or add more space to the HOME partitions.

**To confirm about space**:
I gave HOME and ROOT each 10GB and SWAP 4GB.

However SWAP will now either be 8GB total merging the two SWAP partitions or spreading the other 4GB to each HOME1&2 and ROOT1&2. I tend to simply double the SWAP partition and leave 10GB for each HOME1&2 and ROOT1&2 instead of giving 1GB more to each of those. So 10GB should be enough for ROOT, HOME and 8 GB for SWAP, right?

**To confirm about GRUB2**:
GRUB2 is (or will be once installed) located in the first 63 sectors of the disk sorting the booting of the various OS out, so I won't need a partition for it, right?

**GParted Screenshot:**
Last not least, GParted saved a screenshot of the HDD once I did the partitioning to Home/User/.. how can I access that Dir from Windows? Would love to upload my GParted screenshot here as well or will this only be available once I have installed the Linux distros?

---

### Post by oldfred on 2012-06-04
If you are only giving 10GB each to / & /home I would not make them separate. Most of your data should be in the shared NTFS data partition so all systems can see it. And you will have some unused space in both / & /home so sharing the unused will work better as you will not be sure which may fill up first.

You cannot access info stored in LInux partitions from Windows. There were some drivers but I would not use them.  Just save data to the NTFS shared partition.

You actually do not want to use swap as it is 10+ times slower than RAM. So if you have a fair amount of RAM you may never use it, but If you load a lot of programs  and only have 1 or 2GB RAM then you may occasionally use swap, but will notice system slowing down.

---

### Post by ubni on 2012-06-04
> **oldfred said:**
> If you are only giving 10GB each to / & /home I would not make them separate. Most of your data should be in the shared NTFS data partition so all systems can see it. And you will have some unused space in both / & /home so sharing the unused will work better as you will not be sure which may fill up first.

Thank you for your reply. When you say data in the context above you surly mean personal data, photos, videos, documents but **not** applications (install files), application settings, configuration files, user setting files etc right?

I am asking since I clearly want to separate the system files in / and /home from the user data (word documents, photos, videos etc), so having / and /home together in one 20GB partition would still work? How can I then separate the Linux user settings from the Linux distro install if they are not on two separate partitions?

I thought the / is for the pure install and the Linux user settings are kept in the /home, so when I want to re-install a dirsto I can simply copy my settings back over from /home to / no? This is why I wanted to have separate / and /home partitions and this is also what people in this thread have been saying so far, no?

This leads me to this reply from you:
> **oldfred said:**
> If planning multiple / (root) partitions for multiple installs it may be  better to keep /home inside the root partition and just have one data  partition. Then the data is easily shared if distributions are in the  same family (all Debian) or are configured with UID & GIDs at are  the 1000 as Ubuntu uses.
What data do you mean when you refer to data in this above quote please? Is this the user settings, installation, configuration files for the distro? I think again here you mean personal data like documents, photos and video rather then Linux distro specific user setting files, right? So is it still a good idea to keep the user setting files and the Linux install OS files in one partition? What if I want to re-install that distro but don't want to loose the user settings for the distro? They will be gone if I install over it, this is really the reason I thought having / and /home on separate partitions give me the advantage of not loosing my settings. Note I am not speaking about personal data, documents, photos and video files here, all those will be share between the Linux distros and the Windows OS on the huge Logical NTFS partition. That is also the partition that makes up the biggest space on the HDD so far.

> **oldfred said:**
> 
You cannot access info stored in LInux partitions from Windows. There were some drivers but I would not use them.  Just save data to the NTFS shared partition.
How do I tell GParted run from a live CD to save it to another partition than /home/user? I think it does that automatically somehow. Where could I change the setting for that please?

> **oldfred said:**
> 
You actually do not want to use swap as it is 10+ times slower than RAM. So if you have a fair amount of RAM you may never use it, but If you load a lot of programs  and only have 1 or 2GB RAM then you may occasionally use swap, but will notice system slowing down.
Since I have 8GB RAM I will ditch the SWAP altogether then. Thanks for letting me know about all this!!

Again from your very informative reply new questions arose, I hope with your help I can clear those last few bits and start installing the Linux distros soon.

Thank you.

---

### Post by oldfred on 2012-06-04
Data is the Documents, Video, Photos etc that are not Ubuntu settings. I also include some larger application data that may include some settings like Firefox profile, Thunderbird profile and a few other data files that applications put in . (hidden) files or folders. 

Then my /home really only has the user setting (primarily Ubuntu) for running the system and is very small, easily backed up. I usually do not copy much of those settings to my new install but do copy some of the application settings that did not have enough data to copy into my data partitions.

I have serveal Ubuntu installs all in about 25GB with about 7GB used including /home. My /home is larger as it is over 1GB with .wine which I understand is a bit more difficult to move, so I have not moved it.

Some have not swap and system works. Some have said a bit of swap speeds booting slightly as it looks for swap and has to timeout on not finding it. Some just create swap as a file inside /.

My / include /home. My shared is my NTFS that I used to use a lot with XP and still has Firefox & Thunderbird profiles & all photos for Picasa. All new data goes into my /mnt/data and all folders from /mnt/data are linked into /home.

```
fred@fred-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde3        28G  7.6G   19G  29% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M 1016K  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  124K  2.0G   1% /run/shm
/dev/sda1        55G   36G   20G  64% /mnt/cdrive
/dev/sdd2       100G   28G   72G  29% /mnt/shared
/dev/sdd6        97G   41G   51G  45% /mnt/data

```

These are the folders I have in /mnt/data

fred@fred-Precise:/mnt/data$ ls
Calibre Library  gnu           ISO       lost+found       Pictures    workspace
Documents        google-earth  itrade    Music            Projects
Downloads        grampsdb      jstock    PDF              spyderdata
eclipsetrader    icarra2       kmymoney  PicasaDocuments  Videos

And all are linked to my /home with one command. I do have to delete the one's with the same name like Video or Document first. I do that as soon as I install so I know the folders are empty.
for i in `echo /mnt/data/*`;do ln -s $i; done


Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

