---
title: "Help with triple booting?"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by malinman100 on 2013-05-01
Hello, Im very new to ubuntu and linux in general but can clearly see the benefits of it.. so here is my question/problem... 

I have one 128GB SSD and one 1TB hard drive, I am planning to put windows 7, Ubuntu and Linux mint onto the SSD and save all the files on the 1 TB hard drive.. would this work? can I save the windows and Linux files in one place  or do I need more partitions on the second drive? 

My other question is I know windows must be installed first and everything and then the Linux system but does Linux handle partitioning automatically or do I need to do it manually both times for Ubuntu and Mint and how would I sort these partitions out without screwing things up.

Finally any advice on sizes of partitions? I have 8GB of ram if that helps :).

Sorry for the bombardment of questions and I hope you can help :D

---

### Post by Choragos on 2013-05-01
My opinions on the matter:

1. You do not need to partition things yourself, but the second drive needs to have windows space and linux space.  Linux can see windows formatting but not vice versa (by default).
2. I'm not sure about Mint, but you should be able to install windows, have windows format your second drive, then install the next two linux distros side by side, and grab whatever proportion of the drive you want for linux.
3.  As for the size, each distro itself doesn't need much, but Windows needs quite a bit for it's swap files and whatnot.  I don't have hard numbers for you though.

Disclaimer: I've never specifically tried exactly what you're doing, but I don't see any reason why it shouldn't be like any other install.

---

### Post by malinman100 on 2013-05-01
So how many partitions am I looking at :3 and I don't mind about not seeing Linux stuff while I'm in windows since windows is for games. I was originally going to have 60 gb for windows and a few apps then 60 gb between the two distro's.

---

### Post by ajgreeny on 2013-05-01
I can't help with space requirements for Win7, but I am pretty sure that it can be installed on a single partition if necessary (or is it two?) and there should be plenty of space for all 3 OSs on the 128GB SSD.

Both Mint and Ubuntu use the same installer and you would ideally need to manually partition for both if you are using old type BIOS by choosing the "Something Else" option at Disk Preparation stage.  You can put all linux OSs on logical partitions if it helps, but not Windows, which needs a primary partition for the OS itself.  If you are using GPT partitioning on UEFI you can ignore that as all partitions on that are primary, I believe.  On that size SSD i would leave the linux /home folders in the root partition, as the important files will be your data which can all be put on the 1TB drive.

You will need to make that drive NTFS so it can be used by all OSs; windows will find it automatically, and you can make sure it is mounted by both linux OSs with an easy edit of /etc/fstab.

For more details of this come back again and ask once the OSs are installed and the fstab edit can be dealt with then.

---

### Post by pfeiffep on 2013-05-01
I have a similar set as the one you describe. You might be a bit constrained with 3 OSes on  SSD. I let Win 7 have all of my 160Gb SSD and partitioned my internal HDD for 2 Linux OSes. I splurged and added a 1 Tb ESATA for common storage. You should manually control the partition sized and where to install. 

You can use a single [swap]("https://help.ubuntu.com/community/SwapFaq") partition for both Linux OSes exapmple below from link
> [COLOR=#333333][FONT=inherit]_Low RAM and low disk space_[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] With 512 MiB RAM and 30 GB hard disk, use 512 MiB for swap since RAM is very low.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_Low RAM and high disk space_[/FONT] With 512 MiB RAM and 100 GB hard disk, use 1 GiB for swap since RAM is very low and hard disk space is plentiful.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_High RAM and low disk space_[/FONT] With 2 GiB RAM and 30 GB hard disk, use 1 GiB for swap since hard disk space is very low.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit]_High RAM and high disk space_[/FONT] With 2 GiB RAM and 100 GB hard disk, use 2 GiB for swap since hard disk space is plentiful.[/FONT][/COLOR]
It's pretty difficult to advise [partition sizing]("http://www.control-escape.com/linux/lx-partition.html") on your system needs in advance.  There are more experienced posters here than I - but her goes (I'm brave:KS)
Dedicate 100 Gb of the 1Tb drive for both Linux OSes[INDENT]OS1 41 Gb
OS2 41 GB
Common Swap 8GB
[/INDENT]
I have found that Both Linux OSes on HDD boot just as fast or faster than Win 7 on SSD

---

### Post by malinman100 on 2013-05-01
Thanks for all the suggestions :) I think I will dedicate the SSD to windows and linux os's on the hard drive but is there an easy way/guide to help me set everything up without stuff getting messed up?

---

### Post by pfeiffep on 2013-05-01
Consider [reading this]("http://content.hccfl.edu/pollock/aunix1/partitioning.htm")
 
Write down your proposed partitions in relation to Linux labeling and intended OS to be installed. Sizes are Mb ... be prepared! [B]

I suggest placing Grub 2 on your HDD[/B] which will probably be labeled in Linux term /dev/sdb[INDENT]Even though this is an extremely important consideration it isn't displayed first in the GUI presentation but rather close to the bottom.
Change your BIOS boot order to  boot HDD - GRUB2's OS prober should identify Windows and chain load it enabling boot any of the 3 OSes. 
Caveat here about booting Windows from the drive it's not native - some changes to Win - virtual memory being one - I believe require Win being booted from native drive to take effect. [/INDENT]
Use EXT4 for Linux
Keep 900Mb free for NTFS as shared storage

Take your time - Plan ahead - Be clear headed

---

### Post by oldfred on 2013-05-02
I have two copies of Ubuntu 12.04 & currently 12.10 on my 64GB flash drive in two / (root) partitions and large data partitions and swap on my rotating drive.

I think 60GB would be ok for Windows as many have suggested 30GB as a working minimum even though it will install in less. You do need to keep about 30% free in NTFS partitions for them to remain speedy. 

I like having Windows on one drive and Ubuntu on other drives. You have to use Something else or manual install to get the combo box on the partitioning screen on where to install the grub2 boot loader. You want it in the MBR of the Ubuntu drive.

You can use 10 to 25GB for each / (root) partition and then have a large  NTFS data partition. With 8GB of RAM you may never use swap but good to have some as posted above. I left part of my drive unallocated but in the extended partition and have since added a lot of 25GB / partitions in testing something or the other. 

Is your system a new system with UEFI boot? That may change partitioning or at least arranging it for future use with an efi partition as the first and using gpt partitioning. Ubuntu will boot with either BIOS or UEFI from gpt drives. Windows will only boot from gpt partitioned drives with UEFI but (except XP) will read data on gpt partitioned drives if a partition is NTFS formatted.

---

### Post by malinman100 on 2013-05-02
I think it has UEFI boot but I'm unsure on what that is.. and Ubuntu will give the option on which drive to install and then partition sizes right and the same with mint? So what do I label each partition as?

---

### Post by oldfred on 2013-05-02
If you have a newer system with UEFI, then both Windows from flash or Ubuntu will offer two install choices. But the choice is determined by how you boot install not after booted.
And you have to install both Windows and Ubuntu in same mode, both UEFI or both BIOS or you will not be able to easily dual boot.
If UEFI then you will have gpt partitioning. Windows only boots from gpt with UEFI or only boots from MBR(msdos) with BIOS mode.
Ubuntu can boot in BIOS or UEFI from a gpt partitioned drive or BIOS from a MBR partitioned drive.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

