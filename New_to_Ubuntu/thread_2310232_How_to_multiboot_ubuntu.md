---
title: "How to multiboot ubuntu"
date: 2016-01-17
forum: New to Ubuntu
---

### Post by karsus2 on 2016-01-17
Hello everyone,

I have an old Asus N61JQ laptop with win7 64bit and 500gb HDD. I want to learn more about various Linux distros and want to start with Ubuntu.
Currently I have 2 partitions in my HDD, C and D. (And the recovery partition that I absolutely DONT want to mess up.)

I ve read that I can manage my partitions and create new from this url:

[http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/](http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/)

What is not clear on that guide is how I will install ubuntu without destroying my other partitions. Any advice on that?

Also how will I setup the question screen on which OS to chose upon loading? Is it done automatically.
To expand on that I plan to create 3 new partitions (E\Ubuntu, F\Kali, G\Tails) to learn how to use them. So I am looking for a solution in the boot screen that would scale and later allow me to chose between all 4 OS's installed.


Thanks for your help,
Karsus

---

### Post by Bashing-om on 2016-01-17
karsus2; Hello; My welcome  to the forum.

I do not relate well with Windows' drive nomenclature. I no longer think Windows.
Please boot up a liveDVD(USB) - that desktop install medium of ubuntu - > "try ubuntu" mode to the desktop.
@ the desktop key combo ctl+alt+t will yield a terminal interface _.
Please post back the outputs - Between Code Tags - of linux terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudu blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
so we know from our perspective what the present disk partitioning is.
I do expect that " an old Asus N61JQ laptop with win7 " means that your partitioning scheme is MBR with 3 of the 4 primary partitions in use. In that case we will need to make up that 4th partition for 'buntu's as an extended partition, and within this 'extended' partition make up the 'logical' partitions to contain the additional operating systems.
for your reference; see:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018) <-HowTo: Partitioning Basics-bodhi.zazen
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

As to your concern about the boot menu . Ubuntu will happily accommodate Windows by chainloading the Window's boot code to ubuntu's grub - GRand Unified Boodloader - as well as any/all other operating systems that will be installed. But be aware .. multi-booting several 'buntu's on the same disk ... maintaining the boot code to your preference can be an art .

[INDENT][INDENT]Millions do it
[INDENT][INDENT][INDENT]you can too
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pfeiffep on 2016-01-17
> **karsus2 said:**
> Hello everyone,

I have an old Asus N61JQ laptop with win7 64bit and 500gb HDD. I want to learn more about various Linux distros and want to start with Ubuntu.
Currently I have 2 partitions in my HDD, C and D. (And the recovery partition that I absolutely DONT want to mess up.)

I ve read that I can manage my partitions and create new from this url:

[http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/](http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/)

What is not clear on that guide is how I will install ubuntu without destroying my other partitions. Any advice on that? I strongly suggest using official [Ubuntu documentation ]("https://help.ubuntu.com/community/Installation")

> Also how will I setup the question screen on which OS to chose upon loading? Is it done automatically.The install procedure for a single physical hard drive will replace Windows boot loader with GRUB2 which presents a selectable option to choose which OS to boot[/QUOTE]


> To expand on that I plan to create 3 new partitions (E\Ubuntu, F\Kali, G\Tails) to learn how to use them. So I am looking for a solution in the boot screen that would scale and later allow me to chose between all 4 OS's installed.Possibly use the option try Ubuntu without installing 


> Thanks for your help,
Karsus

---

### Post by grahammechanical on 2016-01-17
Any install of Linux needs at least 2 partitions. One partition for the OS and one partition for swap. Additional installs of LInux will make use of the swap partition used by the previously installed Linux. So, in your situation you will need a minimum of 4 partitions.

1) Ubuntu
2) Kali
3) Tails
4) Swap - used by each Linux OS when we load into it.

Then, we have to think about our data. Linux usually puts user configuration files and data into the /home folder. But we can put /home on its own partition so that a re-install will not loose our data. But in the case of several Linux OS it is best to keep /home as a folder in each OS partition and create a large partition to put our data on and it can then be accessed by all Linux OS. So,

5) partition for data.

Ubuntu will install in less than 10 GB of disk space. To allow space for installing additional large programs we might want to think about 20 - 25 GB partitions for each Linux OS. Altough we can get by with less. And swap to be a little larger than the amount of RAM. Although swap can be less than RAM if we do not intend to hibernate.

Each install of Linux will install its boot loader (Grub) into the MBR of the first hard disk. So, the last Linux installed will have control of the Grub boot loader. If you want Ubuntu to be in control of the boot loader then, after installing another Linux load into Ubuntu and run

```
sudo update-grub
sudo grub-install /dev/sda
```

Assuming that there is only one hard drive.

Those 2 commands will update the Grub boot menu in Ubuntu to detect the newly installed OS and re-write the Ubuntu version of Grub into the MBR again. Keep in mind that every time there is a kernel upgrade in one of the resident Linux OS that kernel will not appear in the boot menu until we run update-grub from the Linux in control of the boot menu.

Ubuntu gives us an Install alongside option which does the work for us but without our control over the size of the partitions. So, most of us will use the Something Else option to direct which partition the installer should put the Linux OS in. I cannot say how things are done in other Linux distributions.

Regards.

---

### Post by oldos2er on 2016-01-17
> **karsus2 said:**
> Hello everyone,

I have an old Asus N61JQ laptop with win7 64bit and 500gb HDD. I want to learn more about various Linux distros and want to start with Ubuntu.
Currently I have 2 partitions in my HDD, C and D. (And the recovery partition that I absolutely DONT want to mess up.)


Then before you do any installing please backup any sensitive files. It is far easier to create backups than it is to try to recover data from a formatted or overwritten partition.

---

### Post by yancek on 2016-01-17
Another option is to put the Linux systems on a flash drive and boot that.  Then all you have to worry about is selecting the correct drive on which to put them.  If you are using windows 7 with MBR, the link below gives an explanation of dual booting Ubuntu with windows and the first part of the page gives a lot of very useful information including some on partitioning.  Also, there is a link to a more detailed page on partitioning.

 [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Edward_Fish on 2016-01-19
1. Back up your entire hard drive, unless you don't care.
2. If running Windows 8 or Windows 10 disable the "fast boot" setting.
3. Load up the Ubuntu DVD and reboot.
4. Install Ubuntu.
5. Partway along the install process you will be presented with some options. Pick "Install Ubuntu alongside Windows" - unless you feel brave enough for advanced partition management. (I didn't.)
6. Drag the slider to set how much memory space Ubuntu will take on the hard drive.
7. Complete a few more steps. Ubuntu should finally install. Once it's done, restart the system.
(Gear in the top-right corner > Shut down... > Restart)
You should be presented with the GRUB bootloader. Congrats!
If Windows starts like normal instead, shut down the computer. Then, start it and spam the key for select boot device. (Probably F9, but could be F2, F10, ESC or DELETE.) Pick Ubuntu and GRUB appears. Congrats!

---

### Post by karsus2 on 2016-01-19
Thank you very much for your replies everyone !!!

:) :) :)

Now to address the suggestions that were mentioned.

I tried using Ubuntu through a USB stick (although I m not sure how correctly I implemented persistent space.) but it was very slow. I m also not sure f it ll not "destroy" the USB because it ll do a lot of read/write operations (and consume it's lifecycle available operations). And overall for the education purposes I want I think it's better to put the OS on a hard drive. IMO in USB it d be better to put a lightweight version (that loads in the console and only loads a GUI if I ask).

As for the basics, yep. I spent these days cleaning useless stuff on my laptop (to make free space). Then I defragged and I backed up my data on an external drive.

Now I have to think about partitions. Currently I have 2 + 1:

1. C:\ Win7 Partition
2. D:\ Data Partition

*hidden [?]: The recovery partition from ASUS that I don't want to destroy [Which is the only thing I haven't backed up - my DVD drive ain't working and since I don't use it I haven't paid half the laptop's price to fix it. Any1 knows if I can back up the recovery partition (it's size is 16gb i think) in a 32 gb USB2.0 drive?]

I m planning to use Win7 's Disk Management untility to create the extra 3 partitions: (E:\ , F:\, G:\). I suspect it might not be the best utility but as long as it does it's job correctly I don't mind (I can learn better utilities later when I m more accustomed to Linux).

Regarding the swap partition, do I have to create it as well or will Ubuntu create it during it's installation? I ve never heard about it  - which means I ll have to google it and do some more reading. [Thanks for pointing it out grahammechanical.] Also can it cause more problems when I try to install Kali and Tails after Ubuntu?

I have already created a USB drive that I can load and isntall Ubuntu 14.04TLS. I ll do the partition later when I have time, my scheduled is kida full lately but I ll be updating after doing something or reading on your suggestions.

Also once I m done with the partitioning I ll load Ubuntu from the USB drive-before installing-and I ll run the commands Bashing-om mentioned and I ll post the results. But before that ll have to understand if I need create 3 partitions or 3+swap. :?

Thanks again for all your suggestions :)
cheers,
Karsus

---

### Post by oldfred on 2016-01-19
DO NOT create partitions with Windows. 
Use Windows tools for Windows and Linux tools for Linux.

Windows may convert to dynamic partitions which is proprietary to Microsoft and does not work with Linux. And cannot be easily undone.
 You need to have the more common extended partition with as many logical partitions as you want inside the extended.

And Linux only works with Linux formatted partitions which Windows cannot make, nor understands.
 gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

### Post by Edward_Fish on 2016-01-19
> *hidden [?]: The recovery partition from ASUS that I don't want to  destroy [Which is the only thing I haven't backed up - my DVD drive  ain't working and since I don't use it I haven't paid half the laptop's  price to fix it. Any1 knows if I can back up the recovery partition  (it's size is 16gb i think) in a 32 gb USB2.0 drive?]
If you boot a live CD, you can use the dd command to copy the entire recovery partition.

> I'm planning to use Win7 's Disk Management untility to create the extra 3 partitions: (E:\ , F:\, G:\)
After you install, Windows will not find any partitions to put in drives E: F: and G: because Windows cannot read/write/detect EXT4 partitions, which is what Linux installs on. So, no extra partitions will appear.
Also, DO NOT the default Windows tool to create partitions. Just go through the normal install process and they will be created automatically. Or, you could use an advanced tool like Paragon Partition Manager (commercial software, full free trial) which CAN detect/create EXT4 partitions.

Really. I've put Ubuntu on 2 computers now, one pretty new, one very old, and the normal install process worked fine. That's still no excuse to not back up the drives before you start!

---

### Post by mansonfan78 on 2016-01-19
If you plan on shrinking the existing windows partition to make room for the new partitions, you MUST use Windows to do that (or else it might not boot).  After doing that it will leave unallocated space - leave that for now, let Ubuntu create the partitions in that space.  You will need one partition for each OS plus one for swap (if you plan to hibernate, swap should be slightly larger than installed ram, if not 2-4gb is probably enough).  You could create another partition for data or just use the windows data partition (d) as linux has no problems reading/writing ntfs.

---

### Post by karsus2 on 2016-01-24
Hello again,

I am slowly but steadily making progress. I backed up my recovery partition (and my data). Used an Ubuntu 14.04 USB to boot Ubuntu without installing, went in terminal and typed the commands Bashing-om told me. Here are the results: 
```

ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0c5913d


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    40965749    20482843+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    40965752   285159031   122096640    7  HPFS/NTFS/exFAT
/dev/sda3       285159424   976771071   345805824    f  W95 Ext'd (LBA)
/dev/sda5       285161472   976771071   345804800    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 8178 MB, 8178892800 bytes
92 heads, 57 sectors/track, 3046 cylinders, total 15974400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aa004


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1312    15974399     7986544    c  W95 FAT32 (LBA)


ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  21.0GB  21.0GB  primary   fat32        hidden, lba
 2      21.0GB  146GB   125GB   primary   ntfs         boot
 3      146GB   500GB   354GB   extended               lba
 5      146GB   500GB   354GB   logical   ntfs




Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 8179MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End     Size    Type     File system  Flags
 1      672kB  8179MB  8178MB  primary  fat32        boot, lba




ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: LABEL="casper-rw" UUID="ccfbea5a-73ee-124b-9541-ff1490bfb367" TYPE="ext2" 
/dev/loop1: TYPE="squashfs" 
/dev/sda1: LABEL="RECOVERY" UUID="3E5F-3A2B" TYPE="vfat" 
/dev/sda2: LABEL="OS" UUID="0CDC712EDC711366" TYPE="ntfs" 
/dev/sda5: LABEL="Data" UUID="1AE473A4E47380B5" TYPE="ntfs" 
/dev/sdb1: LABEL="UUI" UUID="1AFF-2921" TYPE="vfat" 

```

What I m thinking of doing next is reducing D:\ partition (through the windows disk management) by 100gb (if I try to install Ubuntu+Kali+Tails) or by 60gb (If I try to install only Ubuntu).

I ll leave that space unallocated so Ubuntu can format it and patrition it during install (which is doable right?). Do I have to create the 3+1 [Ubuntu, Kali, Tails + Swap partitions during Ubuntu's installation process? Also with 4.0Gb of RAM, how big should swap partition be? 4096Mb or more?

However the above don't factor the results of the commands I posted so I need some help.



Thanks for your help guys.
Regards,
Karsus

---

### Post by Geoffrey_Arndt on 2016-01-24
>   4 Gib for swap is fine.

>   Don't try to create more partitions than you need for a basic Ubuntu install.   That is - a swap, and a system (represented by the root symbol (/) ).

>   Don't try to install Kali or any other Linux distro . . . BECAUSE . . . you'll have your hands full just learning Ubuntu and the Linux basics.   Then, later, if still using Linux, you can install other distros and it'll be a much better experience.   Especially, don't need to create extra partitions during the Ubuntu install process (it complicates the install and increases chances of errors).   Like I said above, later you can always add partitions, drives, distros, etc.

>   Normally best to let installer put the Grub bootloader to the default location (sda).

---

