---
title: "Struggling to understand partitions and bootloaders"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by ukchris on 2012-03-18
Hello folks. :)

I have recently been playing with Ubuntu and it runs a little slow on this tired old laptop so I decided I wanted to try Lubuntu on a separate partition.

Before the install I had:

/dev/sda (120GB);
/dev/sda1 (20GB) - Windows restore partitions;
/dev/sda2 (70GB) - Ubuntu working install & contains Grub bootloader;
/dev/sda4 (2GB) - Swap file used by the above - no idea at the time why it was marked as sda 4 and not sda3;
empty space (28GB) - left for a second test install of a light weight Ubuntu variant.

When I boot the machine I get a manufacturers splash screen that allows me to enter the recover partition, then if left I go to the Grub bootloader and the top option is my Ubuntu OS.

I had left some spare space on the HDD for this purpose so I went ahead and started the install of Lubuntu from a USB stick.

I used the "Something else" option and created a 26GB EXT4 drive for Lubuntu (/dev/sda5) and a 2GB swap file for this install (/dev/sda6).  All were set as "Logical" and /dev/sda5 was set to mount at /.

I wasn't sure what to do with the bootloader so working on the assumption I had with the original install I put it on /dev/sda5 (i.e. where the OS will be).  When I rebooted the machine I got the splash and then Grub but with nothing additional options so I knew I had made a mistake (original Ubuntu install worked fine) and sort of understood why (first bootloader can only load an OS it knows about and not another bootloader on another drive).

So I did the same install again (after deleting and re-creating the relevant partitions) but put the Bootloader on /dev/sda2 and on re-boot I now had additional options for Lubuntu and I could boot into this or Ubuntu correctly.

However, on Grub the Lubuntu install is labelled Ubuntu rather than Lubuntu and sits at the top of the list (with the original install of Ubuntu at the bottom).  Is it possible to amend this/customise Grub so Ubuntu is option 1, Lubuntu is option 2 and then the safe mode options are below this?

I also have a related issue.  Now when I boot into Ubuntu I can see the Lubuntu partition as an additional drive and access the Lubuntu install Home folders.  Is this because I made /sda5 a logical drive?  Should I have used the other option and still mounted at /?

Generally related is the below, when I run sudo fdisk -l I get output that solves why the swap file for the Ubuntu set-up is /sda4 and not /sda3.  There is an /sda3 drive already there that is simply labelled "Extended".  What is this? Is it part of /sda2 and due to some kind of disk size limitation?

```
test@host-ub11-10:~$ sudo fdisk -l
[sudo] password for test: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    16370234     8185086   1b  Hidden W95 FAT32
/dev/sda2   *    16370235   172620234    78125000   83  Linux
/dev/sda3       172621822   234440703    30909441    5  Extended
/dev/sda5       172621824   176916479     2147328   82  Linux swap / Solaris
/dev/sda6       176918528   229847039    26464256   83  Linux
/dev/sda7       229849088   234440703     2295808   82  Linux swap / Solaris

```This is entirely a fresh test install so I have no problems starting again however I must always be careful to leave /sda1 and the manufacturer boot as it is. :)

Thanks in advance for any help.

---

### Post by oldfred on 2012-03-18
With MBR partitioning you can only have 4 primary partitions. This is the same partitioning used on the first hard drives with early PCs. But they realized 4 partitions was not enough so they let you make one and only one primary partition an extended partition. It is just a container for all the logicals which you can have many of. Windows first install (and all later installs) have to boot from the primary partition with the boot flag. Grub does not use boot flag and can boot from logical partitions.

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

With MBR partitioning you have the first sector of the hard drive that is the MBR or master boot record. It has a little bit of boot code that BIOS jumps to and the partition table. The MBR then redirects to added boot code elsewhere. With multiple systems your boot loader boots one system and with grub you can then choose others to boot.

Since only one system can be in the MBR you can boot into your other system and reinstall its copy to grub2's boot loader to the MBR of drive sda (or other drives if present). 

```
sudo grub-install /dev/sda
```And if you have installed another system this will search system and add them to the menu. Which ever install you boot then will be first in the menu.

```
sudo update-grub
```You should not need two swaps as each install can use the same swap unless you hibernate. And you do not have to reinstall to update boot loaders, you can use liveCD to update grub.

One of the better tools for repairs it this. I like to have a liveCD or USB for the current version of every install and one or two other repair tools.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Jake5 on 2012-03-18
Sorry, not much help from me, but I do believe that the second linux swap partition is not needed. About 95% sure that any linux distro should recognize the swap partition and use it as it needs to. I have ubu and lubu on my laptop now, and all I did was a standard side by side install, I don't have a third OS though and that could be whats tripping you up somehow, not sure how though. Hope someone more knowledgeable comes by soon! I will keep an eye on this thread to see what I can learn.

---

### Post by SuaSwe on 2012-03-18
In reference to the boot order question, having a look at the community documentation covering [GRUB2]("https://help.ubuntu.com/community/Grub2"), assuming this is what you have running, what you'd do to change the order/name/default OS in the boot file is to manipulate custom scripts within /etc/grub.d/. :)

---

### Post by ukchris on 2012-03-18
Thanks for your replies folks.  :)

> **oldfred said:**
> But they realized 4 partitions was not enough so they let you make one and only one primary partition an extended partition. It is just a container for all the logicals which you can have many of.

Windows first install (and all later installs) have to boot from the primary partition with the boot flag. Grub does not use boot flag and can boot from logical partitions.

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

With MBR partitioning you have the first sector of the hard drive that is the MBR or master boot record. It has a little bit of boot code that BIOS jumps to and the partition table. The MBR then redirects to added boot code elsewhere. With multiple systems your boot loader boots one system and with grub you can then choose others to boot.

First of all, thanks Fred for the links they were very helpful in giving me some understanding of the theories behind partitioning and bootloaders.

I am still trying though to apply this practically and I'm afraid I have some follow ups, sorry for the basic level I'm shooting at here. :)

Would it be fair to say the following about my system:

1) The MBR is /dev/sda;
2) This MBR controls the manufacturer boot process that allows me to access BIOS settings/boot from alternate devices;
3) This MBR bootloader then tries to loads /dev/sda2 (as sda1 is a restore partition listed as an alternative boot device on the manufacturer boot screen);
4) The first thing /sda2 does is load Grub2 which then allows me to load /sda1 or /sda2 or /sda4 (and all the relevant recovery/safe systems)?

> **oldfred said:**
>  Since only one system can be in the MBR you can boot into your other system and reinstall its copy to grub2's boot loader to the MBR of drive sda (or other drives if present).

```
sudo grub-install /dev/sda
```And if you have installed another system this will search system and add them to the menu. Which ever install you boot then will be first in the menu.

```
sudo update-grub
```

So you are saying that I would have been placed to - during install - place the bootloader on /dev/sda?  Which is the very root of the entire drive?

This machine will ultimately need to be returned into a factory fresh state soI would like to avoid touching the manufacturer boot process at all.  Given this - and what you all say re. 4 drives but not needing the second swap - what is the best thing to do?

I am thinking:

1) /dev/sda - leave alone entirely (this presumably doesn't count as a partition?);
2) /dev/sda1 - leave as Windows recovery partition;
3) /dev/sda2 - Grub2 + main Linux OS;
4) /dev/sda3 - Secondary Linux OS;
5) /dev/sda4 - Shared swap.

Is the above sensible? And if it is should /sda2 and /sda3 be "Primary" or "Logical"?

Or could I have a small /sda2 that just has the Grub2 bootloader on (sort of MBR2) with the other required drive logical drives under this?

> **oldfred said:**
>  One of the better tools for repairs it this. I like to have a liveCD or USB for the current version of every install and one or two other repair tools.

I have kept a USB stick with the Ubuntu install on, what can I say I'm a belt and braces kind of guy.   :)

> **oldfred said:**
>  Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.
 
Option 2 seems like it creates a diagnostic script of the current system, would this map my manufacturer boot AND Grub2 boot?

> **oldfred said:**
>  You should not need two swaps as each install can use the same swap  unless you hibernate. And you do not have to reinstall to update boot  loaders, you can use liveCD to update grub.

> **Jake5 said:**
> About 95% sure that any linux distro should recognize the swap partition and use it as it needs to.

Thanks guys.  This, if my assumptions above are correct will keep me at 4 partitions and save me 2GB on a system where HDD space is limited.  :)

> **Jake5 said:**
> Sorry, not much help from me...

Jake, it will be a while before I can add anything bar questions to a thread here so I think you have already achieved something my friend. :biggrin:

> **Jake5 said:**
> I have ubu and lubu on my laptop now, and all I did was a  standard side by side install, I don't have a third OS though and that  could be whats tripping you up somehow, not sure how though. 

I think you're right, trying to keep the manufacturer stuff and the Windows recovery partition has thrown a spanner my understanding.  I think though that it's because I don't have a grasp on the fundamentals yet.  Trying though. :)

> **SuaSwe said:**
> In reference to the boot order question, having a look at the community documentation covering GRUB2, assuming this is what you have running, what you'd do to change the order/name/default OS in the boot file is to manipulate custom scripts within /etc/grub.d/. 

Thanks for this link SuaSwe, I will take some time going through this and getting the menus in the right order when I have an install I am happy with.  It looks fairly in depth so I'm thinking a Sunday night after a beverage might not be the best time to get stuck in! :P

Thanks again everyone.

---

### Post by oldfred on 2012-03-18
I am not sure how you are booting. Some have put grub2's boot loader into a partition (which is not recommended) and used the Windows boot loader in the MBR which just jumps to the PBR or partition boot sector. That is how Windows boots, but grub does not need code in the PBR.

The MBR does not call BIOS, but BIOS jumps to MBR to boot. To get to BIOS you usually have to press some key often {delete}, but sometimes some other key. Either first BIOS screen or motherboard/system manual should tell you.

The MBR is just the first sector of a hard drive. Partitions often start many sectors later so some more boot code, DRM software, Windows softwar keys etc can be in the "unused" space from the first sector until the first partition.

Some info on how MBR system boot primarily Windows. Article has lots of detail but pictures give a good overview.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by ukchris on 2012-03-18
Thanks Fred.  So I think the initial boot screen shown in the first screen shot below would remain in place if I place Grub2 on /sda?

1. Manufacturer screen, gives access to BIOS, recovery partition (/sda1) and boot menu to allow boots from USB etc.

[IMG]http://i44.tinypic.com/2zyy69d.png[/IMG]

2. Boot device menu.

[IMG]http://i39.tinypic.com/smf0j4.png[/IMG]

3. Grub2, top options are Lubuntu, bottom are Ubuntu.

[IMG]http://i40.tinypic.com/iymrr9.png[/IMG]

Does this help explain any more?  I essentially want to ensure I have 1 and 2 and the Windows line of 3 (on sda1) regardless of what I do to the rest of 3.  :)

Thanks.

---

### Post by oldfred on 2012-03-19
there have been a few computers with customized MBR that the computer vendor users to do something. The first screens you see are from BIOS.

If you want to see what is in your MBR this will show your entrie configuration. Just run the boot_info script. You can download into your install, into the Ubuntu liveCD, or download its own liveCD. Often good to have a repairCD handy as well as the current version Ubuntu liveCD to make repairs. 

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by ukchris on 2012-03-19
Hi again Fred.  I have had the time now to go through the multiboot article you posted and think I have probably done the right thing initially and installed Grub on the Linux partition itself.    

[quote=Multibooters, Vista Dual and Multibooting - A guide to the Multiboot Process]Linux and Lilo/Grub  

When you install Linux you will usually get an option during setup of where to place Lilo or Grub. The choices will include to the MBR of the boot hard drive or to the Linux partition. If you choose the MBR then part of Lilo/Grub will replace the Microsoft IPL and the other part will remain on the Linux partition and be configured to operate as a bootmanager for the other OSes on the computer. If you already have a Windows dual/multiboot using the Microsoft bootmanager then Linux may only add the Windows system partition to its boot menu. If you have various independent Windows installs you may still have to add most of them yourself to the Linux bootmanager.    

**If you instead choose to have Lilo or Grub installed entirely to the Linux partition then you can use your preferred bootmanager to start Linux by way of its own PBR, in exactly the same way as you start independent Windows by their PBRs. It's a cleaner method of doing things and also removes the certainty of breaking the boot sequence chain to your Windows OSes if you later decide to reinstall or remove the Linux OS. Unlike Windows an independent Linux install will not overwrite your MBR bootmanager.**[/quote]

I have also looked a little further into Primary/Logical partitions and  I think when I do a re-install I will do the following:

1) /dev/sda - leave alone entirely (this presumably doesn't count as a partition?);
2) /dev/sda1 - leave as Windows recovery partition;
3) /dev/sda2 - Grub2 + main Linux OS - _Primary Partition_;
4) /dev/sda3 - Secondary Linux OS  - _Primary Partition_;
5) /dev/sda4 - Shared swap - _Primary Partition_.

Will this work?  As the two Linux OS' are to be on primary this should stop me being able to see the Lubuntu docs when using Ubuntu and vice versa.  Does this mean I need two swap partitions, one as a logical partition of the primary OS and one as a logical partition of the secondary OS or does the "any Linux OS can share the same swap" comment remain true even when using a primary partition?

Thanks.  :)

With regards to the Boot-Repair link I will have a look at this when I get in from work and see if I can get some helpful output.

Thanks again Fred (and all).  :biggrin:

---

### Post by oldfred on 2012-03-19
I do not like using all 4 primary partitions, but you can. You just could not create any more logical partitions as you have to have one primary to be the extended as a container for the logical. Default installs usually create the swap as a logical so then you at least have some flexibility. But moving partitions around can be slow and somewhat risky as a power failure in the middle creates huge issues.

Linux uses primary or logical the same, so what ever issue you are having with versions is not related to partition type.

Only if hibernating (which, with dual boot I do not recommend anyway) would you need two swaps.

With dual boots I find I want to share some data files. So I often keep / (root) partitions smaller even with /home included (10 to 25GB) and put all data into a data partition that I can mount and use in both installs.

---

### Post by ukchris on 2012-03-19
Wow Fred, thanks. :)

> **oldfred said:**
> Linux uses primary or logical the same, so what ever issue you are having with versions is not related to partition type.

OK, so I'll install each OS to a logical partition with one logical Swap.  Does it matter where this swap is?  Between OS or just at the end of the drive?

> **oldfred said:**
> Only if hibernating (which, with dual boot I do not recommend anyway) would you need two swaps.

Is this [non-recommendation] in case you restart from hibernation and go into a different OS than the one you hibernated from?

> **oldfred said:**
>  With dual boots I find I want to share some data files. So I often keep / (root) partitions smaller even with /home included (10 to 25GB) and put all data into a data partition that I can mount and use in both installs.

That's a fabulous idea, how do I go about this and is there a quick way of finding out the minimum required HDD space for each OS?  

As I am likely to be playing around with a number of installs would it be best to create my data partition at the beginning of the drive (after /sda1 but before the current /sda2) so OS space can more easily be re-configured?

Or am I too worried about this stuff?? :p

Thanks for your patience and sorry for all the questions, I just like to understand why I am doing this stuff.

---

### Post by oldfred on 2012-03-19
I find Ubuntu usually boots so fast that hibernation does not save much. But the RAM memory is saved to swap, so if you boot the other install you may overwrite swap and damage the hibernation.

I use 20 to 25GB for my installs and add a lot of software. My /home is between 1 and 2GB with almost all of that .wine with Picasa. My total / with /home is about 7GB. But, I am aggressive about moving any data, the obvious Music, Docs folders, etc, but also most of the hidden .mozilla, .thunderbird (actually the profile folders) and others that have a fair amount of data. I share Filefox & Thunderbird profiles across XP & several Ubuntus. But you may need another temporary 4GB in /tmp if you want to write a DVD backup for example. So some extra is recommended.

Some discuss rotation speeds of drives of inside tracks vs. outside tracks. That is so small in most cases that I just install partitions where ever I have them.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by ukchris on 2012-03-19
Thanks man, lot's to play with tonight.  Mrs is going to hate me. :)

---

