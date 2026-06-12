---
title: "Gave up waiting for root device Ubuntu 14.04"
date: 2017-06-30
forum: New to Ubuntu
---

### Post by invincible1986 on 2017-06-30
Hey Guys

Good day for you

Please help me in my issue experts

I have a Dell Latitude laptop running Ubuntu 14.04 operating system and everything was just fine until yesterday. I booted normally and a DOS error message appeared telling me that GAVE UP WAITING FOR ROOT DEVICE.. the screenshot is attached .. I googled all the internet and tried all the solutions such as: FSCK, GRUB INSTALL (WHICH DID NOT WORK AT ALL), Created Live USB BOOT stick, everything but nothing happened.. Tried to boot from a previous kernel. Nothing happened and the problem is still there. Guys I need to boot up my laptop even once! It's for my business and I work as a travel agent and confidential data is there and If i do not get it to work again I WILL BE REALLY FU**ED UP. Please help me.. It will be the favor of my life.

Please note .. I am not ubuntu professional .. so please when giving me solutions provide steps and I will be thankful 

Thank you in Advance

---

### Post by oldfred on 2017-06-30
If data is important, you really need backups, whether Linux or Windows or Mac.

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by invincible1986 on 2017-06-30
> **oldfred said:**
> If data is important, you really need backups, whether Linux or Windows or Mac.

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)


My friend

First of All, I don't get all the descriptions such as (ISO PPA) I am not that professional.
Second, I need to boot up, I am a travel agent and there is a reservations platform installed on my ubunutu which i need to login to retrieve and manage my customers flight reservations.

Sorry for my poor english and I am hoping you will help me.

---

### Post by oldfred on 2017-06-30
Please use standard fonts, large bold sounds like you are shouting.

Please look at links as they explain a lot of what you need to do.

Do you have a working flash drive with Ubuntu installer? You will need that, if you do not have one.
       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by invincible1986 on 2017-06-30
> **oldfred said:**
> Please use standard fonts, large bold sounds like you are shouting.

Please look at links as they explain a lot of what you need to do.

Do you have a working flash drive with Ubuntu installer? You will need that, if you do not have one.
       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Sorry for using the large font I meant to make it clearer.

And Yes, I do have a Bootable Ubuntu USB stick, I've created it today using a windows PC and I tried it and it worked fine.

---

### Post by oldfred on 2017-06-30
then boot it in live mode and go to Boot-Repair link above.
Copy each line on 2nd option to use ppa to add and run Boot-Repair.
then it should give you a link to a pastebin site with your details of your configuration, so we can review how it is set up.
Do not run auto-fix until someone has reviewed the report.

---

### Post by invincible1986 on 2017-06-30
> **oldfred said:**
> then boot it in live mode and go to Boot-Repair link above.
Copy each line on 2nd option to use ppa to add and run Boot-Repair.
then it should give you a link to a pastebin site with your details of your configuration, so we can review how it is set up.
Do not run auto-fix until someone has reviewed the report.

But .. Where is the Boot-Repair Link ?

---

### Post by oldfred on 2017-06-30
Link says BootInfo, but if you look it is really downloading Boot-Repair. The report is only one of many things that Boot-Repair can do, but most are under Advanced Options. And sometimes the auto-fix makes things worse, so best to have report first.

Actually with this link, it is the first install option.
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

And as it says in the link:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-info && boot-info
```

---

### Post by invincible1986 on 2017-07-01
> **oldfred said:**
> Link says BootInfo, but if you look it is really downloading Boot-Repair. The report is only one of many things that Boot-Repair can do, but most are under Advanced Options. And sometimes the auto-fix makes things worse, so best to have report first.

Actually with this link, it is the first install option.
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

And as it says in the link:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-info && boot-info
```

Dear Friend, First of all I want to inform you about an important update of my issue,, before I read your last reply I booted with Live USB, I opened terminal and did : sudo fsck /dev/sda1 and restarted.  Now I am able to boot again, but it's too slow! I mean the error message disappeared, but when I power up the system, my laptop gets stuck in a black screen with a blinking (-) white symbol for about 20 - 30 minutes, then it boots. When I log in it takes about 10  minutes to login and everything is too slow, even when I try to click a drop down menu, it takes about 4 minutes to show, 8 minutes to open firefox.. I don't know if this will make it easier for you to find the fix. and about the Boot-Info link you posted I did exactly the steps in the tutorial and at the end it opened a text file for me with the following output in Ubuntu paste: 

[https://paste.ubuntu.com/24997029/](https://paste.ubuntu.com/24997029/)

---

### Post by oldfred on 2017-07-01
What model Dell, or more importantly what are specs, RAM, CPU, video card/chip?

First if you can at all boot or use live installer and mount your hard drive partition, you need to backup all your data. And if running a business you need to have good backup plans and recovery procedures. Systems fail, users make mistakes, and "stuff" just happens. If you have good backups & recovery procedures you do not then panic.
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup) 


And it looks like you have not done any maintenance on your system. All systems whether Linux, Windows or Mac need some maintenance. You have many kernels and should houseclean all but two.

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)
       [https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)
Do yourself a favor and avoid bleachbit. 
   Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

My ten year old laptop would boot in about 40 sec. So something is still wrong.
When you have flash drive plugged in, it is showing hard drive as sdb and linux in sdb1.
I would after doing backups run full fsck on the hard drive partition. If not sdb1 change example shown to correct ext4 partition(s).

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by invincible1986 on 2017-07-01
> **oldfred said:**
> What model Dell, or more importantly what are specs, RAM, CPU, video card/chip?

First if you can at all boot or use live installer and mount your hard drive partition, you need to backup all your data. And if running a business you need to have good backup plans and recovery procedures. Systems fail, users make mistakes, and "stuff" just happens. If you have good backups & recovery procedures you do not then panic.
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup) 





And it looks like you have not done any maintenance on your system. All systems whether Linux, Windows or Mac need some maintenance. You have many kernels and should houseclean all but two.

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)
       [https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)
Do yourself a favor and avoid bleachbit. 
   Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

My ten year old laptop would boot in about 40 sec. So something is still wrong.
When you have flash drive plugged in, it is showing hard drive as sdb and linux in sdb1.
I would after doing backups run full fsck on the hard drive partition. If not sdb1 change example shown to correct ext4 partition(s).

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1


Man than you for the advice.. But it happened, but I will consult backup specialists after fixing the error and follow a plan. But man please, talk to me as a Linux user with zero experience .. Just tell me steps what to do next .. Do you mean I have to run the provided commands in your reply as they are written exactly ? And I really appreciate your follow up.. But please do not bother from me as I am not that professional .

---

### Post by oldfred on 2017-07-01
Run the e2fsck commands as posted, except if your Linux partition is not sdb1. Edit to correct to your Linux ext4 formatted partitions, like sda1. 
Some systems for whatever reason mount flash drive as sda and internal drive as sdb. Normally the first internal drive is sda.

You do not have to be a Linux professional. Just know to run a few commands or change settings. 
And do relatively easy maintenance, once you have read the instructions.

---

### Post by invincible1986 on 2017-07-01
> **oldfred said:**
> Run the e2fsck commands as posted, except if your Linux partition is not sdb1. Edit to correct to your Linux ext4 formatted partitions, like sda1. 
Some systems for whatever reason mount flash drive as sda and internal drive as sdb. Normally the first internal drive is sda.

You do not have to be a Linux professional. Just know to run a few commands or change settings. 
And do relatively easy maintenance, once you have read the instructions.

When I ran the fdisk -l command 

the output shows that my whole hard drive is sda1 

and then detailed : 

Linux on sdb1 
EXT sdb2
Swap sdb3

---

### Post by oldfred on 2017-07-01
Before the sda drive was your flash drive.
What were sizes of sda & sdb in fdisk or parted commands? That should tell you which is flash drive and which is internal hard drive.
sudo parted -l
sudo fdisk -lu

---

### Post by johndough2 on 2017-07-02
Hi

I would buy and use a new device, like a caddy and new HDD to clone / copy /backup your existing system.  Is it important enough, your data to do that?

At a stretch USB stick or an SD card.

Your existing HDD may be about to fail.  If it does bang goes your business.  
So go to a computer shop and buy the necessary or pay them to clone your HDD.

You may want to try yourself, clonezilla.org, but I am thinking your drive needs careful handling.

If you have access to another PC you could install ubuntu on that and copy over the data, even try a virtual ubuntu inside windows.  [https://www.virtualbox.org/](https://www.virtualbox.org/).

The advice given above by OldFred about a backup is priceless considering your position.

If in doubt please ask.

---

### Post by invincible1986 on 2017-07-02
> **oldfred said:**
> Before the sda drive was your flash drive.
What were sizes of sda & sdb in fdisk or parted commands? That should tell you which is flash drive and which is internal hard drive.
sudo parted -l
sudo fdisk -lu

**This is the output for sudo parted -l :**

```
ubuntu@ubuntu:~$ sudo parted -l
Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sda: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba


Model: ATA WDC WD5000BEVT-7 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  499GB  499GB   primary   ext4            boot
 2      499GB   500GB  1026MB  extended
 5      499GB   500GB  1026MB  logical   linux-swap(v1)


```
**And this is the output of sudo fdisk -lu:**

```
ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1497772032 bytes, 2925336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 14.6 GiB, 15631122432 bytes, 30529536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0062d27c

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 30529535 30527488 14.6G  c W95 FAT32 (LBA)


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2da43bf1

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *         2048 974766079 974764032 464.8G 83 Linux
/dev/sdb2       974768126 976771071   2002946   978M  5 Extended
/dev/sdb5       974768128 976771071   2002944   978M 82 Linux swap / Solaris
```

> **johndough2 said:**
> Hi

I would buy and use a new device, like a caddy and new HDD to clone / copy /backup your existing system.  Is it important enough, your data to do that?

At a stretch USB stick or an SD card.

Your existing HDD may be about to fail.  If it does bang goes your business.  
So go to a computer shop and buy the necessary or pay them to clone your HDD.

You may want to try yourself, clonezilla.org, but I am thinking your drive needs careful handling.

If you have access to another PC you could install ubuntu on that and copy over the data, even try a virtual ubuntu inside windows.  [https://www.virtualbox.org/](https://www.virtualbox.org/).

The advice given above by OldFred about a backup is priceless considering your position.

If in doubt please ask.

Hello man,

Good day for you.

I appreciate your advice.. but there is a platform installed by IATA on my laptop. I need to login to take my credentials.. If I don't, I will be in a big trouble, it's not about the files .. it's about a platform installed and need to get access to it .. It's a reservation system platform for travel agents. I don't know if you get it. But my case is complicated. I will do the thing you advised me after I login and get my credentials, then I will buy a new laptop (I already did) ,, And I will send it to the company to install the platform on it then I will make a backup and disaster recovery plan.. But first of all I must login. :(

---

### Post by oldfred on 2017-07-02
Please use Code Tags if longer output. Easy to add with forum's advanced Editor and # icon.

You show sda as 15.6GB or a typical 16GB flash drive.
And sdb as 500GB or your internal hard drive.

Have you run the e2fsck on sdb1, as you have to have flash drive plugged in to run it.
But when flash drive is not plugged in, your internal drive will probably revert to sda.
And that can confuse drive order install of grub and perhaps some other things.

You have to send computer in to get their proprietary software? You cannot just download it?
They may then be encrypting system or doing something very proprietary that we cannot fix.
Only a cloned backup and a space hard drive might be the way to recovery. 
Does not your vendor have any recommendations on use and repair of their software?
Do they have a web-site just to see what they say on-line.

---

### Post by invincible1986 on 2017-07-02
> **oldfred said:**
> Please use Code Tags if longer output. Easy to add with forum's advanced Editor and # icon.

You show sda as 15.6GB or a typical 16GB flash drive.
And sdb as 500GB or your internal hard drive.

Have you run the e2fsck on sdb1, as you have to have flash drive plugged in to run it.
But when flash drive is not plugged in, your internal drive will probably revert to sda.
And that can confuse drive order install of grub and perhaps some other things.

You have to send computer in to get their proprietary software? You cannot just download it?
They may then be encrypting system or doing something very proprietary that we cannot fix.
Only a cloned backup and a space hard drive might be the way to recovery. 
Does not your vendor have any recommendations on use and repair of their software?
Do they have a web-site just to see what they say on-line.

No man, they do not encrypt the system, but their software is not downloadable since it's only allowed for use by licensed travel agents, all travel agents send their computers to the company to download the software or they send a representative of the company to your office to install it.  For example if you have a travel agency, and you have 3 reservation employees you need to send the 3 computers to the company's headquarters and they will install the platform. But they do not make any changes to the operating system. Anyway, I am now running the e2fsck commands and I will post results.

```
ubuntu@ubuntu:~$  sudo e2fsck -C0 -p -f -v /dev/sdb1
                                                                               
     1307328 inodes used (4.29%, out of 30466048)
        5358 non-contiguous files (0.4%)
         933 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 1215713/1057/13
   111285669 blocks used (91.33%, out of 121845504)
           0 bad blocks
          17 large files

     1003841 regular files
      188246 directories
          57 character device files
          25 block device files
           0 fifos
          23 links
      114600 symbolic links (89905 fast symbolic links)
         550 sockets
------------
     1307342 files
```

```
ubuntu@ubuntu:~$  sudo e2fsck -f -y -v /dev/sdb1 
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

     1307328 inodes used (4.29%, out of 30466048)
        5358 non-contiguous files (0.4%)
         933 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 1215713/1057/13
   111285669 blocks used (91.33%, out of 121845504)
           0 bad blocks
          17 large files

     1003841 regular files
      188246 directories
          57 character device files
          25 block device files
           0 fifos
          23 links
      114600 symbolic links (89905 fast symbolic links)
         550 sockets
------------
     1307342 files

```

I restarted after performing the commands, and tried to boot, the same thing,it can boot but after 30 minutes.. and everything is too slow. :(

---

### Post by oldfred on 2017-07-02
When you reboot are you removing flash drive?

---

### Post by invincible1986 on 2017-07-02
> **oldfred said:**
> When you reboot are you removing flash drive?

Yes I remove the flash drive when I reboot

---

### Post by oldfred on 2017-07-02
If you type exit at the message on booting, does it boot faster?

Once booted even if slow run these and post results:
       systemd-analyze  
cat /etc/fstab

---

### Post by invincible1986 on 2017-07-03
> **oldfred said:**
> If you type exit at the message on booting, does it boot faster?

Once booted even if slow run these and post results:
       systemd-analyze  
cat /etc/fstab

The error message has returned again, and I don't know what happens when I type exit I will try it .. And I will try to boot and post the commands you provided.

---

### Post by johndough2 on 2017-07-03
Hi

No I didn't get it.

From the OP you now give more info, its your credentials you want, not client bookings. 

If the info, your credentials are on the machine, then clonezilla will transfer everything (byte for byte) to a new HDD via a USB stick caddy or whatever and the new laptop will have your credentials on it.

It could just take, (byte for byte) a specific area, like 1 partition or folder, and place that on the new device.  

Therefore a local PC shop clones your HDD to a new one, fits the new one, then your machine is useable again with the old HDD still in your possession.

---

### Post by invincible1986 on 2017-07-03
> **johndough2 said:**
> Hi

No I didn't get it.

From the OP you now give more info, its your credentials you want, not client bookings. 

If the info, your credentials are on the machine, then clonezilla will transfer everything (byte for byte) to a new HDD via a USB stick caddy or whatever and the new laptop will have your credentials on it.

It could just take, (byte for byte) a specific area, like 1 partition or folder, and place that on the new device.  

Therefore a local PC shop clones your HDD to a new one, fits the new one, then your machine is useable again with the old HDD still in your possession.

Man :/ I am sorry.. this is not the case .. I can't explain because of my language .. But it involves credentials and managing existing clients bookings and PASSENGER NAME RECORDS -PNR's- that are inside the platform.. existing bookings mean that they are clients who are already travelling or clients their bookings will get used in the upcoming days.. so I have to login .. I hope you get what I am trying to say.

OldFred, man I am out of town and as soon as I arrive tonight I will execute the commands and post the results, but any way ..  before I get in the car I powered up the laptop waited for the error message and typed exit.. it wasn't quicker as I noticed. But I waited for it to boot .. everything was slow as I told you before but I couldn't wait more because the car was waiting for me. So I typed my login password and went out. As soon as I return tonight it will be logged in and I will execute the commands in the terminal .

---

### Post by leunam12 on 2017-07-04
Your hard drive may be failing and that could be the reason it is so slow to boot and do anything on it. You have to use clonezilla to clone the hard drive to another drive, everything will be transferred unless there are already serious read/write problems on the drive. Hopefully that's not the case.  Hard drives fail very easily.

---

### Post by invincible1986 on 2017-07-04
> **oldfred said:**
> If you type exit at the message on booting, does it boot faster?

Once booted even if slow run these and post results:
       systemd-analyze  
cat /etc/fstab

Dear friend, I attached the outputs of the commands.

---

### Post by invincible1986 on 2017-07-04
> **leunam12 said:**
> Your hard drive may be failing and that could be the reason it is so slow to boot and do anything on it. You have to use clonezilla to clone the hard drive to another drive, everything will be transferred unless there are already serious read/write problems on the drive. Hopefully that's not the case.  Hard drives fail very easily.

I hope this is not the issue, and just in case.. what is clonzilla? is it something like Norton Ghost? Will it recover all my files and settings and customizations ?

---

### Post by leunam12 on 2017-07-04
If the clone is successful everything will be the same as in the original drive.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by oldfred on 2017-07-04
Please copy & paste terminal output. If longer use Forum's advanced editor and use # icon to add code tags. 

Many have used & suggest clonezilla in the forum.

I do not understand your fstab.
You do not show a mount of / so system should not ever boot.
But the mount by UUID is your / (root) partition?

Has it always been that way?

Lets see if a standard entry in fstab works better.

sudo nano /etc/fstab

first add hashtag(#)as shown here to existing line and then copy & paste second line(do not try to type, nano is an old style terminal editor and you have to move with arrow keys, paste will on happen where ever cursor is moved to. So first move down to bottom line and type #.
 [COLOR=#ff0000]#[/COLOR]/dev/disk/by-uuid/77b74235-9035-4d21-a9d6-b619bf4fbeb8 /mnt/77b74235-9035-4d21-a9d6-b619bf4fbeb8 auto nosuid,nodev,nofail,x-gvfs-show 0 0
Then move cursor to bottom and paste this into fstab & exit saving file.
UUID=77b74235-9035-4d21-a9d6-b619bf4fbeb8  /               ext4    noatime,errors=remount-ro 0       1 


Run this to confirm no errors. If it just returns then it is ok. But if error message we must fix before rebooting.
sudo mount -a

---

### Post by invincible1986 on 2017-07-04
> **oldfred said:**
> Please copy & paste terminal output. If longer use Forum's advanced editor and use # icon to add code tags. 

Many have used & suggest clonezilla in the forum.

I do not understand your fstab.
You do not show a mount of / so system should not ever boot.
But the mount by UUID is your / (root) partition?

Has it always been that way?

Lets see if a standard entry in fstab works better.

sudo nano /etc/fstab

first add hashtag(#)as shown here to existing line and then copy & paste second line(do not try to type, nano is an old style terminal editor and you have to move with arrow keys, paste will on happen where ever cursor is moved to. So first move down to bottom line and type #.
 [COLOR=#ff0000]#[/COLOR]/dev/disk/by-uuid/77b74235-9035-4d21-a9d6-b619bf4fbeb8 /mnt/77b74235-9035-4d21-a9d6-b619bf4fbeb8 auto nosuid,nodev,nofail,x-gvfs-show 0 0
Then move cursor to bottom and paste this into fstab & exit saving file.
UUID=77b74235-9035-4d21-a9d6-b619bf4fbeb8  /               ext4    noatime,errors=remount-ro 0       1 


Run this to confirm no errors. If it just returns then it is ok. But if error message we must fix before rebooting.
sudo mount -a

From where to run these commands ? Live boot or normal boot? 
and about copying and pasting the output, I tried to but I couldn't because it was too slow, I opened a firefox window to post on the thread but I waited for about 45 minutes and the browser window was not responding so I finally decided to take a picture by my phone for the output. I am sorry man.

---

### Post by oldfred on 2017-07-04
Commands as posted would only work from your inside your install.

If a lot quicker you can mount your / partition from your live installer and use the terminal there.
But then you have to add to front of each command the extra mount path.

If live installer to edit fstab in partition sda1. If with live installer, you install is really in sdb1, then change the sda1 to sdb1.
Check with this to see which is your Linux partition.
sudo parted -l
 sudo mount /dev/sda1 /mnt
sudo nano /mnt/etc/fstab

---

### Post by invincible1986 on 2017-07-04
> **oldfred said:**
> Commands as posted would only work from your inside your install.

If a lot quicker you can mount your / partition from your live installer and use the terminal there.
But then you have to add to front of each command the extra mount path.

If live installer to edit fstab in partition sda1. If with live installer, you install is really in sdb1, then change the sda1 to sdb1.
Check with this to see which is your Linux partition.
sudo parted -l
 sudo mount /dev/sda1 /mnt
sudo nano /mnt/etc/fstab

Man, I did exactly what you told me, I edited the fstab, and I am attaching a screenshot from the terminal, I executed the ```
sudo mount -a
```, and it returned without any errors, I rebooted, but the "Gave up waiting for root device" error just appeared but with higher resolution, I mean the font of the error text was smaller.

---

### Post by oldfred on 2017-07-04
From live installer, add Boot-Repair again and run from advanced mode the full uninstall/reinstall of grub and check off to add latest kernel.

[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)
Under grub options purge grub before reinstalling, purge kernels,

Is BIOS set for AHCI mode for drives? It should be AHCI, not RAID nor IDE.

---

### Post by invincible1986 on 2017-07-05
> **oldfred said:**
> From live installer, add Boot-Repair again and run from advanced mode the full uninstall/reinstall of grub and check off to add latest kernel.

[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)
Under grub options purge grub before reinstalling, purge kernels,

Is BIOS set for AHCI mode for drives? It should be AHCI, not RAID nor IDE.

Man, I followed your instructions exactly, and followed the instructions of the boot repair accurately, but now I am stuck here as in the screenshot since 1 hour. I don't know what do, is it a good idea to interrupt and reboot? 

And about the BIOS setting I will check and make it right if it is not.

---

### Post by oldfred on 2017-07-05
You have to say Yes, so it removes the old grub. And it will immediately install the new grub.
But if interrupted before new grub is installed or Internet not working to download new copy of grub then it will not boot at all.
This totally removed all of grub and then totally reinstalls grub, so we know we have a full standard copy of grub.

---

### Post by invincible1986 on 2017-07-05
> **oldfred said:**
> You have to say Yes, so it removes the old grub. And it will immediately install the new grub.
But if interrupted before new grub is installed or Internet not working to download new copy of grub then it will not boot at all.
This totally removed all of grub and then totally reinstalls grub, so we know we have a full standard copy of grub.

Man, First of all.. the operations were performed on sda1 (which is the USB), I rebooted and entered BIOS and checked the setting of the drives, It was IRRT, I changed it to AHCI and repeated the Boot-Repair process, and it seen my install drive which is sdb1, then Boot-Repair opened a dialogue for me which says: Please open a terminal then type or copy-paste the following three commands.. I did and the three commands outputs were as follow:

the first command returned nothing means it worked well.

the second command returned : ```
Reading Package lists.. Error!
E: Unable to synchronize mmap - msync (5: Input/output error)
E: The package lists  or status file could not be parsed or opened.
```

the third command did not do anything and did not return it is like frozen. and the dialogue which you have seen is just showing me an example but it's not the actual option to confirm grub removal. And When I click Forward it informs me the following message : GRUB is still present. Please try again.

---

### Post by oldfred on 2017-07-05
Are you trying to install grub to sda which your system seems to see as flash drive.
You need to make sure commands are run against your actual install which when flash drive plugged in is sdb.

The flash drive is not updateable, so errors on trying to update it would be normal.
But if from your actual install, it says system is corrupted. 
And then again restore from the total backup you made  and regularly updated would be the easiest solution.

So try again and make sure it is working on your internal drive not your flash drive.
And regularly check using parted as before, as having flash drive as sda is not normal and some BIOS setting may change drive order.

---

### Post by invincible1986 on 2017-07-05
> **oldfred said:**
> Are you trying to install grub to sda which your system seems to see as flash drive.
You need to make sure commands are run against your actual install which when flash drive plugged in is sdb.

The flash drive is not updateable, so errors on trying to update it would be normal.
But if from your actual install, it says system is corrupted. 
And then again restore from the total backup you made  and regularly updated would be the easiest solution.

So try again and make sure it is working on your internal drive not your flash drive.
And regularly check using parted as before, as having flash drive as sda is not normal and some BIOS setting may change drive order.

But I made sure that sdb1 is my actual install.. And what do you mean about restoring from the total backup I made?

---

### Post by oldfred on 2017-07-05
I am just trying to reinforce the idea that backups are vital. 
We would not have 4 pages trying to recover your system, if you had a good backup.

But we will keep trying.

If Boot-Repair's short version of a chroot (CHange ROOT) is not working then we can try a full chroot.
But each command has to be copied or typed exactly correctly. And if an error, do not proceed as errors have to be resolved first.

Or if you can boot into system, even if slow, and Internet is working, you can just do a full uninstall/reinstall of grub without the chroot.

Did you try the recovery mode boot?

 To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by invincible1986 on 2017-07-05
> **oldfred said:**
> I am just trying to reinforce the idea that backups are vital. 
We would not have 4 pages trying to recover your system, if you had a good backup.

But we will keep trying.

If Boot-Repair's short version of a chroot (CHange ROOT) is not working then we can try a full chroot.
But each command has to be copied or typed exactly correctly. And if an error, do not proceed as errors have to be resolved first.

Or if you can boot into system, even if slow, and Internet is working, you can just do a full uninstall/reinstall of grub without the chroot.

Did you try the recovery mode boot?

 To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

My friend, first and most important of all, I am really embarrassed and thankful at the same time, all your attempts are appreciated.. I am so sorry because it took a long time but I am really seriously in a big trouble and there is no one there to help but you. I can't stop thanking you for your efforts and I will follow a backup plan in the very near future after finding a solution. Thank you again man. I will keep trying your fixes and hope it will come to a positive result ;).
And about logging in my system normally if I connect to the internet everything becomes unresponsive. Can we do it via live booting ? 
And I remember that I have entered recovery mode but I forgot how did I get there.

---

### Post by oldfred on 2017-07-05
Recovery mode is the second grub menu item, may be under the Advanced Options.

I did not know what IRRT was as have not seen that before.
That is for RAID, but Dell seemed to use it for single drives also. If Windows you probably would have to add a Windows AHCI driver before changing.
RAID can confuse Desktop install of grub, as you have to have the server version to fully support RAID.
So change to AHCI is important.
[https://www.google.com/search?client=ubuntu&channel=fs&q=BIOS+drive+IRRT&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=BIOS+drive+IRRT&ie=utf-8&oe=utf-8)

If not connected to Internet, is installed system response ok? Are you using Wireless or hardwired connection. If Wireless try a hard wire Ethernet cable connection.
And with live install is system ok, with and without Internet?
We may need Internet driver type fixes, which I know less about as all my systems have just worked.

---

### Post by invincible1986 on 2017-07-05
> **oldfred said:**
> Recovery mode is the second grub menu item, may be under the Advanced Options.

I did not know what IRRT was as have not seen that before.
That is for RAID, but Dell seemed to use it for single drives also. If Windows you probably would have to add a Windows AHCI driver before changing.
RAID can confuse Desktop install of grub, as you have to have the server version to fully support RAID.
So change to AHCI is important.
[https://www.google.com/search?client=ubuntu&channel=fs&q=BIOS+drive+IRRT&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=BIOS+drive+IRRT&ie=utf-8&oe=utf-8)

If not connected to Internet, is installed system response ok? Are you using Wireless or hardwired connection. If Wireless try a hard wire Ethernet cable connection.
And with live install is system ok, with and without Internet?
We may need Internet driver type fixes, which I know less about as all my systems have just worked.

I have already configured my BIOS to AHCI, and the response of my ubuntu install is very unresponsive even without internet .. but with internet it freezes fully. When booting from USB it's normal and responsive with and without internet everything is 100% ok.

---

### Post by oldfred on 2017-07-05
Bit more complicated to chroot that run commands from inside install, but if too slow to use then we will have to use live installer & chroot. But first lets see what may be issue from log files.

With Ubuntu there is the old way to boot & the newer way. We tried running 
  systemd-analyze and you got nothing, so I assume you are booting with upstart.
Then you should have a long log file in /var/log/dmesg.

Is live installer you are using the same version as your install or a newer version?
From live installer, if install is still sdb1:
      
 sudo mount /dev/sdb1 /mnt
gksudo gedit /mnt/var/log/dmesg 

If error on not having gksudo
sudo apt-get install gksudo

We do not care about most of the lines. But first part is a time stamp and you should be able to copy just those entries, one before & one after a large jump in time. 
this was a 3 sec jump in mine, post just a few with very large time jumps, you may only have several.
```
[    3.069686] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    6.045625] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro

```

---

### Post by invincible1986 on 2017-07-06
> **oldfred said:**
> Bit more complicated to chroot that run commands from inside install, but if too slow to use then we will have to use live installer & chroot. But first lets see what may be issue from log files.

With Ubuntu there is the old way to boot & the newer way. We tried running 
  systemd-analyze and you got nothing, so I assume you are booting with upstart.
Then you should have a long log file in /var/log/dmesg.

Is live installer you are using the same version as your install or a newer version?
From live installer, if install is still sdb1:
      
 sudo mount /dev/sdb1 /mnt
gksudo gedit /mnt/var/log/dmesg 

If error on not having gksudo
sudo apt-get install gksudo

We do not care about most of the lines. But first part is a time stamp and you should be able to copy just those entries, one before & one after a large jump in time. 
this was a 3 sec jump in mine, post just a few with very large time jumps, you may only have several.
```
[    3.069686] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    6.045625] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro

```

I couldn't install gksudo 

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ gksudo gedit /mnt/var/log/dmesg
The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt install gksu
You will have to enable the component called 'universe'
ubuntu@ubuntu:~$ sudo apt-get install gksudo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gksudo
ubuntu@ubuntu:~$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gksu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gksu' has no installation candidate
ubuntu@ubuntu:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial InRelease
Hit:2 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial Release
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease  
Hit:6 http://archive.ubuntu.com/ubuntu xenial InRelease                 
Hit:7 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
                                                   
** (appstreamcli:23530): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gksu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gksu' has no installation candidate
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 
```

---

### Post by leunam12 on 2017-07-06
Invincible1986, the first thing that you need to do before attempting to do anything is to make sure that your hard drive is not failing, because if it is you are just wasting your time trying to fix a system on a bad drive. Boot your live session from USB and press the windows key and type disks, then open the disks application, then open the SMART data & Self-test and check the SMART information. Look to see if there are any Read Error Rate, reallocated sector count, sectors pending reallocation; Reported uncorrectable; reallocation event count errors. If you have non-zero value on any of those fields start migrating your data to a new drive.

---

### Post by oldfred on 2017-07-06
Good point from leunam12, best to check drive.

It also said you have to enable universe to be able to download gksu.
sudo add-apt-repository universe
then 
sudo apt-get install gksu

I had forgotten that gksudo is just part of gksu. They really are the same command.

---

### Post by invincible1986 on 2017-07-06
> **oldfred said:**
> Good point from leunam12, best to check drive.

It also said you have to enable universe to be able to download gksu.
sudo add-apt-repository universe
then 
sudo apt-get install gksu

I had forgotten that gksudo is just part of gksu. They really are the same command.


Am I in  a big trouble guys ?

---

### Post by leunam12 on 2017-07-06
That disk is in bad shape, that is why you are having so many problems and slow boot times and all that. Use Clonezilla to transfer everything to another drive.

---

### Post by oldfred on 2017-07-06
Leuname12 posted the link to clonezilla back in post #28. You probably should have made that backup then, as more use will lead to more drive issues.
If clonezilla makes a good copy, then I would get a new drive and copy the clone back.

---

### Post by invincible1986 on 2017-07-06
> **oldfred said:**
> Leuname12 posted the link to clonezilla back in post #28. You probably should have made that backup then, as more use will lead to more drive issues.
If clonezilla makes a good copy, then I would get a new drive and copy the clone back.

Guys do you have any tutorial on how to use clonezilla ? and will clonezilla restore everything :( ?

---

### Post by leunam12 on 2017-07-06
Clonezilla will restore everything if the clone is successful. We don't know what is going to happen with your drive, since it is in bad shape and it is probably throwing IO errors like crazy, but you don't lose anything by trying.

[http://www.clonezilla.org/clonezilla-usage/clonezilla-live-videos.php](http://www.clonezilla.org/clonezilla-usage/clonezilla-live-videos.php)

---

### Post by invincible1986 on 2017-07-06
> **leunam12 said:**
> Clonezilla will restore everything if the clone is successful. We don't know what is going to happen with your drive, since it is in bad shape and it is probably throwing IO errors like crazy, but you don't lose anything by trying.

[http://www.clonezilla.org/clonezilla-usage/clonezilla-live-videos.php](http://www.clonezilla.org/clonezilla-usage/clonezilla-live-videos.php)

Thank you man for your efforts I will try,, :( but please tell me, according to the numbers I showed you in the screenshot what is the percentage of an unsuccessful clone ?

---

### Post by leunam12 on 2017-07-06
Probably very high, you may not get everything out but your new disk may be bootable depending where the damage is.
You want to do a whole disk copy using beginner mode. Your destination drive has to be the same size or larger than the original. You have two options: disk-to-disk or disk-to-image. You use disk-to-disk to clone to your destination hard drive if you have a way to have both installed on the same computer at the same time.
You use disk-to-image to make an image of your hard drive usually on a removable device, after the image is completed you remove the damaged drive and install the new one and restore the image to the good drive.

---

### Post by invincible1986 on 2017-07-06
> **leunam12 said:**
> Probably very high, you may not get everything out but your new disk may be bootable depending where the damage is.
You want to do a whole disk copy using beginner mode. Your destination drive has to be the same size or larger than the original. You have two options: disk-to-disk or disk-to-image. You use disk-to-disk to clone to your destination hard drive if you have a way to have both installed on the same computer at the same time.
You use disk-to-image to make an image of your hard drive usually on a removable device, after the image is completed you remove the damaged drive and install the new one and restore the image to the good drive.

And what is the size of the removable device should be when using disk-to-image ? and what is your advice ? to do disk-to-disk? or disk-to-image ? I dont want to boot anymore .. I just want to restore my files again, it will be a less trouble :(

---

### Post by leunam12 on 2017-07-06
If you can do a disk-to-disk it will be better and faster but both drives have to be connected to the computer at the same time, if you have a desktop computer that's not a problem; it is a little harder with a laptop since most laptops only have room for one HDD. But there are hard drive docks and other systems that allow you to plug a SATA HDD via USB

---

### Post by invincible1986 on 2017-07-06
> **leunam12 said:**
> If you can do a disk-to-disk it will be better and faster but both drives have to be connected to the computer at the same time, if you have a desktop computer that's not a problem; it is a little harder with a laptop since most laptops only have room for one HDD. But there are hard drive docks and other systems that allow you to plug a SATA HDD via USB

Okay, then I have to do a disk-to-image, but what is the required removable media for the image ? Does a 16 GB USB flash memory can do the job ?

---

### Post by leunam12 on 2017-07-06
It depends on how much data you have on your hard drive. Try it and if it's too small it will tell you.

---

### Post by invincible1986 on 2017-07-06
> **leunam12 said:**
> It depends on how much data you have on your hard drive. Try it and if it's too small it will tell you.

ok man .. thank you very much .. I will try.. You and Oldfred assisted me alot ... Now I will start trying to make an image and tomorrow I will buy a larger hard disk and I will inform you  what happens. Thank again.

---

