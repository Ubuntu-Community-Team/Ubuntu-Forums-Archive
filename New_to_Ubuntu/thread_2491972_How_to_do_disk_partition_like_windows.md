---
title: "How to do disk partition like windows?"
date: 2023-10-26
forum: New to Ubuntu
---

### Post by laxmidhar on 2023-10-26
Hi,
I am new to Ubuntu. I am using an HP laptop which has 512 GiB SSD. Just wanted to do the disk partition like windows. The entire OS will be in one partition and other two for the study material and media.
So someone can please guide me how can i do this. Is there any app or what are the commands for the entire process.
Please guide me.


Thanking you in advance.

---

### Post by TheFu on 2023-10-26
You can also use the Ubuntu installer "do something else" option.  Setting up the partitioning with a single partition for the OS files has negative security aspects.  There are many threads in these forums where other users have asked a similar question. Have you reviewed those to learn some of the options?

There are hundreds of guides on the internet for using **gparted**. Gparted is the best, easiest, way to setup partitions for Linux, but it isn't guided. It is expected that the admin would know what they need/want and would setup those things.  Also, gparted isn't available as part of the installer, so what people do is boot into a Live Boot environment, partition the device they plan to install into, then use the normal installer, choose "do something else" and connect the partitions we created to the different parts of the OS for installation.  Without some reading, going into any detail now would just be confusing.

For non-trivial setups, there are other methods. I use a custom script to setup my new systems, but this is far from the poor-security setup you are requesting.

As with most things, there are trade-offs with every choice/option.  Simple has ramifications.  Complex has ramifications.  Only you can decide.  I suppose one of the biggest complaints with Linux is all the options and that nobody wants to tell you THE answer. That's because there isn't 1 answer.  There are 50+ answers, depending on your needs. oldfred has a number of posts in these forums concerning partitioning and disk layouts.

Partitions, Device Names, explained:
[Https://ubuntuforums.org/showthread.php?t=2481638&p=14122012#post14122012](Https://ubuntuforums.org/showthread.php?t=2481638&p=14122012#post14122012)

A layout only:
[Https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](Https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987)

A layout with reasons why:
[Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)

More complex, [Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144)  This has encryption, manually created.

---

### Post by sudodus on 2023-10-26
+1 to the reply by TheFu.

I would also recommend that you learn how to use **gparted**.

- Please notice that you must unmount the partitions that you want to edit, and that you cannot unmount the partition(s) where you have the working operating system. For that reason it is a good idea to **boot from an external drive**, typically Ubuntu Desktop *live* in a USB drive.

- Please start this adventure by **backing up everything that you cannot afford to lose** to another drive or location. Editing partitions is risky.

---

### Post by grahammechanical on 2023-10-26
Do you want to share your data with a Microsoft Windows operating system? That will further complicate matters. If you do not then my advice would be - to get some experience with installing Ubuntu using the "Do something else" option. That is the easiest way to install Ubuntu. Do not put any data on it.

Then use the USB live session and GParted to practice shrinking; moving; expanding; creating and deleting partitions. If you mess up then you simply re-install Ubuntu.

I have three installs of Ubuntu on the same drive with another partition that I call Data. In that Data partition I have created folders that I keep my data in. I access the files on that Data partition and when I save the file it gets saved to its location on the Data partition. If I download a file or create a file in one of the installs of Ubuntu and I want to keep it safe, then I copy or move the file onto the Data partition.

Regards

---

### Post by laxmidhar on 2023-10-27
@TheFu
Thanks for the response.
Actually i search for the question but i got confused which one to go which one not go that's why i created a thread.
Can you please guide me how can i do the partition using **gparted. **Just now i installed the[B]gparted.

[/B]Thanking you in advance.

---

### Post by Rubi1200 on 2023-10-27
From within Ubuntu or the liveUSB, open a terminal and run this command:
```
sudo fdisk -l
```

lower case L not i

Post the results back here using code tags please.

---

### Post by laxmidhar on 2023-10-27
Thanks for the response @Rubi1200
Below is the output after executing command.

```
sudo fdisk -l
[sudo] password for laxmidhar: 
Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 9.59 MiB, 10051584 bytes, 19632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 105.82 MiB, 110960640 bytes, 216720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 63.28 MiB, 66355200 bytes, 129600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 63.46 MiB, 66547712 bytes, 129976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 73.9 MiB, 77492224 bytes, 151352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 66.56 MiB, 69795840 bytes, 136320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 240.61 MiB, 252301312 bytes, 492776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: IM2P33F8-512GD4                         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6CBC3BD7-2FA3-4A13-9F0A-439C6AA249C5

Device            Start        End   Sectors   Size Type
/dev/nvme0n1p1     2048    1050623   1048576   512M Microsoft basic data
/dev/nvme0n1p2  1050624   11290623  10240000   4.9G Linux filesystem
/dev/nvme0n1p3 11290624   12335103   1044480   510M Linux swap
/dev/nvme0n1p4 12335104   13385727   1050624   513M EFI System
/dev/nvme0n1p5 13385728 1000214527 986828800 470.6G Linux filesystem


Disk /dev/loop8: 240.32 MiB, 251994112 bytes, 492176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 346.33 MiB, 363151360 bytes, 709280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 349.7 MiB, 366682112 bytes, 716176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 496.98 MiB, 521121792 bytes, 1017816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 45.93 MiB, 48160768 bytes, 94064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 12.32 MiB, 12922880 bytes, 25240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 49.84 MiB, 52260864 bytes, 102072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 40.86 MiB, 42840064 bytes, 83672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 304 KiB, 311296 bytes, 608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 452 KiB, 462848 bytes, 904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

---

### Post by laxmidhar on 2023-10-27
I was wondering how these many partition is there.
Wanted to know if i install any application then in which partition it will store.
Because i don't want to store media and study related stuff in OS drive.
Please guide me how to do?

---

### Post by sudodus on 2023-10-27
The loop devices are probably 'only' for snaps, not physical drives and/or partitions.

This is the relevant drive with its partitions:

```

Disk /dev/nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: IM2P33F8-512GD4                         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6CBC3BD7-2FA3-4A13-9F0A-439C6AA249C5

Device            Start        End   Sectors   Size Type
/dev/nvme0n1p1     2048    1050623   1048576   512M Microsoft basic data
/dev/nvme0n1p2  1050624   11290623  10240000   4.9G Linux filesystem
/dev/nvme0n1p3 11290624   12335103   1044480   510M Linux swap
/dev/nvme0n1p4 12335104   13385727   1050624   513M EFI System
/dev/nvme0n1p5 13385728 1000214527 986828800 470.6G Linux filesystem

```
But it does not show much about the content. Please run the following commands and show them plus their output:
```

df -h

lsblk -e7 -o model,name,fstype,size,fsavail,fsuse%,label,mountpoints

```

---

### Post by Impavidus on 2023-10-27
Ubuntu isn't like Windows and partitioning in Ubuntu isn't like partitioning in Windows. In Windows (IIRC, I haven't used Windows in ages), files for your applications get sorted per application. In Ubuntu, they get sorted by usage pattern. And there's no sharp distinction between OS and applications. So, the executables for your applications are stored alongside the low-level tools and things like the Window manager; the graphics files of a game are stored alongside the icons of some settings manager.

Gparted isn't included in the installed system (but you can install it, as you did) because it's only useful to partition external drives. That is because you cannot change a mounted partition and you cannot unmount the root partition of the currently running OS. So, to change the partition of the OS, you boot from a live disk and use the gparted of that system.

Having said all that, yes, you can put your personal files or your media files on a separate partition. The default these days is to put everything in one big partition (+the EFI partition), but you can arrange things differently, with just a few constraints. It's common to put /home (with all your personal documents and settings) in a separate partition, or just make a partition for your documents or for your media files. Make a directory to use as a mountpoint and modify your /etc/fstab to mount it automatically at boot time. For a /home partition, the installer can do it for you. Just tell it to use /home as a mountpoint.

Those /dev/loop* devices in your output aren't real. Only the /dev/nvme* are. Those are peculiar though: alongside the big Linux filesystem and the EFI partition (which are normal), you've got a small swap partition, another small Linux partition and one tiny Windows partition.

---

### Post by yancek on 2023-10-27
Your fdisk output seems a bit unusual as a current standard preinstalled windows will have the primary system partition as well as a 'reserved' and 'recovery' partition.  That isn't a problem, just a bit unusual.  Current Ubuntu installations don't generally create a 'swap' partition but use a swap file.  That also is not a problem.  The largest partition (/dev/nvme0n1p5) is likely the filesystem partition.  I don't know what  ( /dev/nvme0n1p2) is as it is too small (4.9GB) to be a system partition for Ubuntu and would be pretty useless as a /home or data partition.  The EFI partition is used for boot files for both windows and Ubuntu and what is unusual is that it is partition 4.  Generally, it is the first partition but that also should not be a problem.

Mostly, applications installed will be install on the / (root) filesystem partition which in your case is partition 5.  If you want to personal data such as text files, images, musci, etc. separate yo can create a data or /home partition for that either on the same drive or a separate drive.  If you want that information accessible, you will need to always have the drive attached (if it is a secondary or external drive and will need an entry in the /etc/fstab file.

You indicate you do not want to store media and study stuff on the OS drive.  Are you referring to the system partition or to a separate physical drive?
If you mean on a separate partition on the same drive, it should be simple to shrink the / filesystem partition (partition 5) and create another partition for personal data.  As suggested above, the simplest way to do this is with the gparted software which is on the Ubuntu installation iso (DVD/USB) you used to install Ubuntu.  GParted has an online manual with detailed instructions on how to do this.  See the link below and if you have questions or don't understand something, stop and post your questions here.

 [https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by laxmidhar on 2023-10-27
Thanks for the response @sudodus

Below is the output from the command 'df -h'
```

df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1.5G  2.3M  1.5G   1% /run
/dev/nvme0n1p5  463G   13G  427G   3% /
tmpfs           7.5G     0  7.5G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p4  512M  7.0M  505M   2% /boot/efi
tmpfs           1.5G  1.7M  1.5G   1% /run/user/1000
/dev/nvme0n1p1  511M   24M  488M   5% /media/laxmidhar/A544-D3FB
/dev/nvme0n1p2  4.7G  4.1G  353M  93% /media/laxmidhar/e42d229f-bb34-460b-80cc-4b50fcdf1754
```

Below is the output from 'lsblk -e7 -o model,name,fstype,size,fsavail,fsuse%,label,mountpoints'
```

lsblk -e7 -o model,name,fstype,size,fsavail,fsuse%,label,mountpoints
MODEL           NAME        FSTYPE   SIZE FSAVAIL FSUSE% LABEL MOUNTPOINTS
IM2P33F8-512GD4 nvme0n1            476.9G                      
                &#9500;&#9472;nvme0n1p1 vfat     512M  487.2M     5%       /media/laxmidhar/A544-D3FB
                &#9500;&#9472;nvme0n1p2 ext4     4.9G  352.5M    87%       /media/laxmidhar/e42d229f-bb34-460b-80cc-4b50fcdf1754
                &#9500;&#9472;nvme0n1p3 swap     510M                      
                &#9500;&#9472;nvme0n1p4 vfat     513M    505M     1%       /boot/efi
                &#9492;&#9472;nvme0n1p5 ext4   470.6G  426.4G     3%       /var/snap/firefox/common/host-hunspell
```

Thanking you in advance

---

### Post by laxmidhar on 2023-10-27
Thanks for the response @[**[COLOR=#000000]yancek[/COLOR]**]("https://ubuntuforums.org/member.php?u=1928724")
Yes when i saw there is 5 partition i was also wandering.
I am not referring to any separate physical drive i am referring to the internal 512GiB SSD only.
What is think is if we keep our all the stuff in one then it might create confusion for us and it might create any problem for the OS. That's why i am thinking it is better to keep the OS and app in one partition and other two partition for Media and Study material.

---

### Post by TheFu on 2023-10-27
Too hard to read the **df** and **lsblk** output without code tags.  Fix that please in post #12 above.
Please don't make it hard to help you.

---

### Post by laxmidhar on 2023-10-27
Hi @The Fu
Thanks for the response.
As per your requirement i changed and additionally attached a screenshot for your reference.
Please guide me the next step.


Thanking you in advance.

---

### Post by TheFu on 2023-10-27
```
MODEL           NAME        FSTYPE   SIZE FSAVAIL FSUSE% LABEL MOUNTPOINTS
IM2P33F8-512GD4 nvme0n1            476.9G                      
                &#9500;&#9472;nvme0n1p1 vfat     512M  487.2M     5%       /media/laxmidhar/A544-D3FB
                &#9500;&#9472;nvme0n1p2 ext4     4.9G  352.5M    87%       /media/laxmidhar/e42d229f-bb34-460b-80cc-4b50fcdf1754
                &#9500;&#9472;nvme0n1p3 swap     510M                      
                &#9500;&#9472;nvme0n1p4 vfat     513M    505M     1%       /boot/efi
                &#9492;&#9472;nvme0n1p5 ext4   470.6G  426.4G     3%       /var/snap/firefox/common/host-hunspell
```

I can't tell what I'm looking at here. The **df** and **lsblk** output aren't from the same boot or same system. It doesn't make sense.

I don't know what p1 is since there is p4 doing the UEFI stuff.  Only 1 FAT32 partition is needed.
I don't know what p2 is about and p5 doesn't make sense.  P2 is ext4 and has a UUID that looks like it belongs with ext4, but it isn't mounted to the correct place.  p5 makes ZERO sense.  snaps use loop devices, not real partitions. Again, it makes zero sense.

p3 for swap seems much too small for a default install as well. Since 2020, the default way that swap is created is as a swap file, not a swap partition.  I prefer not using a swap partition, but that isn't the default.  You must either be running an old, unsupported, version of Ubuntu or have manually changed something to cause a swap partition. Can't tell.

Why not just to a fresh install and tell it to use the whole disk?  Different releases and versions of Ubuntu will handle that differently.  Because you've never said which release or flavor of Ubuntu is being used, we can't know what is expected.  **lsb_release -d** will show the booted version, but not the flavor.  To get both, install inxi and run **inxi -Sz**  That will show the minimal information.

As for "like Windows" ... I haven't installed MS-Windows since around 2010. Many of us here don't really use Windows, so we don't know what "like Windows" means.

You keep asking for guidance, but haven't provided sufficient details about what you seek.  "Like Windows" isn't sufficient.  Having 1 big partition, isn't possible thanks to UEFI requirements.  Further, having 2 partitions has security implications that it is clear you don't have the background to understand. It is a bad idea.  The best advice we can provide is to accept the defaults from an install of 22.04 that takes the whole drive for the install provided you use ext4 - no encryption; no ZFS; no BTRFS; no LVM. This should make a simple setup with little deep knowledge required to do something better.

---

### Post by laxmidhar on 2023-10-27
Thanks for the reply @TheFu

As you ask about the release and flavor of Ubuntu how much i am getting sharing that
```
sb_release -d
Description:    Ubuntu 22.04.3 LTS
```
```
inxi -Sz
System:
  Kernel: 6.2.0-35-generic x86_64 bits: 64 Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)

```
```
cat /var/log/installer/media-info 
Ubuntu 22.04.2 LTS "Jammy Jellyfish" - Release amd64 (20230223)
```

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292955&stc=1[/IMG]

In windows it comes with one partition or the main partition that is **C** drive which is the OS drive we have to do the partition from one to usually three partition those are called **C** drive **D** drive and **E** drive. The **C** drive always for the OS and any app or software you install by default it will install in **C** drive and you can keep your media and other stuff in **D** and **E **drive.

Please guide me the further steps if you need any information let me know i am happy share.

Thanking you in advance.

---

### Post by yancek on 2023-10-27
>  In windows it comes with one partition or the main partition that is **C**  

For about 10 years now, windows preinstalled systems have generally had 4 partitions.  On a GPT drive, windows must be installed in UEFI mode which will mean an EFI partition.  Looking at your output, it appears that your first partition (nvme0n1p1) was the windows EFI partition.  That is standard with windows EFI installs, the EFI partition is usually the first and with a vfat filesystem.  Other windows partitions will be ntfs filesystems.  Current/recent windows systems also have 'reserved' and 'recovery' partitions.  Your system does not.

The problem with the windows naming conventions is that they are copied from earlier systems (IBM, CP/M) from the 1970's.  Usually the C, D, E naming for partitions isn't a problem but windows users confuse drives with partitions and partitions with drives.  The C can be the entire hard drive or simply a partition.  If you have ever dual booted windows systems you will see how this creates problems.  If you have 2 windows systems on a computer or the same drive, when you boot the first it will show itself as 'C' and the other as 'D' or some other letter.  If you boot the second windows, it will also show itself as the 'C' partition and the first install of windows as 'D' or some other letter.

The above is just informational and as to your problem, you have a 470GB partition which you can shrink and create a separate partition for a /home partition or simply a data partition on which you can store your media or other personal files.  THe link in my last post is to the GParted manual which explains in detail how to do this.  If you have problems with it, post back and specify what you do not understand.

---

### Post by laxmidhar on 2023-10-28
Thanks @yancek for the information.
Sorry for the delay response.

I will do the partition of 470GB.
1. Now my concern is if i need any app in which partition it will store.
2. How can i remove these two SSD from the dock. When i am right clicking on that i am getting only mount option. I have attached a screenshot for your reference.


Thanking you in advance.

---

### Post by Impavidus on 2023-10-28
> **laxmidhar said:**
> Thanks @yancek for the information.
Sorry for the delay response.

I will do the partition of 470GB.
1. Now my concern is if i need any app in which partition it will store.
When you install some application using the package manager (and I wouldn't recommend doing otherwise until you've gained some more Linux experience), the software will be installed in whatever directories (plural) the package says it must be installed. There's no need to worry about that; the package manager handles everything, including updates and clean removal later. The partition used is simply whatever partition that directory can be found on. Now there are two big differences compared to Windows:
1: Applications don't get a directory of their own. Typically, the executable is stored in /usr/bin, supporting data files in /usr/share, documentation in /usr/share/doc, supporting libraries in /usr/lib or /usr/lib64, where they are shared with other applications using the same libraries. Shared libraries exist on Windows too (.dll files), but are used more commonly on Linux.
2: The partition is not the top level in the directory tree. In Windows, you get one directory tree under C, another one under D, another one under E, etc. On Linux, the root filesystem (equivalent to C) is mounted at the root of the directory tree, but additional filesystem are mounted somewhere in the same tree. So if, for whatever reason, you decide to mount one filesystem at /usr/share (I'm not recommending that), the supporting data files of all applications will be stored on that partition, with everything else still on the root partition.
> 2. How can i remove these two SSD from the dock. When i am right clicking on that i am getting only mount option. I have attached a screenshot for your reference.


Thanking you in advance.
When your /etc/fstab tells where these filesystems must be mounted, they will no longer be displayed by your file manager. The file manager only displays the stuff not already handled by some deeper level.

---

### Post by TheFu on 2023-10-28
Impavidus' description nails it, but I'll post looking at it from a different way.

Unix systems generally split files in this way:
[LIST=1]
[*]Boot stuff
[*]OS/application stuff
[*]Log files
[*]User working directories - normally called "HOME directories" - every userid has a HOME.
[*]Other, manually customized, data and program areas that don't fit into any of the above areas
[/LIST]

These different locations can be separate partitions or not.  Human users typically use their HOME directory for all files, though it would be smart to place media files like movies, TV shows, other videos, and music files outside your HOME.

Boot stuff goes under /boot/.  That includes UEFI stuff, which must be in a FAT32 partition, I think it is in /boot/EFI/.   /boot must be a native Linux file system - ext2/3/4 or something else native.

OS/Application stuff has multiple different directories.  Probably best to just say to find the table of the _Linux File System Hierarchy Standards_ and review those 10-15 places. [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)  Main locations are /usr, /var, /etc, /proc, /dev, /lib ... You'll get used to these and what sorts of files they hold. There's real genius in the layout.

Log files are placed under /var/log/ ... there are exceptions - there are always exceptions, but the logging system built-into all Unix OSes uses that location. If your disk fills up, it is almost always /var/log that is the problem. many people choose to mount a separate partition to /var/ to prevent some issues.   /var/ is also where Canonical decided to put their snap programs.  I'm fairly unhappy about that choice (I'm unhappy about lots of things related to snap packages), but there's no way to fix it ... er ... no elegant way to fix it is more correct.

User files go into HOME directories.  Each user has a HOME set in their login data at login time.  Most of the time /home/{username} is the location, so many people choose to mount a separate partition to /home/ to keep the OS away from their files.  Always know that /home/ isn't mandated and that any user HOME directory may be placed anywhere on storage. Additionally, that storage doesn't actually need to be directly connected to the computer. It can be network storage. However, there is 1 important requirement. It must have a native Linux file system.  No NTFS. No exfat. No FAT32.   It is possible to have every user's HOME directory use a different partition. 

Other areas for data can be anywhere you like. There are standards and there are places commonly used.  Then there are placed which violate standards, but Canonical has decided to use.  I use these:
/d/D1/
/d/D2/
/d/D3/
/d/D6/
/d/D7/

Commercial software will usually expect to be manually installed into /opt/ somewhere.
If you connect a USB device and allow the DE to mount it, that will typically be placed into /media/{LABEL} or /media/{username}/{UUID}.  I don't allow automatic, unknown, mounts on my systems for security reasons, but most people do (for convenience).

Anyways, I hope this clarifies some things.

Ah ... and when I say partition, I mean partition.  Sizing of partitions is a bit of an art form that I've never mastered.  A partition can be on 1 drive or many drives. Partitions can be merged across different storage devices, though a failure on 1 will usually destroy the data on all of them if they are merged.

Unix systems also expect adults to be managing the OS and performing backups.  If you do something foolish, expect to need backups.  You need to create those backups. There isn't any 1 click solution and the built-in backup tools don't "just work" magically forever. Periodic maintenance is required, usually at least once a month, if not more often.

The best recommendation I have is to accept that you'll get it wrong the first 10 times you setup storage.  I'm still getting it wrong 30 yrs after my first Linux install.  To make up for my inability to guess the future correctly, I use some enterprise storage methods that help make storage much more flexible, at the cost of complexity.  Even with that, I get it wrong.  Maybe "wrong" is incorrect. It isn't perfect and some of it is less than optimal.  I also have a bunch of junk - many TBs of junk that needs to be cleaned up - mainly deleted, as I've already migrated the data to new storage and setup backups for it. I certainly don't need 4 copies of  8TB of junk, right?

So, expect to make mistakes, but learn from each. As your skill grows, if you care, you can try to do better.  OTOH, it isn't the end of the world if you don't get storage setup perfect either.

---

### Post by laxmidhar on 2023-10-28
Hi @[URL="https://ubuntuforums.org/member.php?u=1417721"][B][COLOR=#000000]Impavidus
[/COLOR][/B][/URL]Thanks for the response.
> 2. How can i remove these two SSD from the dock. When i am right  clicking on that i am getting only mount option. I have attached a  screenshot for your reference.
When your /etc/fstab tells where these filesystems must be mounted, they  will no longer be displayed by your file manager. The file manager only  displays the stuff not already handled by some deeper level. 				

Do i need to do any thing for the above or how it will happen please guide me.

Thanking you in advance.

---

### Post by yancek on 2023-10-28
Create an entry in the /etc/fstab directory.  You need an entry for each separate  partition you want available.  For example, one partition for Videos, one for Music, another for data.  I would just do a search here at the forums for how to create an entry in fstab for a data partition.  If that doesn't give you what you want expand the search to an online search.  You should be able to find countless sites describing and explaining as well as examples.

---

### Post by laxmidhar on 2023-10-29
Thanks for the response @**yancek**
as i checked the directory there is no fstab directory inside the etc directory.
```
cd /etc/fstab
bash: cd: /etc/fstab: Not a directory
```
```
cd /etc
laxmidhar@laxmidhar-HP-ProBook-445-G8-Notebook-PC:/etc$ cd /fstab
bash: cd: /fstab: No such file or directory

```

Thanking you in advance.

---

### Post by yancek on 2023-10-29
> cd /etc/fstab

The command above won't show anything as the 'cd' command means change directory.  fstab if a file not a directory.  A simple way to see the contents is to use the command below:

```
cat /etc/fstab
```

This will show the contents of the file.  If you want to edit or make changes to it, you will need to use a text editor to do that such as nano, vi, gedit, etc. and do it with sudo.

---

### Post by laxmidhar on 2023-10-29
Thanks for the guidence @yancek.
Below is the output from the terminal.
 ```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p5 during installation
UUID=fe824d6e-e735-4acd-874b-e361436b0c43 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p4 during installation
UUID=847D-34A5  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
```
Please guide me the next step.

Thanking you in advance.

---

### Post by Impavidus on 2023-10-29
Yes, fstab is only a directory in the sense of a telephone directory: a list of things and where they can be found. In filesystem terms, it's a file. And if you want to get really pedantic, a directory is a file too.

Read the documentation here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by TheFu on 2023-10-29
Lots of people come to these forums asking for help with their fstab files.  There are hundreds of examples.  Find one that makes sense to you and follow it. Obviously, you'll need to replace the example parts with your parts.  The documentation Impavidus linked is excellent too.  Plus there are comments inside YOUR fstab file.
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
        1             2           3        4              5       6

```

Those are there as reminders.  There's also a manpage which explains what the 6 fields mean.  

Make an attempt. Post your updated fstab and get help.  This is the best way to learn.  

Only you know where you want things mounted. We don't.  
Only you know the file system identifier to be used.  We don't.  
Only you know what the file system type is. We don't.  
We can help with specific options, AFTER you show those other things.  
The dump and pass can start as 0 (each of them), but you will probably want to change the value for the "pass".  Again, that depends on the type of file system, so it may not be important. 
The value for the dump is left over from when we did backups using dump/restore in the 1980s.  Nobody uses those tools anymore except people who are 100 yrs old. 

We can't guide you until you make an attempt to find the answer yourself and/or post that attempt.  If you just want someone to do this for you, there are lots of people you can pay, but as with any consumer buying things they don't understand at all, buyer beware.

One of the hardest things for people new to Unix systems to grasp is that if you need something in a configuration file, you are expected to add it.  Every line in the fstab is 1 mount.  The fstab mounts an existing file system to a specific directory.  If the directory is empty, that's best, but you can mount a file system over an existing directory. Everything underneath that mount will still exist, but be completely inaccessible.  That's mostly useless, but it can be done.  Unix can't tell if what you tell it to do is stupid or genius, so if it can allow something, it will.  It is up to the admin to determine whether it is a good idea or not.  So, while we can mount a file system over a directory with contents inside it, that is almost always a bad idea.

---

### Post by laxmidhar on 2023-10-30
Thanks @**TheFu** and @**[COLOR=#000000]Impavidus [/COLOR]**[COLOR=#000000]for the guidance[B].
[/B]It is very simple to remove the two ssd logo from the dock as it is in the above screenshot.
Below is  the screenshot how i removed.


[/COLOR][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292984&stc=1[/IMG]

---

### Post by laxmidhar on 2023-10-30
While trying to do the partition for 470GB when i am clicking the create partition table getting an warning msg.
Below is the screenshot of that msg.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292985&stc=1[/IMG]

Please guide me what is the correct and safe way.

Thanking you in advance.

---

### Post by Impavidus on 2023-10-30
As the error message explains, and as I explained in post #10, you cannot change a mounted partition. You have to run gparted from a live disk, where your root partition can be unmounted.

---

### Post by laxmidhar on 2023-11-03
Thanks to all for the help and support.
Done the partition using **something else** option while installation.

---

