---
title: "Howto: Backup with Partimage"
date: 2006-10-28
forum: Outdated Tutorials &amp; Tips
---

### Post by wieman01 on 2006-10-28
**0. Prerequisites: **[LIST]
[*]Reference: [http://www.ubuntuforums.org/showthread.php?t=226402](http://www.ubuntuforums.org/showthread.php?t=226402)
[*]Download "Rescue CD": [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)[/LIST]
[COLOR="Red"]_**REMARK:**_[/COLOR] The credit goes to user "Frank Golden" whose thread I have taken as a reference in the first place.

**1. Boot from RESCUE CD & type:**[LIST]
[*]Create mount-point:
> mkdir /backup
[*]Checking partition tables:
> fdisk -l
[*]Mount backup partition; **[COLOR=Red]xxxx[/COLOR]** stands for your partition that serves as a backup device (e.g. hda1, sda1):
> mount /dev/**[COLOR=Red]xxxx[/COLOR]** /backup
[*]Start Partimage:
> partimage[/LIST]**2.1. Backing up (screenshot 1):**[LIST]
[*]Choose partition you want to backup.
[*]Type "Image file to create/use":
> /backup/[COLOR=Red]your_backup_file[/COLOR]
[*]Choose "Action to be done" = "Save partition into a new image file".
[*]Press F5.[/LIST]**2.2. Backing up (screenshot 2):**[LIST]
[*]Choose "Compression level" = "None".
[*]Choose "Image split mode" = "Into files whose size is:...".
[*]Select size bigger than your partition in MB (left).
[*]Hit F5.[/LIST]
**2.3. Backing up (screenshot 3):**
[LIST]
[*]Enter any description (or leave it blank).
[*]Press <enter> to continue.[/LIST]
**2.4. Finalizing backup:**
[LIST][*]Hit <enter> when prompted to confirm backup size, disk space, etc.
[*]That's it![/LIST]

**[COLOR="Red"]_IMPORTANT NOTE:_[/COLOR]** When I used "Compression level" Gzip to compress my backup file I was unable to restore it later on. I cannot remember the exact error message, but I have avoided it ever since. When backing up your data, I recommend to use option A which is "None" (no compression). It's also the faster option.

**3.1. Restoring (screenshot 4):**
[LIST]
[*]Select partition to restore.
[*]Type "Image file to create/use" (note the extension [COLOR="Red"].000[/COLOR]):
> /backup/[COLOR=Red]your_backup_file.000[/COLOR]
[*]Choose "Action to be done" = "Restore partition from an image file".
[*]Press F5. [/LIST]
**3.2. Restoring (screenshot 5):**
[LIST][*]Select "Options" = "Simulation of the restoration..." in order to [COLOR="Red"]_test_[/COLOR] your backup file. I highly recommend this extra step. Leave it blank to go ahead without simulation.
[*]Hit F5.[/LIST]
**3.3. Finalizing restoring:**
[LIST]
[*]Confirm all remaining operations with <enter> when prompted.
[/LIST]
Partimage has been fairly reliable so far (well, except for the mentioned issue with GZip compression) but I appreciate if anybody else can contribute ideas & comments. Should I have left out important (or less important) step, please drop me a line.

---

### Post by tedrogers on 2006-11-14
Is it possible to save the image over a network, either to a Windows machine or separate Ubuntu install using Samba?

I have both on my other system, XP and Ubuntu (though not dual boot as I don't want the mess that GRUB/LILO can make of things - so I've got them on separate drives and use my BIOS to select the boot drive for each OS - nice and clean!)

I've noticed from some screenshots there is a network option - is it really that simple?

I'm downloading the Rescue CD now using wget, and will try it out....just wondered if what I want to try is possible.

Thanks wieman [you're everywhere fella! ;) ]

---

### Post by aysiu on 2006-11-14
I created a very similiar tutorial to this, too, detailing how to use it from a Ubuntu Desktop CD (the SystemRescue CD is ideal, of course, though--that way you don't have to install PartImage first):
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by tedrogers on 2006-11-14
I've seen your Psychocats tutorial...it's very good...but I wonder if when I type:

```
sudo fdisk -l
```

...why is it that it doesn't show my network drives as well? Should it?

Maybe Samba isn't setup right.

---

### Post by aysiu on 2006-11-14
> **tedrogers said:**
> I've seen your Psychocats tutorial...it's very good...but I wonder if when I type:

```
sudo fdisk -l
```

...why is it that it doesn't show my network drives as well? Should it?

Maybe Samba isn't setup right.
Honestly, I don't know much about networking or networked drives. I'm hoping someone else will jump in and answer that question.

---

### Post by tedrogers on 2006-11-14
I've spent my evening so far trying to get the networking working normally....mind you...I am trying this over wireless which could be difficult.

Plus, I have noticed, that both my Ubuntu installs have exactly the same 'computer names' which can't be a good thing....clash clash clash! :) :(

So, when I get the chance I will try getting the networking running using a wired LAN config first....then we'll see.

Anyway...good news is that the linux-rescue CD iso works! That is, I suppose, a step in the right direction.

So, any ideas how I might change the computer name 'after' the install process?

Cheers.

---

### Post by wieman01 on 2006-11-14
Not sure what you are referring to as computer names, but this is slightly off-topic so let's talk about that in another thread.

To answer your question: Yes, in principle this would also work over a network. But you would have to install NFS or Samba and mount the share drives not dissimilar to what is mentioned in the howto. The process would look like this:

1. Boot Live CD / Rescue CD.
2. Startup (wireless) networking.
3. Install Samba/NFS server on remote machine.
4. Install Samba/NFS client on local machine (that you are trying to backup).
5. Create mount point & mount shared driver on remote machine.

I am sure you can do that with either the Ubuntu Live CD or the Rescue CD, however, it seems a lot of steps for a simple backup. I usually prefer to store the backup files on the local harddrives first, then copy them to my backup server after restarting & booting my normal Ubuntu install.

Hope this helps. For networking, NFS & Samba I suggest that you open a new thread or read some of the corresponding howtos.

---

### Post by tedrogers on 2006-11-15
One other thing I'm not sure of, because I'm still trying to understand (and remember!) Linux partitioning...is if I only backup /hda1 (SYSTEM) [and it looks like partimage will only let me backup one partition at a time] what happens to /hda2 (SWAP) and /hda5 (EXT3). Do I have to back these up seperately? 

Or are these stored in say the MBR or something so that when I restore /hda1, the /hda2 and /hda5 partitions are restored but without any data in them.

---

### Post by wieman01 on 2006-11-15
> **tedrogers said:**
> One other thing I'm not sure of, because I'm still trying to understand (and remember!) Linux partitioning...is if I only backup /dha1 (SYSTEM) [and it looks like partimage will only let me backup one partition at a time] what happens to /hda2 (SWAP) and /hda5 (EXT3). Do I have to back these up seperately? 

Or are these stored in say the MBR or something so that when I restore /hda1, the /hda2 and /hda5 partitions are restored but without any data in them.
You need to backup & restore each partition separately. So you need to go through the procedure for each data partition that you have with one exception: SWAP. There is no point in making a backup of SWAP of course.

---

### Post by tedrogers on 2006-11-15
So when I restored again...I would need to create a swap partition of the same/similar size I am using currently?

I just tried to make a backup of my partition now using the above guide and I hit a snag...I think the problem is that I was trying to backup to same partition that is mounted (i.e. /hda1)....so is this not possible and do I need to create a new partition to store my backup onto? Something other than /hda1?

Thanks again.

---

### Post by wieman01 on 2006-11-15
> **tedrogers said:**
> So when I restored again...I would need to create a swap partition of the same/similar size I am using currently?

I just tried to make a backup of my partition now using the above guide and I hit a snag...I think the problem is that I was trying to backup to same partition that is mounted (i.e. /hda1)....so is this not possible and do I need to create a new partition to store my backup onto? Something other than /hda1?

_**REVISED:**_
You CANNOT backup to the same partition but you have to mount a separate backup partition that has sufficient space. That's pretty much it. As for the SWAP partition, the size of it is irrelevant, so when you restore you system you create it from scratch with a size that suits your needs.

---

### Post by tedrogers on 2006-11-15
> **wieman01 said:**
> You can backup to the same partition. But you need to have enough space on it. That's pretty much it. As for the SWAP partition, the size of it is irrelevant, so when you restore you system you create it from scratch with a size that suits your needs.

I just tried backing up to the same partition (/hda1) using partimage on the rescue cd...and it wouldn't let me do it. It gave me an error saying that the partition is mounted and wouldn't work...and that I could unmount (umount) it using umount /dev/hda1 (I think).

What's going on here then?

I also tried using qtparted to resize the /hda1 partition, in order to create a spare partition for backing up to, and the only partition where the 'resize' option wasn't ghosted out was the swap?!? It wouldn't let me resize /hda1 at all. I tried to unmount /hda1 in the rescue CD terminal, and it reported that /hda1 wasn't mounted. Confused now.

What next? Any ideas?

Thanks.

---

### Post by wieman01 on 2006-11-15
Ok, I must revise my statement. You cannot backup to the same partition... Sorry, now I got confused. You have to mount a _separate partition_ while making a backup of the HDA1. That should answer your question. 

For resizing partitions, etc. please open up a new thread. Don't want to dilute things here.

---

### Post by tedrogers on 2006-11-16
OKay....that's clearer now. Thanks.

---

### Post by tedrogers on 2006-11-18
Hi wieman01,

Success! I managed to backup my /hda1 partition to my newly created /hda3 partition using your guide. :D 

It was actually very straightforward, apart from the big about splitting the files (I think this could be a bit clearer with maybe some examples)...but I just set it to something bigger than the whole partition I was backing up and it went like a dream. I was a bit concerned for a while though.

The only question I have is to do with the following icon of my backup file:

[IMG]http://i77.photobucket.com/albums/j58/fiddybux/Screen.png[/IMG]

What is the red 'X' on the top-right of the file called 't22-edgy.000' and what does this mean?

Thanks mate.

---

### Post by wieman01 on 2006-11-18
Hello Ted, 

Not sure what the little red "x" means as I am using KDE. However, to change owership of the file (in case it has something to do with it) do this:
> sudo chown [COLOR="Red"]your_user:your_user[/COLOR] /mnt/hda3/t22-edgy.000
Cheers!

---

### Post by dcstar on 2006-11-19
> **wieman01 said:**
> 
.....
**[COLOR="Red"]_IMPORTANT NOTE:_[/COLOR]** When I used "Compression level" Gzip to compress my backup file I was unable to restore it later on. I cannot remember the exact error message, but I have avoided it ever since. When backing up your data, I recommend to use option A which is "None" (no compression). It's also the faster option.
.....

I also had this problem with my original Dapper version of **partimage** (0.6.4.14), but when I backported the Edgy version (0.6.4.17) I was able to create and restore a 1 GB EXT2 partition (on my USB stick) using the **gzip** option successfully.

---

### Post by tedrogers on 2006-11-19
> **wieman01 said:**
> Hello Ted, 

Not sure what the little red "x" means as I am using KDE. However, to change owership of the file (in case it has something to do with it) do this:

Cheers!

Just out of interest, why is it that you use the syntax 'your_user' twice, i.e. your_user:your_user?

By the way, it worked perfectly!

Also I just worked out that if I wanted to change the owner back to being root, I would just replace my 'your_user' section with 'root:root' instead.

Thanks.

---

### Post by wieman01 on 2006-11-19
This syntax ensures that both **user** & **group** owership are assigned to your current user. Just to round the whole thing up. You can skip  the second part (":mrgrimble") if you would like to.

---

### Post by tedrogers on 2006-11-19
I see...thanks. I understand now.

You know...I was on DOS the other night at the command line...and I typed 'ls' instead of 'dir' to show the directory! I had to think hard for a moment but it shows that I'm getting into the Linux way nowadays! :)

---

### Post by amoore on 2006-11-25
This method does not work for me!!!! It might for you.... I wish that the ubuntu live cd would contain a utillity for creating backups of an entire system. 

How does Ubuntu ever expect to make it in the enterprise market without a soild backup or imaging tool?

I've have given sbackup a try too... but no love.

Ubuntu is on both of my main systems at home and a few at work, I love it!!! I just wish it was easy to back up and restore a system.... I thank god that I've never had too, I just want to be ready if I ever do.

Serious thought should be given to including such a utillity in FF 7.06

---

### Post by wieman01 on 2006-11-25
> **amoore said:**
> This method does not work for me!!!! It might for you.... I wish that the ubuntu live cd would contain a utillity for creating backups of an entire system.
What's exactly your problem? Why does it not work for you?

---

### Post by Frank Golden on 2007-01-07
Hi folks, there is a new version of System Rescue CD (v0.3.0)
it has alot going for including Firefox 2.0 and the ability to connect to network.
You can also enter a  "x" desktop environment. See below.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)


amoore, Please describe you problems with partimage. Maybe between us we can make it work for you. Partimage is an excelent ( for me anyways) backup solution. It has allowed me to experiment with settings and customizations in Ubuntu, giving me a method of restoring a hopelessly hosed install in about 10 minutes or so. I do store the backup image on a fat32 partition on my hard drive making everything very quick.
Once you learn the simple commands it is very effective.

---

### Post by LKRaider on 2007-01-16
Partimage has a server that can be installed on the computer where you want to store/restore the backup images to/from.

The package is called **partimage-server**. When setup, you can tell the partimage client the IP of the server and it will transfer the partition data for the server to store. It can also restore data from the server in the same manner.

Very useful, specially for those with notebooks or multiple machines.

---

### Post by bernstein on 2007-01-21
> **wieman01 said:**
> When I used "Compression level" Gzip to compress my backup file I was unable to restore it later on.

Just want to point out that you only need to unzip it before restoring.... (had(6.06) and actually have(6.10) the same problem, that partimage will give an error when trying to restore from a gzipped image)

```
gzip -d yourpartimagefile
```

maybe you want to add this to your first post

---

### Post by LKRaider on 2007-01-22
> **bernstein said:**
> Just want to point out that you only need to unzip it before restoring.... (had(6.06) and actually have(6.10) the same problem, that partimage will give an error when trying to restore from a gzipped image)

```
gzip -d yourpartimagefile
```

maybe you want to add this to your first post

It was reported as a bug. If you have more information or can help confirm it, go to [https://launchpad.net/ubuntu/+source/partimage/+bug/50810](https://launchpad.net/ubuntu/+source/partimage/+bug/50810) and post a reply there about it (like, maybe say it occurs on 5.10 too if you confirmed that).

---

### Post by Gen2ly on 2007-01-22
little disappointed that partimage needs to be used on another file system - i.e. one that isn't mounted.  Hardly seems necessary with how linux works.

I'll continue using Heliodes excellent tutorial which doesn't require this:

[Howto: Backup and restore your system!]("http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup")

---

### Post by LKRaider on 2007-01-23
Well, you can always hack your way around it, but it is good principle of the program to not allow it by default:

partimage --allowmnt

Be sure nothing is writting to the partition at the time (single user mode <strike>suggested</strike> **A MUST!**), or better, mount the partition _read-only_ and then proceed.

OTOH, Tar is definitly safer in this situation.

---

### Post by the.phantom on 2007-01-24
hi, i just used the partimage per your instructions and thought i would make a few small suggestions from a newbie point of view of you don't mind?????

you can't copy and paste the instruction commands and i had one heck of a time as to where to put a space and where not to 

and i think you MIGHT have something a bit wrong?

you have us do a df -l  ( as in L) sure looked like a one or cap i to my over 60 eyeballs

and that shows the partitions
well when i did it it only showed the cd and the main hard drive

BUT
when i did the mount /dev/hdb1 /backup

before i did the df -l

it would show my second hard drive

but thanks for the great post 

mitch

---

### Post by PartisanEntity on 2007-03-13
Just a quick question, does Partimage need to be told **not** to backup empty (unused) space or does it do that automatically?

---

### Post by tagra123 on 2007-03-13
[http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)

My post -- listed above.

The only thing I found missing was to remember to backup the partition table and MBR


Also the ubuntu live cd can be used for this --  see my post.


Also as part of my backups I always keep a printed copy of /boot/grub/menu/lst and /etc/fstab

Also Daily Weekly and hourly backups are linked to at the bottom of the post using a tar and rsync script.   Not real difficult to setup.  I use it mainly for data and the /etc folder. but you could easily just tell it to backup everything.

---

### Post by wieman01 on 2007-03-14
> **PartisanEntity said:**
> Just a quick question, does Partimage need to be told **not** to backup empty (unused) space or does it do that automatically?
It does it automatically as fas as I know. My backup files are usually way smaller than my entire partition.

---

### Post by tedrogers on 2007-03-14
I can confirm what wieman is saying...partimage only backs up the data and not the whole partition size in my experience.

---

### Post by PartisanEntity on 2007-03-14
Thanks for the info.

---

### Post by hppyfngy on 2007-03-15
This method isn't working for me.  See if you can help me out.

I have set up hda3 to accept my backup.  When I boot to SysRescueCD 0.3.3 and then enter

df -l

I only get the mount points of the live cd.  I can't mount the partition as it is not in /etc/fstab

What am I doing wrong?  :confused:

---

### Post by wieman01 on 2007-03-16
> **hppyfngy said:**
> This method isn't working for me.  See if you can help me out.

I have set up hda3 to accept my backup.  When I boot to SysRescueCD 0.3.3 and then enter

df -l

I only get the mount points of the live cd.  I can't mount the partition as it is not in /etc/fstab

What am I doing wrong?  :confused:
Could it be that the Rescue CD does not recognize your hardware? Haven't heard of this one yet.

---

### Post by mw99 on 2007-03-19
> **aysiu said:**
> I created a very similiar tutorial to this, too, detailing how to use it from a Ubuntu Desktop CD (the SystemRescue CD is ideal, of course, though--that way you don't have to install PartImage first):
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Sadly I can't boot my old hardware with System Rescue Disk or Feather Linux so had to revert to my live Ubuntu Edgy CD and download/install PartImage using Aysui's HowTo. I'm backing up to a Samba share on another machine, so here's a few pointers for anyone else trying to do the same:

1) Use aptitude (or synaptic) to install smbfs in addition to partimage

2) Mount the share with something like
```
sudo mkdir /mnt/nas
sudo mount -t smbfs -o lfs,username=****,password='*****' //192.168.1.3/backups /mnt/nas
```
3) Run PartImage and use /mnt/nas/your_image_filename as the target

This also has the advantage of not needing to install PartImage server on the remote machine.

---

### Post by hppyfngy on 2007-03-19
> **wieman01 said:**
> Could it be that the Rescue CD does not recognize your hardware? Haven't heard of this one yet.

No, I don't think so because as the SysRescueCD is loading, the hard drives are all mounted, but after the ram drive is set up, that's all I can access.  For that matter, if I startx at that point, I can see all my drives and partitions, but all the choices in partimage are locked and I can't change them, so I can't write to the partition I want to.   I don't get it either.

Anyone else find a better way to do this?  It's a real pita if you ask me...

---

### Post by croc1 on 2007-03-21
> **hppyfngy said:**
> This method isn't working for me.  See if you can help me out.

I have set up hda3 to accept my backup.  When I boot to SysRescueCD 0.3.3 and then enter

df -l

I only get the mount points of the live cd.  I can't mount the partition as it is not in /etc/fstab

What am I doing wrong?  :confused:

I have the same problem
When I df -l I see only the RescueCD
If i fdisk -l then i can see the partitions listed but cannot mount anything

---

### Post by wieman01 on 2007-03-21
> **croc1 said:**
> I have the same problem
When I df -l I see only the RescueCD
If i fdisk -l then i can see the partitions listed but cannot mount anything
Just to bump this up... Does anybody have an idea so that I can update my thread?

Help is appreciated.

---

### Post by LKRaider on 2007-03-23
You have to manually mount the disk:

mkdir /mnt/hda3
mount /dev/hda3/ /mnt/hda3

---

### Post by tagra123 on 2007-03-24
> **wieman01 said:**
> Just to bump this up... Does anybody have an idea so that I can update my thread?

Help is appreciated.


In my experience SysRescueCD will find the devices but not automatically automount them.

To find your devices --  these commands should work:
```
cd /dev
ls hd*
ls sd*
```

Lets say hdd is my backup drive and its partition 1 and hdc2 is my ubuntu root partition that I'm backing up

```
mkdir /mnt/backup
chmod 777 /mnt/backup
mount /dev/hdd1 /mnt/backup
```

now back it up

```
partimage -o -d -b -z1 save /dev/hdc2 /mnt/backup/root-hdc2-12212006
```

[http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)

---

### Post by wieman01 on 2007-03-25
> **tagra123 said:**
> In my experience SysRescueCD will find the devices but not automatically automount them.

To find your devices --  these commands should work:
```
cd /dev
ls hd*
ls sd*
```

Lets say hdd is my backup drive and its partition 1 and hdc2 is my ubuntu root partition that I'm backing up

```
mkdir /mnt/backup
chmod 777 /mnt/backup
mount /dev/hdd1 /mnt/backup
```

now back it up

```
partimage -o -d -b -z1 save /dev/hdc2 /mnt/backup/root-hdc2-12212006
```

[http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)
You are right in that RescueCD does not automount drives. Our problem, however, is that some drives aren't recognized in the first place (see previous posts). They are not listed.

---

### Post by tagra123 on 2007-03-25
**df -l**  will only** list local mounted file systems**  see man df

You can either look in /dev for hd* or sd*

OR

Type

```
sudo fdisk -l
```

to list drives and partitions.

---

### Post by wieman01 on 2007-03-26
> **tagra123 said:**
> **df -l**  will only** list local mounted file systems**  see man df

You can either look in /dev for hd* or sd*

OR

Type

```
sudo fdisk -l
```

to list drives and partitions.
You're right. Thanks a lot. Have updated the thread accordingly.

---

### Post by tagra123 on 2007-03-26
Could you also mention the dd commands for the partitions tables in your how to -- you are welcome to copy directly from my post if you like.

I believe copying the partition table and MBR helps to make a rock solid method of restoring the disk if need be.

---

### Post by wieman01 on 2007-03-29
> **tagra123 said:**
> Could you also mention the dd commands for the partitions tables in your how to -- you are welcome to copy directly from my post if you like.

I believe copying the partition table and MBR helps to make a rock solid method of restoring the disk if need be.
I'll give this tutorial an overhaul soon and will highlight the stuff you have mentioned.

---

### Post by Lucifiel on 2007-04-17
Good tutorial!!! :D 

Just two questions: can you restore the backup from a media like DVD? :)

And I'm actually currently dual-booting with WinXP. Due to certain hdd issues, I intend to replace my hdd. 

So, for a while, I'm going to be running off Ubuntu off another hdd, but without dual-booting XP.

Will there be any problems with my boot loader if I don't dual-boot with XP(for a while only): that is, will Ubuntu have any problems booting up? 


Thank you! :)

---

### Post by wieman01 on 2007-04-17
> **Lucifiel said:**
> Good tutorial!!! :D 

Just two questions: can you restore the backup from a media like DVD? :)

And I'm actually currently dual-booting with WinXP. Due to certain hdd issues, I intend to replace my hdd. 

So, for a while, I'm going to be running off Ubuntu off another hdd, but without dual-booting XP.

Will there be any problems with my boot loader if I don't dual-boot with XP(for a while only): that is, will Ubuntu have any problems booting up? 


Thank you! :)
No problem...

**1)** Yes, you should be able to restore from a DVD. You just need to mount the device. 
**2)** You need to install GRUB on the HDD's replacement. To do so, you need to copy all data on the new device and thereafter, install GRUB using the Ubuntu LiveCD. There are tutorials concerning this around here.

---

### Post by Lucifiel on 2007-04-17
> **wieman01 said:**
> No problem...

**1)** Yes, you should be able to restore from a DVD. You just need to mount the device. 
**2)** You need to install GRUB on the HDD's replacement. To do so, you need to copy all data on the new device and thereafter, install GRUB using the Ubuntu LiveCD. There are tutorials concerning this around here.

1) Thank you very much. :D Phew... :p 

2) Oh, don't worry. I'm going to repartition the hdd anyways. :p There's no way I'm letting Ubuntu have the entire hdd. :) Oh and actually, this hdd is actually in-use and already partitioned. I'm already clearing off data from 1 of the partitions for this. Edit: Actually, if I'm not wrong, the bootloader's installed on C:\ which is hdc1, a partition from the hdd I'm going to use.

---

### Post by berserker on 2007-04-18
I followed this tutorial and created multiple 2 GB backup files.

When I restore the first one (e.g., /backup/hda1partition000) do I then have to go back and restore the others individually (hda1partition001 then hda1partition002, etc.) or will partimage do all of them in one shot?

TIA

---

### Post by wieman01 on 2007-04-18
> **berserker said:**
> I followed this tutorial and created multiple 2 GB backup files.

When I restore the first one (e.g., /backup/hda1partition000) do I then have to go back and restore the others individually (hda1partition001 then hda1partition002, etc.) or will partimage do all of them in one shot?

TIA
Partimage will do this for you. Don't worry. :-)

---

### Post by Lucifiel on 2007-05-05
Okay, I finally managed to get around to restoring my image of Ubuntu, with Partimage.

What I did was restore my 4.9 gb image to a 20 gb partition.

Now, here's my question: What on earth happened to the other 15 gb?! My partition, dev6 is reported as having 5.5 gb of space and having 600++ mb of free space. :(

Under Gparted, it says that 16.99 gb of 20 gb is used.

Edit: Okay, so having searched around some more, I found out that you need to use a tool or Gparted or some commands to resize the partition?

---

### Post by r76 on 2007-06-01
Thanks for a brilliant guide, I used it to back up my ubuntu and xp partitions.  I hope I never have to test if it works ;)  Still, the backup didn't mention any errors and I did it on to an external ext3 hard drive - exactly what I wanted to do.  I like that it runs like a live CD while no hard drive is mounted or OS running.  One question is why frank golden uses extra commands for mount ([on the system rescue cd forums]("http://www.sysresccd.org/forums/viewtopic.php?t=790")):
```
mount [COLOR="Red"]-t vfat[/COLOR] /dev/xxxx /backup
```
for FAT32 (where xxxx is sda1 or whatever) and
```
mount [COLOR="#ff0000"]-t ext3[/COLOR] /dev/xxxx /backup
```
for ext3, but I guess that's a question for him not you.

Have you tried using the gzip option again yet?  I didn't, just in case.  Anyway, many thanks again :D

---

### Post by wieman01 on 2007-06-01
> **r76 said:**
> Thanks for a brilliant guide, I used it to back up my ubuntu and xp partitions.  I hope I never have to test if it works ;)  Still, the backup didn't mention any errors and I did it on to an external ext3 hard drive - exactly what I wanted to do.  I like that it runs like a live CD while no hard drive is mounted or OS running.  One question is why frank golden uses extra commands for mount ([on the system rescue cd forums]("http://www.sysresccd.org/forums/viewtopic.php?t=790")):
```
mount [COLOR="Red"]-t vfat[/COLOR] /dev/xxxx /backup
```
for FAT32 (where xxxx is sda1 or whatever) and
```
mount [COLOR="#ff0000"]-t ext3[/COLOR] /dev/xxxx /backup
```
for ext3, but I guess that's a question for him not you.

Have you tried using the gzip option again yet?  I didn't, just in case.  Anyway, many thanks again :D
Hi, 

Nope, I have not tested the GZIP thing in the meantime. I did so a while ago when I wrote the tutorial, but it failed. So I don't know if it works now...

---

### Post by r76 on 2007-06-18
> **r76 said:**
> Thanks for a brilliant guide, I used it to back up my ubuntu and xp partitions.  I hope I never have to test if it works ;)

Well I did just use this method to restore my / partition after installing a bunch of stuff which slowed my machine - following your guide to the letter it worked perfectly (and only took a few minutes).  Thanks again!

---

### Post by yodog on 2007-06-24
> **Lucifiel said:**
> Okay, I finally managed to get around to restoring my image of Ubuntu, with Partimage.

What I did was restore my 4.9 gb image to a 20 gb partition.

Now, here's my question: What on earth happened to the other 15 gb?! My partition, dev6 is reported as having 5.5 gb of space and having 600++ mb of free space. :(

Under Gparted, it says that 16.99 gb of 20 gb is used.

Edit: Okay, so having searched around some more, I found out that you need to use a tool or Gparted or some commands to resize the partition?

Hello Lucifiel,

I got the same result upgrading my notebook from a 60GB to a 80GB HDD... The total space that's available after restoring the backup in the new HDD is the same as in the old one, but Gparted shows that all 80GB is been used.

How did you solve this? Or may be someone can help me giving some directions, please!

---

### Post by thor918 on 2007-06-28
it would be cool to see an howtoo that deals with backing up the partition that linux is booted up with...
I'm in ubuntu, 
1. I got a backup hd that is mounted
2. I wan't to backup the partition that is mounted as /

---

### Post by wieman01 on 2007-06-28
Guess 'rsync' would do the job... Have you heard of it?

---

### Post by thor918 on 2007-06-28
> **wieman01 said:**
> Guess 'rsync' would do the job... Have you heard of it?

thanks.
I have heard of it, and it may work, but I'm monstly looking for gui enabled options.

---

### Post by wieman01 on 2007-06-28
You may try this:

[http://www.debianhelp.co.uk/rsyncweb.htm]("http://www.debianhelp.co.uk/rsyncweb.htm")

That's an GUI for Gnome with limited functionality.

---

### Post by thor918 on 2007-06-28
> **wieman01 said:**
> You may try this:

[http://www.debianhelp.co.uk/rsyncweb.htm]("http://www.debianhelp.co.uk/rsyncweb.htm")

That's an GUI for Gnome with limited functionality.

thanks.. I found several interesting links there.

I like the simplicity of this one:
[http://www.opbyte.it/grsync/screenshot.html](http://www.opbyte.it/grsync/screenshot.html)
do you think that is enough to do a complete system restore with that one?

---

### Post by wieman01 on 2007-06-28
> **thor918 said:**
> thanks.. I found several interesting links there.

I like the simplicity of this one:
[http://www.opbyte.it/grsync/screenshot.html](http://www.opbyte.it/grsync/screenshot.html)
do you think that is enough to do a complete system restore with that one?
All that I can say is that you should try. :-) Looks promising.

---

### Post by SilverWave on 2007-07-30
A worked example

3 drives 500gb each
/dev/sda
/dev/sdb
/dev/sdc

/dev/sda1 20gb xp ntfs
/dev/sda5 20gb ntfs blank for testing
/dev/sdb1 500gb ext3 for backups (b for backups ... ;) it works for me).
Boot from knoppix disk, at boot prompt enter: knoppix toram lang=uk
Off the k menu there is a group for &#8220;KNOPPIX&#8221; find the item &#8220;change root password&#8221;
Enter a password e.g &#8220;root&#8221;

(This bit is so I can check that the image is a good copy after restore and id any corrupt files.)
_______________________________________________
Use the disk icon to mount /media/sda1 rc and enable r/w.
Open a root terminal enter the following: 

cd /media/sda1
find  . -type f   2>/dev/null  -exec md5sum {} \; >check.md5

Once this has completed umount /media/sda1
_______________________________________________

mount -t ext3 /dev/sdb1 /backup

I find that mounting the backup partition as /backup and not /media/sdb1 is the single most helpful thing you can do to help ensure you do not use the wrong partitions.

I followed the rest of the how to except I used the gzip option and then restored to /dev/sda5

To check that the image was not corrupt open a root terminal and enter the following command:

cd /
cd /media/sda5
md5sum -c check.md5 

or 

cd /
cd /media/sda5
md5sum -c check.md5 > /backup/bak-070730a.log

You should receive 1 md5 warning ( that should be the check.md5 file itself).

I received 1 more warning regarding an other file.
Remember that this was a ntfs partition and this support is still experimental.
I will redo this test and see if anything changes &#8211; also I will test some ext3 partitions and report the results.

If anyone else could run the md5sum check (before and after) and report that would allow us to gauge how accurate the copying is.

[EDIT] ran the md5sum -c check.md5 on the original partition just to be safe and the same file is failing the check here as well!!!
So that seems to be good news... in that the image is a faithful copy after all [img]http://ubuntuforums.org/images/smilies/smiley-faces-75.gif[/img]

Thanks for the howto I would have past on partimage without it.

Note: I would recommend using knoppix as it has the best hw support and you get a fully functional  desktop with the toram option its also blazingly fast.

---

### Post by rainbowed_man on 2007-07-30
> **tedrogers said:**
> I've seen your Psychocats tutorial...it's very good...but I wonder if when I type:

```
sudo fdisk -l
```

...why is it that it doesn't show my network drives as well? Should it?

Maybe Samba isn't setup right.

fdisk shows the partition information of your hard drive(s). Mounting over Samba does not create any new hard drive at all, it only makes the GNU/Linux filesystem recongize that (insert directory here) has been associated to Samba, and will forward on any requests, changes to the directory, etc over to Samba, which then forwards the request/change/etc over the network to a Samba server which the directory is associated with.

It should not show your network drives. The network is completely seperate from what you _do_ at the terminal, and should stay that way.

---

### Post by SilverWave on 2007-08-04
Just a quick note to confirm partimage, used as per the instructions in this howto, works as advertised.

I have used a combination of tools on the knoppix cd; gparted;
partimage and this howto to replace my use of trueimage.

I have created images of partitions with hundreds of thousands of file some very small others multi gb all with no corruption when restored.

A couple of observations:

1. it is LOTS faster to do a straight copy with no gzip.
2. size does matter, if you receive an error it could just be that the partition is a little smaller than needed. Add a couple of % and try again.

I had some issues (locking up) with the knoppix cd which I am attributing to using the toram boot option.
If I used my normal boot option of "knoppix lang=uk"I had no such issues.

---

### Post by paker on 2007-08-04
When I installed Feisty, I wasn't planning to use partimage and put all 200 gb in one partition. So I have no partition to backup hda1 to.

I have an old slower 30gb IDE hard disk sitting on the shelf. Can I connect this to the computer and backup hda1 to this? How actually do I do that? Just connect the cable to it? Or should I format it? Will Feisty prompt me to format it?

Thanks.

PS: If this post is irrelevant, please make a separate thread for me.

---

### Post by HermanAB on 2007-08-04
Hmm, next time you install Linux, be sure to make more partitions.  For a home desktop, you really should have /, /swap and /home as a minimum.  That ensures that when you re-install Linux (for whatever reason) you can do so without overwriting /home and losing all your family photos and schtuff.

Regarding the old HDD:
By all means plug it in. 
If it is a SATA, then it goes on its own cable - just plug it in.
If it is an IDE, move the jumper to make it a Slave and plug it in, preferably with your CDROM - since a CDROM is hardly ever used, so then you'll get maximum speed out of the HDD.

You then need to run the hardware wizard and format the disk as Ext3 and mount it, say as /data or whatever you wish to call it.

'Hope that helps!

Herman

---

### Post by wieman01 on 2007-08-05
> **HermanAB said:**
> Hmm, next time you install Linux, be sure to make more partitions.  For a home desktop, you really should have /, /swap and /home as a minimum.  That ensures that when you re-install Linux (for whatever reason) you can do so without overwriting /home and losing all your family photos and schtuff.

Regarding the old HDD:
By all means plug it in. 
If it is a SATA, then it goes on its own cable - just plug it in.
If it is an IDE, move the jumper to make it a Slave and plug it in, preferably with your CDROM - since a CDROM is hardly ever used, so then you'll get maximum speed out of the HDD.

You then need to run the hardware wizard and format the disk as Ext3 and mount it, say as /data or whatever you wish to call it.

'Hope that helps!

Herman
Just a note to say that FAT32 will do as well. There is no need to format the HD if it's not an EXT3. Apart from this I agree with your comments. Partitioning in the first place is absolutely necessary.

---

### Post by SilverWave on 2007-08-13
> **SilverWave said:**
> Just a quick note to confirm partimage, used as per the instructions in this howto, works as advertised.



Tried restoring a 100gb partition and received a compression error.
In testing found I always get a least 1 crc error on 100gb images... so tried no compression same problem... tried splitting to the 2gig default received a crc error. on part 4 of 16.

:(

I am saving these images to a 500gb drive as were the smaller 10-20gb images which were successful.

I would suggest that at a minimum that you need to test each newly created image and see if they are valid.

May have to go back to trueimage. sigh

---

### Post by wieman01 on 2007-08-14
> **SilverWave said:**
> Tried restoring a 100gb partition and received a compression error.
In testing found I always get a least 1 crc error on 100gb images... so tried no compression same problem... tried splitting to the 2gig default received a crc error. on part 4 of 16.

:(

I am saving these images to a 500gb drive as were the smaller 10-20gb images which were successful.

I would suggest that at a minimum that you need to test each newly created image and see if they are valid.

May have to go back to trueimage. sigh
The file system might be corrupt. I had that once so I had to 'force-check' the HD.

Do this from command line:
> sudo touch /forcefsck
Then restart the PC into Ubuntu. The system will check your HD and eliminate HD errors.

Any better?

---

### Post by SilverWave on 2007-08-16
Yes thanks, that worried me as well, I was relieved when the check reported no problems.  

I have had a bit of a blitz on researching different backup strategy's...

My thoughts are now along these lines:
A comment about single image file backups (or single compressed archive backups) being brittle has struck a cord with me.

That is, the observation that any slight damage to a image file makes it impossible to restore any part of it.

If such an error occurs to just one file in a collection of files then it is not, necessarily, such a catastrophic loss.  

With this in mind I have tested a number of alternatives to partimage.

Criteria
======
1/. Reliability/fidelity is everything.
2/. The application must be well supported, also a package must exit in the Ubuntu repositories (if its included in knoppix as well, thats bonus points).
3/. The backup process should be painless and efficient and it should be easy to confirm the fidelity of the copy.
4/. A preference for a solution that provides a mirror/snapshot with access to individual files.
 
The solution I am going with is rdiff-backup.

I have just tested backing up 'home'.
35gb in 24mins, the next backups will just be the diffs - so *much* quicker.

The basic command couldn't be easier:
e.g.
rdiff-backup /home /media/backup/home

What I end up with is a mirror of /home at  /media/backup/home

restoring is just a '-r' away if you just want the latest backup:
rdiff-backup -r now /media/backup/home /tmp/home

or 

From a backup 10 days ago:
rdiff-backup -r 10D /media/backup/home /tmp/home

Next a more realistic test ... backing up '/ ' :D

The command I have came up with is:
rdiff-backup --exclude /media --exclude /tmp/'*' --exclude /var/tmp/'*' --exclude /mnt --exclude /proc --exclude /sys / /media/backup/mir/silver

Lot of testing ahead but I think I am finally on the right track...

Also if the problem is the disk this will highlight it ;)

notes:
[http://www.nongnu.org/rdiff-backup/index.html](http://www.nongnu.org/rdiff-backup/index.html)


Quote:
rdiff-backup:
A remote incremental backup of all your files could be as easy as
"rdiff-backup / host.net::/target-dir"[disclaimer]

---

### Post by wieman01 on 2007-08-17
> **SilverWave said:**
> Also if the problem is the disk this will highlight it ;)

notes:
[http://www.nongnu.org/rdiff-backup/index.html](http://www.nongnu.org/rdiff-backup/index.html)


Quote:
rdiff-backup:
A remote incremental backup of all your files could be as easy as
"rdiff-backup / host.net::/target-dir"[disclaimer]
Excellent. Sounds like a good alternative. I use 'rsync' most of the time but it can be incredibly slow. I'll give "rdiff-backup" a try.

---

### Post by MystaMax on 2007-08-27
First, let me say **thank you** for putting together such a guide. This could possibly save me a lot of time if I can restore properly and consistently.

I followed your guide and now have a backup image of my main Ubuntu install partition (sda4). But, **I'm having troubles restoring it to another hard drive**. The hard drive is the same exact make, model, and size. I think I know what my problem is, and just need some guidance to resolve it. I'm almost certain I'm doing something wrong w/ the restore process. Probably somewhere along the lines of restoring the MBR and properly restoring the partitions necessary to get my Ubuntu install running again on a different hard drive. Here's a screenshot of my partitions:

[IMG]http://tavdash.com/my_images/partitions.png[/IMG]

I have one hard drive (sda) 3 logical (sda1, sda2, and sda4) partitions, and 1 extended partitions (sda3). **sda2 has the boot flag (does that mean it contains the MBR?)** The extended partiton contains 3 other partitions. Those are: sda5/ext3, sda7/linux-swap, and sda6/sda6. My sda5 partition is for music/photos/videos. My sda6 is my /home partition.

**Which partitions do I need to restore for a bootable ubuntu install?** sda2 (windows partition) contains the boot flag. I want to attempt and restore ubuntu w/o windows and any windows partition. Do I reinstall grub using the liveCD as suggested before (how is this done)? When reinstalling grub is the MBR automatically put back?

I'm assuming its mandatory to restore sda4, sda6, and sda7 to have a working linux install after backing up w/ partimage. Do i create the partitions w/ gparted and then restore? I'm just not sure what order to go in to get this right.

---

### Post by wieman01 on 2007-08-28
@MystaMax:

What partitions / drive do you want to restore the images to? Basically you could use any partition as long as it is a Ext3 and has enough space for the images. 

As for the 'bootable' flag, don't worry about that. But you will have to restore/reinstall GRUB once you have moved the partitions and [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub") ("Using the Desktop/LiveCD and Overwriting the Windows bootloader") is a good starting point. Moreover you will have to change settings in...
> gedit /etc/fstab
I suggest that you open a new thread and ask others for support here if you have not done it yet. I went through the procedure and it can be tricky. A full backup of your system is advisable.

Just send me the link once you have your own thread.

_**EDIT:**_
Actually you should take a look at this site as well:

[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by MystaMax on 2007-08-28
> **wieman01 said:**
> @MystaMax:

What partitions / drive do you want to restore the images to?

Are you implying I should have the partitions already created on the receiving hard drive? And then use partimage to restore to the empty partitons?

> 
_**EDIT:**_
Actually you should take a look at this site as well:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)


That link is great! Lots of information. Screenshots of the whole grub reinstall, perfect. Too late to start tonight, I'll have detailed results tomorrow. Thanks for the quick response!

---

### Post by wieman01 on 2007-08-28
> **MystaMax said:**
> Are you implying I should have the partitions already created on the receiving hard drive? And then use partimage to restore to the empty partitons?
Yes, exactly. That's the best way to move partitions. If you need a hand  with it, send me a message. 

Use the LiveCD and GParted to do all the dirty work like creating new partitions, removing old ones, changing "fstab" & GRUB, etc. Herman's site will shed some light on the issue.

---

### Post by Rick Z on 2007-09-05
Hi I am trying to figure out how to use partimage.  I just install the partimage, but when I was trying to backup /tmp dir.  I received error that the directory must umount.  So, I went to command line and sudo the security where I become root to umount the /tmp.  I wasn’t able to umount the /tmp or umount /dev/sda7 (which is the /tmp directory).  The error message is saying that the directory is busy.  I even try the following command umount –f –v /dev/sda7 or umount –f –v /tmp yet I still received the same error message.  I also tried the webmin to umount the /tmp directory, but I was not able to do so either.  I have also try some other directory like /home, /var, /opt, and /boot.  None of those directories allow me to umount.  When I boot up using LiveCD, I am able to mount/umount.  

Please help…

---

### Post by wieman01 on 2007-09-06
> **Rick Z said:**
> Hi I am trying to figure out how to use partimage.  I just install the partimage, but when I was trying to backup /tmp dir.  I received error that the directory must umount.  So, I went to command line and sudo the security where I become root to umount the /tmp.  I wasn’t able to umount the /tmp or umount /dev/sda7 (which is the /tmp directory).  The error message is saying that the directory is busy.  I even try the following command umount –f –v /dev/sda7 or umount –f –v /tmp yet I still received the same error message.  I also tried the webmin to umount the /tmp directory, but I was not able to do so either.  I have also try some other directory like /home, /var, /opt, and /boot.  None of those directories allow me to umount.  When I boot up using LiveCD, I am able to mount/umount.  

Please help…
You cannot umount any of the root folders while the system is up & running. I would assume that the consequences could be disastrous. That's why using Rescue CD is recommended in this case.

---

### Post by syncdram on 2007-09-09
I'v been trying to use partimage for about 1 month now. with no success. I'm using fiesty fawn. I'v done my home work printed out how to posts ect. 

my problem is i can get the program to run for the first 19 percent then it says disk is full!. 

no matter what thread i try to use for copying a partition to either another partition or to a usb backup drive its always the same. disk is full! at 19 percent.  all the post make it seem so easy i guess it should be but what am i doing wrong?? can somebody please take the time to help me? Ken

---

### Post by wieman01 on 2007-09-10
> **syncdram said:**
> I'v been trying to use partimage for about 1 month now. with no success. I'm using fiesty fawn. I'v done my home work printed out how to posts ect. 

my problem is i can get the program to run for the first 19 percent then it says disk is full!. 

no matter what thread i try to use for copying a partition to either another partition or to a usb backup drive its always the same. disk is full! at 19 percent.  all the post make it seem so easy i guess it should be but what am i doing wrong?? can somebody please take the time to help me? Ken
What maximum files size have you chosen? What file system are you using on the target hard drives? 

This is really odd.

---

### Post by r76 on 2007-09-10
> **syncdram said:**
> I'v been trying to use partimage for about 1 month now. with no success. I'm using fiesty fawn. I'v done my home work printed out how to posts ect. 

my problem is i can get the program to run for the first 19 percent then it says disk is full!

I get a similar message about half the time I run partimage - in my case it's because I have forgotten to specify [COLOR="Red"]/backup[/COLOR]/backupfilename (in the case that I mounted my external drive as /backup) and it's creating the backup in ramdisk memory (and hence is always the same size = my ram - sytem rescue cd ram requirement).

I find it quite embarassing but at least I realise straight away now! :)

---

### Post by syncdram on 2007-09-10
The partition i want to back up is 3.9 gig linux ext 3 and the partiton i'm backing up to is on the same drive with a ext3 partition of 128 gig. I use the default settings like all the posts say to do. i'm messing up on the image file to creat/use section. its going into ram like you said

---

### Post by syncdram on 2007-09-10
I tried using g4l it works but it just takes so long. I want to use partimage

---

### Post by syncdram on 2007-09-10
Ok, this is what i have.  1 hard drive with 2 partitions. linux is on /dev/sda3 ext3. its a 24.8g partition and of this partition 4.7 g is used. the next partition is a new ext3 partition at 122.81 gig with 2.11g used. I want to part image /dev/sda3 to dev/sda1. If you were sitting at my computer right now type out exactly what you would do. You can use whatever name you want.  Keep in mind what you would be looking at on the screen and any changes you would make. I'm at my witts end.

---

### Post by wieman01 on 2007-09-11
@syncdram:

Ok, I'll walkt you through it. :-)

Make a backup directory first:
> mkdir /backup
Then mount the device you want to store the backup image to:
> mount /dev/[COLOR="Red"]sda1[/COLOR] /backup
Now start 'partimage':
> partimage
And choose an arbitrary file name for your backup image:
> /backup/[COLOR="Red"]your_backup_file[/COLOR]
Any error messages?

---

### Post by syncdram on 2007-09-11
wieman 01, well after printing out what you did for me and 3 trys later it finaly WORKED! This is what i did. mkdir /backup.   mount /dev/sda1 /backup. Then i did df -f to make sure that drive was mounted and low and behold it was!. Ok then i partimaged. Then i typed in /backup/hda3/backup. Kept all the default settings all but i asked it to quit when done. And it worked! I bruzed both knees from jumping up from my desk! but i had to try it again and it worked like a charm.  Ok now that i'm commed down from all the excitment I'd like to say thank you!. 

What about restoring? from the information i just gave you could you help me out with that to?  I haven't even looked at that yet.  Ken

---

### Post by wieman01 on 2007-09-11
> **syncdram said:**
> wieman 01, well after printing out what you did for me and 3 trys later it finaly WORKED! This is what i did. mkdir /backup.   mount /dev/sda1 /backup. Then i did df -f to make sure that drive was mounted and low and behold it was!. Ok then i partimaged. Then i typed in /backup/hda3/backup. Kept all the default settings all but i asked it to quit when done. And it worked! I bruzed both knees from jumping up from my desk! but i had to try it again and it worked like a charm.  Ok now that i'm commed down from all the excitment I'd like to say thank you!. 

What about restoring? from the information i just gave you could you help me out with that to?  I haven't even looked at that yet.  Ken
No problem. 
> mkdir /backup
> mount /dev/[COLOR="Red"]sda1[/COLOR] /backup
> partimage
Now restore from your backup image:
> /backup/hda3/[COLOR="Red"]backup.000[/COLOR]
Then follow the HOWTO. Note the [COLOR="Red"]".000"[/COLOR] suffix. How did that go? You can select the "simulation of restoration" option to test the process/image first.

---

### Post by syncdram on 2007-09-11
I'm going to try the restore on a practice drive.  I'm a bit weary of deleting my linux partition just yet. With your help I not only backed up my desktop i'm now backing up my laptop as we speak. The only difference is i have to use ntfs-3g /dev/sda1 /mnt/windows. and its working. Restoring this is a nother venture i guess.  I'll keep in touch with you. I printed out the restore instructions as well. You have been a GREAT help to a new linux user. Thanks again. Ken.

---

### Post by shane2peru on 2007-09-24
Wieman01,

  Thanks for the great how to!!!  I have used partimage in the past but had forgotten about it.  Plus the lack of an automatic backup is a bit annoying, but I will have to deal with that.  I'm considering installing a small linux distro (puppylinux or xubuntu) so that I can boot into that and back up via partimage instead of using the LiveCD method as it should boot and run faster.  Thanks for the howto!

Shane

---

### Post by r76 on 2007-09-26
> **syncdram said:**
> I'm going to try the restore on a practice drive.  I'm a bit weary of deleting my linux partition just yet. With your help I not only backed up my desktop i'm now backing up my laptop as we speak. The only difference is i have to use ntfs-3g /dev/sda1 /mnt/windows. and its working. Restoring this is a nother venture i guess.  I'll keep in touch with you. I printed out the restore instructions as well. You have been a GREAT help to a new linux user. Thanks again. Ken.

Did this work out ok for you?  I've used this how to loads of times, I feel it is the best possible backup startegy for me as I'm constantly trying out new distros but want to be able to get straight back to a couple of favourites in a matter of minutes.

Anyway, last time I tried it, I tried backing up on to an NTFS drive - it seemed to work ok (except it took ~20 mins to back up a total of 5GB, onto an ext3 disk takes less than 3 minutes) and when I rebooted afterwards I couldn't find the backup files on the disk.

It's the first time I tried saving onto NTFS from partimage and it didn't work.  The external drive is identical to the ext3 one I normally use, just formatted differently. I wondered if anyone else had success.

---

### Post by shane2peru on 2007-09-27
I came across this web page while looking for a non CD solution to backing up, this is a must read!
[URL="http://www.swerdna.net.au/linhowtorescuecd.html"]
http://www.swerdna.net.au/linhowtorescuecd.html[/URL]


Shane

**EDIT:**  OK, I did this and it works great!!! Wow, I'm very impressed with this method.  It is similar to the method described here, except you are not tied to a cd.  Great system.

---

### Post by Yoke &amp; Chung on 2007-10-06
Forgive my ignorance. I am trying to restore my image created from another drive. How do you select the options in partimage?

The default setting is (*) on save/create backup
How do I select the restore partition? Tried many different keys and couldn't mark "*" on the restore option.

Thanks in advance

---

### Post by wieman01 on 2007-10-07
> **Yoke & Chung said:**
> Forgive my ignorance. I am trying to restore my image created from another drive. How do you select the options in partimage?

The default setting is (*) on save/create backup
How do I select the restore partition? Tried many different keys and couldn't mark "*" on the restore option.

Thanks in advance
You need to mount the restore device. Is it listed here?
> fdisk -l
Then simply choose your device and mount it as described in the tutorial.

---

### Post by Yoke &amp; Chung on 2007-10-07
Thanks for your reply.
Yes, the 2nd hard disk containing the backup is mounted. The 1st disk to be restored is unmounted as per the instruction.

I am actually stucked at the Partimage software itself. I am on the first screen where you select the partition, and I keyed in the image file name and location. However, I do not know how to select "restore partition from an image file" as the default is "save partition into a new image".

I moved the cursor the "restore partition..." but can't seem to select it. What key should I press to select the option?

Thanks.

---

### Post by wieman01 on 2007-10-07
> **Yoke & Chung said:**
> Thanks for your reply.
Yes, the 2nd hard disk containing the backup is mounted. The 1st disk to be restored is unmounted as per the instruction.

I am actually stucked at the Partimage software itself. I am on the first screen where you select the partition, and I keyed in the image file name and location. However, I do not know how to select "restore partition from an image file" as the default is "save partition into a new image".

I moved the cursor the "restore partition..." but can't seem to select it. What key should I press to select the option?

Thanks.
Ah... you can change options using the Tab key on you keyboard? Tried that yet? Just press it and the cursor will jump from option to option.

---

### Post by gimpguy2000 on 2007-10-07
Well, I followed this method as it seems one of the best, however, I can't mount any device when using it. I booted to the rescue disk, when I type in fdisk -l, It sees all the drives. I have another hard drive ext3, nothing on it but when I want to mount it, eg. mount /dev/hdb  it tells me not found in etc/fstab or anywhere.  When I start Ubuntu, it is listed and mounted and I can write to it. Any Ideas why this would happen?

TX

Paul

---

### Post by wieman01 on 2007-10-08
> **gimpguy2000 said:**
> Well, I followed this method as it seems one of the best, however, I can't mount any device when using it. I booted to the rescue disk, when I type in fdisk -l, It sees all the drives. I have another hard drive ext3, nothing on it but when I want to mount it, eg. mount /dev/hdb  it tells me not found in etc/fstab or anywhere.  When I start Ubuntu, it is listed and mounted and I can write to it. Any Ideas why this would happen?l
Mmm... What about:
> mount /dev/hdb**[COLOR="Red"]1[/COLOR]** /mnt
You have probably picked the wrong device?

---

### Post by ru0n on 2007-10-08
Newbie Help!
I managed to find out what my partitions are...
sda1*(boot) start:1 end:9562 blocks: 76806733+ system: linux
sda2 start: 9563 end: 9726 blocks: 1317336 system: extended
sda5 start: 9563 end: 9726 blocks: 1317298+ system: swap solaris

Even with the tutorial, I do not know what exactly i need to do with mounting and un-mounting.

And what's this about? -> for nr in 1 2 3 6 7 8 ; do partimage -z1 -b -o -d save /dev/hda$nr /mnt/temp1/hda$nr.img.gz ; done

?????

All I want to do is save my current settings (image/iso) on a cd and then put it on 4other computers with the same hardware. 

I also heard of dd(disk dump) but i've got no clue how that works and i think partimage is easier to do what i want.

Seriously Confused.
:confused:

---

### Post by wieman01 on 2007-10-08
This is going to be a bit complicated, but not impossible. :-) If you are patient, we will manage this together. 

First of all, I believe that "sda1" stands for your Linux install. When you open Gnome's Partition Manager, can you confirm that? Linux resides on one single partition, is that correct? If you can confirm the name of the partition (e.g. sda1), we can pull a backup first and then burn it on to a DVD.

---

### Post by ru0n on 2007-10-08
> **wieman01 said:**
> This is going to be a bit complicated, but not impossible. :-) If you are patient, we will manage this together. 

First of all, I believe that "sda1" stands for your Linux install. When you open Gnome's Partition Manager, can you confirm that? Linux resides on one single partition, is that correct? If you can confirm the name of the partition (e.g. sda1), we can pull a backup first and then burn it on to a DVD.

Okay here it goes:
sda1*(boot) start:1 end:9562 blocks: 76806733+ system: linux
It seems to be mounted... also it's ext3 (what ever that is)
Used: 5%/ Not used: 95%

---

### Post by wieman01 on 2007-10-08
> **ru0n said:**
> Okay here it goes:
sda1*(boot) start:1 end:9562 blocks: 76806733+ system: linux
It seems to be mounted... also it's ext3 (what ever that is)
Used: 5%/ Not used: 95%
So your Linux install resides on one single partition named "sda1". Can you confirm that? If so, it should be easy.

---

### Post by ru0n on 2007-10-08
> **wieman01 said:**
> So your Linux install resides on one single partition named "sda1". Can you confirm that? If so, it should be easy.

Yeah i can confirm it. It's the only one being used.

---

### Post by gimpguy2000 on 2007-10-08
> **wieman01 said:**
> Mmm... What about:

You have probably picked the wrong device?

Thanks, I'll try the mnt at the end and see what happens. Yeah, it's the right device "unfortunately" lol. It couldn't ever be that easy for me. ;) But I will give this a try later and see how it goes.  What I was typing exactly is  mount /dev/hdb1/backup

Paul

---

### Post by wieman01 on 2007-10-08
Can we use "sda2" to store your data? Then we would mount it (we do NOT mount "sda1", Partimage will do that for us):
> mkdir /backup
> mount /dev/[COLOR="Red"]sda2[/COLOR] /backup
> partimage
Then follow the tutorial. Select "sda1" since we want to pull a backup of it.

---

### Post by ru0n on 2007-10-08
> **wieman01 said:**
> Can we use "sda2" to store your data? Then we would mount it (we do NOT mount "sda1", Partimage will do that for us
Then follow the tutorial. Select "sda1" since we want to pull a backup of it.

When i put in:

mount /dev/sda2 /backup

I get something like this:
Squashfs error can't find superblock on sda2
Fat bougs number reserved sectors
mount specifc filesystem typ...
help!
:confused:

---

### Post by wieman01 on 2007-10-08
> **ru0n said:**
> When i put in:

mount /dev/sda2 /backup

I get something like this:
Squashfs error can't find superblock on sda2
Fat bougs number reserved sectors
mount specifc filesystem typ...
help!
:confused:
I see... It is NTFS, isn't it? I need to check how to mount NTFS volumes. Slipped my mind, but I will check when I get back home.

Do you have a FAT32 HD by chance? An external (e.g. USB) device would do.

---

### Post by ru0n on 2007-10-08
Yes, it's got 500GB. (is that enough?)

---

### Post by wieman01 on 2007-10-08
> **ru0n said:**
> Yes, it's got 500GB. (is that enough?)
What file system is it? NTFS will be a problem... Not sure if Rescue CD gives you write access to a NTFS file system.

---

### Post by ru0n on 2007-10-08
> **wieman01 said:**
> What file system is it? NTFS will be a problem... Not sure if Rescue CD gives you write access to a NTFS file system.

Should be Fat32, how can i check?

---

### Post by wieman01 on 2007-10-08
> **ru0n said:**
> Should be Fat32, how can i check?
Checking with Windows would be best. I think it is under "properties" when you do a right-click on the drive icon. 

If it is FAT32 then I'll post the command later on. But FAT usually does not require that you specify the files system.

---

### Post by ru0n on 2007-10-08
> **wieman01 said:**
> Checking with Windows would be best. I think it is under "properties" when you do a right-click on the drive icon. 

If it is FAT32 then I'll post the command later on. But FAT usually does not require that you specify the files system.

It's a Western Digital My Book 500GB... should be a FAT32...

Found from some Site:
Other Thoughts: this drive comes FAT32 fotmatted so if you primarily use windows I would recommend reformatting to NFTS (for 500GB the reformat went pretty fast, which is a good sign)...i assume their thinking was FAT32 works for a Mac or PC, but NFTS defintely more stable for windows IMO

---

### Post by wieman01 on 2007-10-08
> **ru0n said:**
> It's a Western Digital My Book 500GB... should be a FAT32...

Found from some Site:
Other Thoughts: this drive comes FAT32 fotmatted so if you primarily use windows I would recommend reformatting to NFTS (for 500GB the reformat went pretty fast, which is a good sign)...i assume their thinking was FAT32 works for a Mac or PC, but NFTS defintely more stable for windows IMO
If the volume/device is empty it would be easier to reformat it and use "ext3" instead. Only while we are pulling the backup. You can reformat it later on. Would that be an option? 

You can format it using Gnome's partition editor (ext3).

---

### Post by ru0n on 2007-10-08
> **wieman01 said:**
> If the volume/device is empty it would be easier to reformat it and use "ext3" instead. Only while we are pulling the backup. You can reformat it later on. Would that be an option? 

You can format it using Gnome's partition editor (ext3).

Yes it would be a option... i'll just need to back up the files that are on it right now. 

How can i format it with Gnome's partition Editior?

When i've formated it? What then?

---

### Post by wieman01 on 2007-10-09
> **ru0n said:**
> Yes it would be a option... i'll just need to back up the files that are on it right now. 

How can i format it with Gnome's partition Editior?

When i've formated it? What then?
Apparently you have not used Partition Editor before. That is how you use it:

[http://gparted.sourceforge.net/documentation.php]("http://gparted.sourceforge.net/documentation.php")

The reason why I suggest to use EXT3 rather than FAT32 is that FAT32 cannot cope with file larger than 4 GB. And that would be a potential stumbling block.

Alternatively you can resize your external hard drive and create a small ext3 partition. This way you don't have to reformat the whole drive and delete file. 

If you have problems doing that, I would open a new thread for this exercise only (send me the link by PM). We continue here later on. What do you think?

---

### Post by gimpguy2000 on 2007-10-09
Howdy,

Well I tried the mnt, and I also listed into each directory and it will not mount nor is it found in etc/fstab or anywhere. The only time I can see it is if I'm booted into Ubuntu or if I fdisk -l.  I admit, i'm stumped :confused: 

Thanks for the help so far..

Paul

---

### Post by ru0n on 2007-10-09
Okay i've managed to make it ext3... What now?

---

### Post by wieman01 on 2007-10-09
> **ru0n said:**
> Okay i've managed to make it ext3... What now?
Well, plug it in and follow the HOWTO. :-)

What devices are listed when you do a: 
> fdisk -l

---

### Post by ru0n on 2007-10-09
There was some Success Message... then i pressed okay... 

now there's a blue screen that tells me to please wait. what now?

---

### Post by wieman01 on 2007-10-09
> **ru0n said:**
> There was some Success Message... then i pressed okay... 

now there's a blue screen that tells me to please wait. what now?
Still there? If yes, please press 'ctrl c' to exit. 

Now you have a complete image of your install on the HD. Do you see the file?

---

### Post by ru0n on 2007-10-09
Okay i've got some sda1.000 file.... What now?

---

### Post by gimpguy2000 on 2007-10-09
Ok, got all mounting in order and could "potentially" perform a backup. I notice it says to choose no compression. I can't edit my settings or move the (*) to another option and only the default options remain. Is there a way to change this? 

Thanks

Paul

---

### Post by wieman01 on 2007-10-10
> **ru0n said:**
> Okay i've got some sda1.000 file.... What now?
Burn it on a DVD using K3B or any other burning program. Then reinstall it on the other system following my tutorial. Have you seen that section?

---

### Post by wieman01 on 2007-10-10
> **gimpguy2000 said:**
> Ok, got all mounting in order and could "potentially" perform a backup. I notice it says to choose no compression. I can't edit my settings or move the (*) to another option and only the default options remain. Is there a way to change this? 

Thanks

Paul
Yeah, you can move the cursor by pressing the TAB button. Could you try?

---

### Post by gimpguy2000 on 2007-10-10
> **wieman01 said:**
> Yeah, you can move the cursor by pressing the TAB button. Could you try?

Thanks, but I tried the tab button and it wouldn't do anything besides cycle through windows/er...the little option windows that is. I would have replied sooner but didn't think you'd be on here late so sorry bout that. 

Paul

EDIT, oops, yeah it moves the cursor but the   *  won't switch. <<At first what I thought you meant. It's been a looonnggg day. lol.

---

### Post by ru0n on 2007-10-10
> **wieman01 said:**
> Burn it on a DVD using K3B or any other burning program. Then reinstall it on the other system following my tutorial. Have you seen that section?

I've installed K3B... but somehow it cant find the dvd to burn it on. :(
(as what file typ should i burn it on the cd?)

---

### Post by wieman01 on 2007-10-10
> **ru0n said:**
> I've installed K3B... but somehow it cant find the dvd to burn it on. :(
(as what file typ should i burn it on the cd?)
Hang on... You want to install the image on all other PCs, correct? Then the DVD is a no-go... Because in order to do so, you need to load the Rescue CD and unless you have 2 DVD drives, you are stuck.

Why don't you leave the image on the drive and load it via USB using your other PCs? Just install right from the drive, not DVD. That will be perfectly fine.

---

### Post by wieman01 on 2007-10-10
> **gimpguy2000 said:**
> Thanks, but I tried the tab button and it wouldn't do anything besides cycle through windows/er...the little option windows that is. I would have replied sooner but didn't think you'd be on here late so sorry bout that. 

Paul

EDIT, oops, yeah it moves the cursor but the   *  won't switch. <<At first what I thought you meant. It's been a looonnggg day. lol.
Lol... You can also move with the arrows I believe. Don't worry, just play around with your keyboard. :-) Although it is late.

---

### Post by gimpguy2000 on 2007-10-10
> **wieman01 said:**
> Lol... You can also move with the arrows I believe. Don't worry, just play around with your keyboard. :-) Although it is late.

I did and hit every key I could think of, it's like the settings are just stuck. I tried arrows, keypad, backspace, space, and everything else, nothing will move that little...er....* :) I'll be nice to it.  I will try a couple more things and if not, then I give up for tonight and will maybe figure it out tomorrow. Gnight all. Yawwwnnn 

Thanks,

Paul

---

### Post by wieman01 on 2007-10-10
> **gimpguy2000 said:**
> I did and hit every key I could think of, it's like the settings are just stuck. I tried arrows, keypad, backspace, space, and everything else, nothing will move that little...er....* :) I'll be nice to it.  I will try a couple more things and if not, then I give up for tonight and will maybe figure it out tomorrow. Gnight all. Yawwwnnn 

Thanks,

Paul
Oh no... Did you try a sledge hammer as well? Might help. ;-)

Seriously I'll check later on as well. I am not in front of my own computer, so I cannot help right now. But I'll find out for you. No worries.

---

### Post by gimpguy2000 on 2007-10-10
> **wieman01 said:**
> Oh no... Did you try a sledge hammer as well? Might help. ;-)

Seriously I'll check later on as well. I am not in front of my own computer, so I cannot help right now. But I'll find out for you. No worries.

Thanks, I thought I'd post one last time to let you know before you go on a needless search on my account, I did get it finally, I used the mouse but the * won't move even though it changes the setting, ok, that was good. However, I can't back my main partition onto another local drive, it keeps wanting to backup onto my OS drive instead of my ext3 backup drive. *sigh*, tomorrow is another day, lol. Thanks though and I appreciate the help. My wife is giving me the evil eye so I'd better go. 

Cheers,

Paul

---

### Post by wieman01 on 2007-10-10
> **gimpguy2000 said:**
> Thanks, I thought I'd post one last time to let you know before you go on a needless search on my account, I did get it finally, I used the mouse but the * won't move even though it changes the setting, ok, that was good. However, I can't back my main partition onto another local drive, it keeps wanting to backup onto my OS drive instead of my ext3 backup drive. *sigh*, tomorrow is another day, lol. Thanks though and I appreciate the help. My wife is giving me the evil eye so I'd better go. 

Cheers,

Paul
Ok, let's continue tomorrow then. We'll find a solution, I am sure.

---

### Post by wieman01 on 2007-10-10
> **ru0n said:**
> I've installed K3B... but somehow it cant find the dvd to burn it on. :(
(as what file typ should i burn it on the cd?)
ru0n:

When you have installed the images on the other PCs, you probably need to reinstall GRUB as well, so that you can boot the OS. Let me know how you go. Reinstalling GRUB is simple but not if you have to do so the first time.

---

### Post by gimpguy2000 on 2007-10-11
> **wieman01 said:**
> Ok, let's continue tomorrow then. We'll find a solution, I am sure.

Hi, sorry for a late reply here but been a bit under the weather. Far as I can tell, there isn't an easy way to backup to another drive. No matter what I choose, it only allows me to pick which to backup, obviously, but then proceeds to backup to the same partition without an option otherwise. I mounted the hdb1, I cd'd to it, created mkdir /backup but again, after choosing which part to backup, it will only backup to the selected part that I am backing up. 

Thanks,

Paul

---

### Post by wieman01 on 2007-10-12
> **gimpguy2000 said:**
> Hi, sorry for a late reply here but been a bit under the weather. Far as I can tell, there isn't an easy way to backup to another drive. No matter what I choose, it only allows me to pick which to backup, obviously, but then proceeds to backup to the same partition without an option otherwise. I mounted the hdb1, I cd'd to it, created mkdir /backup but again, after choosing which part to backup, it will only backup to the selected part that I am backing up. 

Thanks,

Paul
Did you mount the drive to "/backup" then?

---

### Post by gimpguy2000 on 2007-10-12
> **wieman01 said:**
> Did you mount the drive to "/backup" then?

Yep, I mounted the hdb1 to /backup but no love. Once I choose the part to backup, it will only backup to that partition regardless what I mount /backup as. Right now I am using "KEEP" which is very simple and backs up to the ext3 drive. I am thinking of staying with that, not because it's a simple GUI interface, I don't judge on looks, but it seems to be doing very well and backs up on timed increments etc....plus has restore feature. I don't know how well this truly is in the linux world but seems ok so far. I will still delve into the other a bit but have since given up on it. I appreciate the help though. 

TC

Paul

---

### Post by swoosh on 2007-10-13
Hi,

After I did the backup I have got files like backup.000, backup.001,...backup.00x of up to 2GBs each.

Is this correct?

If I want do a restore I will restore from backup.000..will I be prompted for backup.001 during the restoration or will it be a automated by partimage?

Thanks.

---

### Post by wieman01 on 2007-10-13
> **swoosh said:**
> Hi,

After I did the backup I have got files like backup.000, backup.001,...backup.00x of up to 2GBs each.

Is this correct?

If I want do a restore I will restore from backup.000..will I be prompted for backup.001 during the restoration or will it be a automated by partimage?

Thanks.

Yes, that is correct.. You will **not** prompted for any other backup file than .000. Promise. You could do a test restoration... Partimage gives you the option to do so. It is all automated.

---

### Post by swoosh on 2007-10-14
> **wieman01 said:**
> Yes, that is correct.. You will **not** prompted for any other backup file than .000. Promise. You could do a test restoration... Partimage gives you the option to do so. It is all automated.

Thanks for the info. Will try it out!

---

### Post by syncdram on 2007-10-15
Hi guys, ok thanks to my original post i'm able to use partimage to backup and restore. Now for the next question. Here is what i have: ubuntu linux wired to a wireless router. In the living room a labtop with xp and its wireless. can i use partimage to backup xp to a ubuntu partition that is already shared through smb?

---

### Post by wieman01 on 2007-10-16
> **syncdram said:**
> Hi guys, ok thanks to my original post i'm able to use partimage to backup and restore. Now for the next question. Here is what i have: ubuntu linux wired to a wireless router. In the living room a labtop with xp and its wireless. can i use partimage to backup xp to a ubuntu partition that is already shared through smb?
Mmm... sounds very challenging. I doubt you can do it for 2 reasons (but this is just my uninformed opinion):

a. The SAMBA share does not show up as partition. As soon as you mount it, you won't be able to back it up.
b. You can't back up a running Windows system as far as I know.

---

### Post by syncdram on 2007-10-16
[http://video.google.com/videoplay?docid=-3626316476246113239&q=partimage&total=8&start=0&num=10&so=0&type=search&plindex=1](http://video.google.com/videoplay?docid=-3626316476246113239&q=partimage&total=8&start=0&num=10&so=0&type=search&plindex=1)
I thought i'd ask. I came across this video. This is what i want to do. But no success. I can ifconfig eth0 xxx.xxx.x.xxx  ip address and mount the share and ping the pc but thats about it. :)

---

### Post by swoosh on 2007-10-17
> **syncdram said:**
> Hi guys, ok thanks to my original post i'm able to use partimage to backup and restore. Now for the next question. Here is what i have: ubuntu linux wired to a wireless router. In the living room a labtop with xp and its wireless. can i use partimage to backup xp to a ubuntu partition that is already shared through smb?

I have successfully backup from ubuntu-ubuntu via smb but I am not sure whether it works for windows-ubuntu.

When you attempted the backup, can partimage "see" your xp partition? 

If it is able to "see" the partition then you should be backup but I am not sure whether you can get the same system after you restore though.

And also, your machine is portable, you can bring it nearer to the router if possible to get it wired when performing a large backup like this because of losses and interference of signals over wireless network will cause your backup/restore be much slower than wired.

---

### Post by shane2peru on 2007-10-17
> **swoosh said:**
> I have successfully backup from ubuntu-ubuntu via smb but I am not sure whether it works for windows-ubuntu.

When you attempted the backup, can partimage "see" your xp partition? 

If it is able to "see" the partition then you should be backup but I am not sure whether you can get the same system after you restore though.

And also, your machine is portable, you can bring it nearer to the router if possible to get it wired when performing a large backup like this because of losses and interference of signals over wireless network will cause your backup/restore be much slower than wired.

I think this is going to be problematic, because I remember reading somewhere that partimage and ntfs (which is most likely what your XP computer is using for its filesystem type) don´t mix well.  

Shane

---

### Post by carloslosgrande on 2007-10-18
[FONT="Comic Sans MS"]I'm also having trouble with changing the default values (of systemrescue cd). I tried the tab key, amongst others, without any result.
I did save an image but its in gzip as I couldn't change this.
Then I tried to restore but couldn't change the default.
I read thru this thread and the others seem to have had success with tab key? Obviously I've missed something.
Also I'm a simple old man and new to this, so please keep it simple:)[/FONT]

---

### Post by wieman01 on 2007-10-18
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]I'm also having trouble with changing the default values (of systemrescue cd). I tried the tab key, amongst others, without any result.
I did save an image but its in gzip as I couldn't change this.
Then I tried to restore but couldn't change the default.
I read thru this thread and the others seem to have had success with tab key? Obviously I've missed something.
Also I'm a simple old man and new to this, so please keep it simple:)[/FONT]
No problem. :-) What about the "arrows"? Can you move the cursor using them?

---

### Post by carloslosgrande on 2007-10-18
[FONT="Comic Sans MS"]I can move the cursor with tab, arrows, mouse, backspace, whatever.
I can't change the *
I've tried shift*, ctrl*, delete, backspace
no luck.
Sorry my post wasn't clear on that.[/FONT]

---

### Post by swoosh on 2007-10-18
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]I can move the cursor with tab, arrows, mouse, backspace, whatever.
I can't change the *
I've tried shift*, ctrl*, delete, backspace
no luck.
Sorry my post wasn't clear on that.[/FONT]

You can try the space bar. It should work.

---

### Post by wieman01 on 2007-10-18
> **swoosh said:**
> You can try the space bar. It should work.
Yes, that is right. The pressing <space> will do.

---

### Post by carloslosgrande on 2007-10-19
[FONT="Comic Sans MS"]You know, I think thats the only one I didn't try.
I'll get back to you after I give it a go.[/FONT]

---

### Post by carloslosgrande on 2007-10-19
[FONT="Comic Sans MS"]Ok. Yes space bar works but only if I change the initial setup to [COLOR="Magenta"]'uk[/COLOR]' keyboard, even though I actually have a '[COLOR="#ff00ff"]us[/COLOR]' keyboard (Dell standard).:confused:

Took a few tries to get this, I'm a little slow.

Also someone mentioned the blue screen with[COLOR="DeepSkyBlue"] 'please wait'.[/COLOR] ctrl c doesn't work for this in either [COLOR="#ff00ff"]uk[/COLOR] or [COLOR="#ff00ff"]us[/COLOR] setup.

I type [COLOR="Red"]exit[/COLOR] which throws me back to the main selection screen, then I have to power off to restart the system.

Anyway, now I know how to use it (thanks guys! incl Aysiu whose site put me onto this originally) I can clean up my main partition and do a real backup[/FONT]:guitar:

[FONT="Comic Sans MS"][COLOR="Purple"]Thanks Wieman.[/COLOR][/FONT]

---

### Post by carloslosgrande on 2007-10-24
[FONT="Comic Sans MS"]Big problem. I've just got back online after having major problems with my discs. After successfully (I thought) creating an image I restarted and found that Feisty was having trouble accessing my ext hdd's. This problem got progressively worse to include my system discs/partitions.
fsck found errors, hal wouldn't start, gnome had a fit, etc,etc. Ditto for Gutsy.
Decided to restore from the image and lost it all!!! No OS!
systemrescuecd screwed it, supergrubdisk and reinstall of gutsy has got me to here.
I thought I had lost everything.
.[/FONT]

---

### Post by wieman01 on 2007-10-24
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Big problem. I've just got back online after having major problems with my discs. After successfully (I thought) creating an image I restarted and found that Feisty was having trouble accessing my ext hdd's. This problem got progressively worse to include my system discs/partitions.
fsck found errors, hal wouldn't start, gnome had a fit, etc,etc. Ditto for Gutsy.
Decided to restore from the image and lost it all!!! No OS!
systemrescuecd screwed it, supergrubdisk and reinstall of gutsy has got me to here.
I thought I had lost everything.
.[/FONT]
D@#! it. Do you know what went wrong? Could you restore your data eventually?

Let me know if I can be of any help. I can imagine how frustrating this must be.

---

### Post by carloslosgrande on 2007-10-24
[FONT="Comic Sans MS"]Hi. I don't really know what went wrong. I actually got the image files made so I guess that part went ok??maybe?
But it was from then that I progressively lost access. Maybe something to do with mount command??
The restore process really killed it though. The error messages seemed to be saying (all in all) that the drives were unreadable so I'm guessing the mount command changed the address??

Anyway It looks like I've now got all my access back to my files.:guitar:
The Feisty partition is still cactus. I'll reabsorb it into the Gutsy partition later on.

Its a worry when the backup process is the problem.:(

The only final sticker is nautilus can't open a folder in the drive that I restored the image from, ie sdb1. Yet VLC can no trouble.
This may or may not be connected. It may fix itself next restart, Gutsy seems to be able to do that.

Anyway, thanks for your help.[/FONT]

---

### Post by wieman01 on 2007-10-24
Carlos, 

First time I hear of such thing. I believe that this is due to a hardware / HD failure, could that be the problem? That backup solution is definitely fine, I and others have used it many times.

By they way... nice fonts you got there!

---

### Post by carloslosgrande on 2007-10-24
[FONT="Comic Sans MS"]Yeah, I thought my discs had bit the dust, with all my stuff, but its all working fine now.
I was really puzzled at the whole thing. I still think it was something to do with addressing and it got changed.
Whatever.[/FONT]:guitar:
[FONT="Comic Sans MS"]Thanks again.[/FONT]

---

### Post by seventhc on 2007-11-25
this is a good thread, very helpful. Thanks for posting it. I bookmarked it :)

---

### Post by wieman01 on 2007-11-26
> **seventhc said:**
> this is a good thread, very helpful. Thanks for posting it. I bookmarked it :)
You are welcome. Post here if you encounter problems. :-)

---

### Post by Clancy_s on 2007-11-28
I found the guide thorough and easy to follow.

I imaged the / partition last night then ran a simulated restore, everything seemed to be working properly.  I won't try an actual restore unless I need one... 

I had one problem only making the image: I couldn't work out how to increase the specifiec size of the image file: I could get to that part of the screen using the tab or up and down arrow keys, but I couldn't work out how to increase the default number (2073 Mb IIRC).  I tried the + and - keys, up and down and left to right arrows, numerical keys, the space bar and the enter key, with no effect.  The answer is probably simple but it eluded me.  In the end I used the "Automatically set the size of the image file" option and since I was imaging a 10Gb partition with 3Gb of data into a partition with 70Gb free it made one image file with no problem.

Thanks for your help. :)

---

### Post by wieman01 on 2007-11-29
> **Clancy_s said:**
> I had one problem only making the image: I couldn't work out how to increase the specifiec size of the image file: I could get to that part of the screen using the tab or up and down arrow keys, but I couldn't work out how to increase the default number (2073 Mb IIRC).
It's even easier... Just type in whatever size it ought to have. Simple numerical values. :-) E.g. 10000. That's all.

---

### Post by Clancy_s on 2007-11-29
> **wieman01 said:**
> It's even easier... Just type in whatever size it ought to have. Simple numerical values. :-) E.g. 10000. That's all.

I did actually try the numerical keys, when the cursor was in that box (I think).  I must have been doing something wrong, I'll try it again next time I do it.

Thanks again. :)

---

### Post by wieman01 on 2007-11-30
> **Clancy_s said:**
> I did actually try the numerical keys, when the cursor was in that box (I think).  I must have been doing something wrong, I'll try it again next time I do it.

Thanks again. :)
Press Num-Lock next time you try. :-) It should work.

---

### Post by boob11 on 2007-11-30
Thanx man

---

### Post by Aracheon on 2007-11-30
I'm starting to think perhaps I'm the only person who's having this problem...


A little background first - here's what I'm working with:

- IBM ThinkPad T30, 512MB RAM, 40GB hard drive
- I'm backing up to an external USB hard drive
- I only have two partitions on the hard drive, /dev/sda1 and the swap partition

The backup of the /dev/sda1 partition to the external drive seems to work just fine, as I get no errors. To minimize the possibility of corruption, I opted for No Compression on the backup.

The problem, however, seems to stem from when I want to run a restore on another machine with identical hardware. The entire restore process takes about an hour, and PartImage even tells me that it completed successfully. But, once the machine is rebooted, I get an error message stating that there is an error loading the operating system. This is clearly an MBR problem, but even restoring the MBR in a separate process doesn't seem to work.

Am I missing something?

---

### Post by wieman01 on 2007-12-01
> **Aracheon said:**
> I'm starting to think perhaps I'm the only person who's having this problem...


A little background first - here's what I'm working with:

- IBM ThinkPad T30, 512MB RAM, 40GB hard drive
- I'm backing up to an external USB hard drive
- I only have two partitions on the hard drive, /dev/sda1 and the swap partition

The backup of the /dev/sda1 partition to the external drive seems to work just fine, as I get no errors. To minimize the possibility of corruption, I opted for No Compression on the backup.

The problem, however, seems to stem from when I want to run a restore on another machine with identical hardware. The entire restore process takes about an hour, and PartImage even tells me that it completed successfully. But, once the machine is rebooted, I get an error message stating that there is an error loading the operating system. This is clearly an MBR problem, but even restoring the MBR in a separate process doesn't seem to work.

Am I missing something?
You probably need to set up GRUB on the new machine. Have you done so?

---

### Post by mcarni on 2008-01-26
I'm very new to Linux, sorry if my questions sound very very silly...

at the moment my hard disk is partitioned as follows:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2551        5978    27535410   83  Linux
/dev/sda2           11541       12161     4988182+   5  Extended
/dev/sda3   *        5979        9104    25109595   83  Linux
/dev/sda4               1        2550    20482843+  83  Linux
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris
/dev/sda6           11541       11784     1959867   82  Linux swap / Solaris

the ubuntu installation on /dev/sda3 is working fine, but I need to improve the screen resolution (ATI video card problem...)

the ubuntu installation on /dev/sad1 is some kind of leftover from my very first attempt to install ubuntu and has got some problem.

My idea was to use the installation on sda3 has a safe point, and I could use the installation on sda1 to run experiments with the drivers and settings.

I used the live cd of SysteRescueCD to create an image of the sda3 partition, and then I restored it on sda1, everything seemed good but then when rebooting if I select the sda1 installation nothing happens, it does as it used to do before restoring the partition.
If when booting I choose the installation on sda3 when I browse my computer I cannot see the sda1 partition,
If I use Gparted to analyse my partition I see the sda1 partition but it has a warning sign next to it and it say "Unable to find mountpoint. Unable to read the contents of this filesystem, beacuse of this some operations maybe unaivalable"

Please let me know where I went wrong.

thank you very much for your help

---

### Post by wieman01 on 2008-01-26
> **mcarni said:**
> I'm very new to Linux, sorry if my questions sound very very silly...

at the moment my hard disk is partitioned as follows:

the ubuntu installation on /dev/sda3 is working fine, but I need to improve the screen resolution (ATI video card problem...)

the ubuntu installation on /dev/sad1 is some kind of leftover from my very first attempt to install ubuntu and has got some problem.

My idea was to use the installation on sda3 has a safe point, and I could use the installation on sda1 to run experiments with the drivers and settings.

I used the live cd of SysteRescueCD to create an image of the sda3 partition, and then I restored it on sda1, everything seemed good but then when rebooting if I select the sda1 installation nothing happens, it does as it used to do before restoring the partition.
If when booting I choose the installation on sda3 when I browse my computer I cannot see the sda1 partition,
If I use Gparted to analyse my partition I see the sda1 partition but it has a warning sign next to it and it say "Unable to find mountpoint. Unable to read the contents of this filesystem, beacuse of this some operations maybe unaivalable"
This might be less of a Partimage problem, but anyway, let's see what can be done.

Does "sda3" boot as normal?

Please post the contents of:
> sudo gedit /boot/grub/menu.lst
Please pay attention to the fact that both partitions (i.e. 'sda1' and 'sda2') need to have the exact same size. Restoring an image to a partition that is smaller or bigger than the source partition will mess things up.

---

### Post by mcarni on 2008-01-26
Yes, sda3 boots fine,

Before restoring sda3 on sda1 I had to resize the sda3 partition, but I didn't know they had to have the same identical size so I just made the source partition slightly smaller than the destination partition.

Below you find the outcome of 
sudo gedit /boot/grub/menu.lst

Thank you very much for your help

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0f143362-d486-4965-8c70-19ed1e2b5b0e ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0f143362-d486-4965-8c70-19ed1e2b5b0e ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by wieman01 on 2008-01-27
> **mcarni said:**
> Yes, sda3 boots fine,

Before restoring sda3 on sda1 I had to resize the sda3 partition, but I didn't know they had to have the same identical size so I just made the source partition slightly smaller than the destination partition.
No problem. They don't have to be identical, it's just that you are wasting space if the target partition is much bigger, because the Partimage will mysteriously occupy the additional space and you won't be able to use anymore. It just 'disappears'.

This is a problem I have never seen before nor tackled it myself, so bear with me, we will have to do same testing. Don't worry, this should be safe. Please make a safety copy of that file first:
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
I am only making changes at the relevant section:
> ## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=**[COLOR="Red"]523ff495-34f8-4530-90d9-7c6eb8bf97f2[/COLOR]** ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=0f143362-d486-4965-8c70-19ed1e2b5b0e ro single
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 7.10, memtest86+ (on /dev/sda1)
root (hd0,0)
kernel /boot/memtest86+.bin
savedefault
boot
The only change that I have made is the section in red. This won't affect "/dev/sda3" at all. Please restart the PC and let me know if you can boot from "/dev/sda1". I try to explain later on what we have done.

---

### Post by mcarni on 2008-01-27
I modified the menu.lst file as you said and when I reboot I can actually boot from sda1.

Something is strange though, 
It looks like even if I select to boot from sda1 it actually boots from sda3. I tried to change the background appearance on the ubuntu on sda3 I thought this would have helped me to understand on what partition I am...and then when I rebooted from sda1 I had the new background.

If I go to gparted I can see all the partition, and next to sda1 there is the same warning symbol (no mounting point...) but when I browse to look for files on my computer I can't actually see the sda1 partition.

I'm tempted to format sda1 and try again to create an image of sda3 with partimage and restore it over sda1.
But not sure it's a good idea.... I'm afraid of screwing things even more...

thanks again for your help

---

### Post by wieman01 on 2008-01-27
> **mcarni said:**
> I modified the menu.lst file as you said and when I reboot I can actually boot from sda1.

Something is strange though, 
It looks like even if I select to boot from sda1 it actually boots from sda3. I tried to change the background appearance on the ubuntu on sda3 I thought this would have helped me to understand on what partition I am...and then when I rebooted from sda1 I had the new background.

If I go to gparted I can see all the partition, and next to sda1 there is the same warning symbol (no mounting point...) but when I browse to look for files on my computer I can't actually see the sda1 partition.

I'm tempted to format sda1 and try again to create an image of sda3 with partimage and restore it over sda1.
But not sure it's a good idea.... I'm afraid of screwing things even more...

thanks again for your help
Do both partitions share the same home partition by chance? That might explain it.

Another thing though... Please post the contents of "fstab" on both partitions:
> sudo cat /etc/fstab

---

### Post by mcarni on 2008-01-27
I don't think the two partitions share the same home directory, I haven't messed around with the home directory (yet...) when I restored the image of sda3 over sda1 I thought the two partitions where going to be independent, so that I could use one to do some experiments without damaging the other...


this what I got from fstab

hope this helps

Thanks

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d3006903-a4d8-447e-8d26-33262c989f07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
susini@alyosha:~$

---

### Post by wieman01 on 2008-01-27
Alright, that's sda3. Please post the same for 'sda1'. You can retrieve that information by mounting 'sda1':
> sudo mount /dev/sda1 /mnt
> sudo cat /mnt/etc/fstab
Please post the contents. I know what we need to do.

---

### Post by mcarni on 2008-01-27
here you go:

susini@alyosha:~$ sudo mount /dev/sda1 /mnt
[sudo] password for susini:
susini@alyosha:~$ sudo cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d3006903-a4d8-447e-8d26-33262c989f07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by wieman01 on 2008-01-27
> **mcarni said:**
> here you go:

susini@alyosha:~$ sudo mount /dev/sda1 /mnt
[sudo] password for susini:
susini@alyosha:~$ sudo cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d3006903-a4d8-447e-8d26-33262c989f07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
That's the issue... you see it? Although this is 'fstab' for 'sda1' it mounts 'sda3'. We need to change that. Now open the file:
> sudo gedit /mnt/etc/fstab
And make it read:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
**[COLOR="Red"]/dev/sda1[/COLOR]** /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
**[COLOR="Red"]/dev/sda6[/COLOR]** none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
Now save the file.

Please also undo the changes to '/boot/grub/menu.lst' we made earlier as I was wrong:
> ## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=**[COLOR="Red"]0f143362-d486-4965-8c70-19ed1e2b5b0e[/COLOR]** ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=0f143362-d486-4965-8c70-19ed1e2b5b0e ro single
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 7.10, memtest86+ (on /dev/sda1)
root (hd0,0)
kernel /boot/memtest86+.bin
savedefault
boot
Now restart the PC and see if you can boot from 'sda1'.

---

### Post by mcarni on 2008-01-27
Sorry, seems it doesn't work.

Now when I try to boot from sda1 I get a black screen, I don't know if it is actually prompting me for my username and password.
This is what it used to do before I restored the sda3 image over sda1.

booting from sda3 works fine, and everything seems to be working.

---

### Post by wieman01 on 2008-01-27
> **mcarni said:**
> Sorry, seems it doesn't work.

Now when I try to boot from sda1 I get a black screen, I don't know if it is actually prompting me for my username and password.
This is what it used to do before I restored the sda3 image over sda1.

booting from sda3 works fine, and everything seems to be working.
OK, I'll have to think about it and post back tomorrow. Late here, so let's call it a day. :-)

---

### Post by mcarni on 2008-01-27
thanks anyway,

I really appreciate your help.

If it gets too complicated don't worry, i can always format the sda1 and create a new image of sda3 and restore it....

thank you very much

---

### Post by wieman01 on 2008-01-28
> **mcarni said:**
> I modified the menu.lst file as you said and when I reboot I can actually boot from sda1.

Something is strange though, 
It looks like even if I select to boot from sda1 it actually boots from sda3. I tried to change the background appearance on the ubuntu on sda3 I thought this would have helped me to understand on what partition I am...and then when I rebooted from sda1 I had the new background.

If I go to gparted I can see all the partition, and next to sda1 there is the same warning symbol (no mounting point...) but when I browse to look for files on my computer I can't actually see the sda1 partition.

I'm tempted to format sda1 and try again to create an image of sda3 with partimage and restore it over sda1.
But not sure it's a good idea.... I'm afraid of screwing things even more...

thanks again for your help
No problem.

I think there is an issue with UUIDs. Let's do the following then. Please boot from 'sda3'.
> sudo mount /dev/sda1 /mnt
> ls -lh /dev/disk/by-uuid/
I think the UUID entry in "/boot/grub/menu.lst" is incorrect. The last command should shed some light on it.

---

### Post by UnCola on 2008-01-28
> Mount backup partition; xxxx stands for your partition that serves as a backup device (e.g. hda1, sda1):
Quote:
mount /dev/xxxx /backup

this invariably gives me the message 

"Can't find /dev/xxxx/backup in /etc/fstab or /etc/mtab"

the instructions (see below) were to create a  backup directory, but not clear where, and no matter which drive I try the above with I get that same message.

> 1. Boot from RESCUE CD & type:

    * Create mount-point:
      Quote:
      mkdir /backup
    * Checking partition tables:
      Quote:
      fdisk -l
    * Mount backup partition; xxxx stands for your partition that serves as a backup device (e.g. hda1, sda1):
      Quote:
      mount /dev/xxxx /backup
    * Start Partimage:
      Quote:
      partimage 

---

### Post by wieman01 on 2008-01-28
> **UnCola said:**
> this invariably gives me the message 

"Can't find /dev/xxxx/backup in /etc/fstab or /etc/mtab"

the instructions (see below) were to create a  backup directory, but not clear where, and no matter which drive I try the above with I get that same message.
Please post the following:
> fdisk -l
We'll figure it out.

---

### Post by mcarni on 2008-01-28
This is what I get





susini@alyosha:~$ sudo mount /dev/sda1 /mnt
[sudo] password for susini:
susini@alyosha:~$ ls -lh /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-01-28 12:04 30457144-349c-4e7e-8b6e-2d879997a989 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-01-28 12:04 523ff495-34f8-4530-90d9-7c6eb8bf97f2 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-01-28 12:04 b8e1ea2a-5aa3-4ded-b1fe-bdfb0ce2a5f5 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-01-28 12:04 d3006903-a4d8-447e-8d26-33262c989f07 -> ../../sda6
susini@alyosha:~$ 

Thanks

---

### Post by wieman01 on 2008-01-28
> **mcarni said:**
> This is what I get

susini@alyosha:~$ sudo mount /dev/sda1 /mnt
[sudo] password for susini:
susini@alyosha:~$ ls -lh /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-01-28 12:04 30457144-349c-4e7e-8b6e-2d879997a989 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-01-28 12:04 523ff495-34f8-4530-90d9-7c6eb8bf97f2 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-01-28 12:04 b8e1ea2a-5aa3-4ded-b1fe-bdfb0ce2a5f5 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-01-28 12:04 d3006903-a4d8-447e-8d26-33262c989f07 -> ../../sda6
susini@alyosha:~$ 

Thanks
I don't get it. Where is 'sda1'?

Could you do the same please after booting from the Live CD? Something is very strange here, I just cannot put my finger on it. The Live CD might throw light on it.

---

### Post by mcarni on 2008-01-28
Sorry Wieman, this will sound incredibly dumb.
I typed ls -lh /dev/disk/by-uuid/ with the systermrescuecd in, and it says command not found: ls. 

I feel sorry you are spending all this time to help me and I can't even do this....
I would feel even worse if the problem with sda1 is something I have done without realising it...

---

### Post by wieman01 on 2008-01-28
> **mcarni said:**
> Sorry Wieman, this will sound incredibly dumb.
I typed ls -lh /dev/disk/by-uuid/ with the systermrescuecd in, and it says command not found: ls. 

I feel sorry you are spending all this time to help me and I can't even do this....
I would feel even worse if the problem with sda1 is something I have done without realising it...
Hey, don't worry. Just don't give up yet. Learning how to use Linux is perfectly fine, so bear with me.

You sure have got the Ubuntu Live CD, right? The one that you have installed your system with. Boot using that very CD, not the RescueCD. It will recognize the command.

---

### Post by mcarni on 2008-01-28
Giving up is not an option.
UBUNTU is supercool, I really like it,

Below you find the result from the ls command:

lrwxrwxrwx 1 root root 10 2008-01-28 20:00 30457144-349c-4e7e-8b6e-2d879997a989 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-01-28 20:01 523ff495-34f8-4530-90d9-7c6eb8bf97f2 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-28 20:00 b8e1ea2a-5aa3-4ded-b1fe-bdfb0ce2a5f5 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-01-28 20:00 d3006903-a4d8-447e-8d26-33262c989f07 -> ../../sda6

Thanks

---

### Post by mcarni on 2008-01-28
I don't know if this can help to understand the problem, but maybe...
If I go to gparted to analyse my current partitions, sda1 appears to be mounted even if I booted from sda3.

Hope this means something to you...

---

### Post by wieman01 on 2008-01-29
> **mcarni said:**
> Giving up is not an option.
UBUNTU is supercool, I really like it,

Below you find the result from the ls command:

lrwxrwxrwx 1 root root 10 2008-01-28 20:00 30457144-349c-4e7e-8b6e-2d879997a989 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-01-28 20:01 523ff495-34f8-4530-90d9-7c6eb8bf97f2 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-28 20:00 b8e1ea2a-5aa3-4ded-b1fe-bdfb0ce2a5f5 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-01-28 20:00 d3006903-a4d8-447e-8d26-33262c989f07 -> ../../sda6

Thanks
You know... What really beats me is the fact that I cannot recognize the backup partition (i.e. sda1) that we are talking about. Don't get hung up on the partition numbers, just tell me which one of them is "sda1" when you boot from "sda3".

Is it 'sda5' or 'sda1' or 'sda4' or 'sda6'? You could find out by opening GParted (from the Live CD).

The thing is this: Your '/boot/grub/menu.lst' states that 'sda1' has a UUID which is '0f143362-d486-4965-8c70-19ed1e2b5b0e'. I think that is wrong because you have made changes to that partition (e.g. size) and as a consequence the number has changed. So when you try to boot from it now, it fails.

So I am trying to find out what the new UUID is. Do you understand what I am trying to get at?

_**EDIT:**_
Please don't give up yet. We are close.

---

### Post by mcarni on 2008-01-29
I don't have a complete understanding of where the problem could be but I guess I'm starting to get a hint.
Don't worry, I won't give up...

I took a quick look at the partitions with gparted, hope this tells you something more:

sda3 is the partition which I backed up with partimage.
It boots fine, and I have all the applications and data I need on it.

sda6 is the swap partition for sda3 (1.87GB)

sda1 is the partition I tried to overwrite by restoring the image of sda3 over it. It was already not booting correctly before I restored sda3 over it. I was planning to use this partition as a clone of sda3 partition, so that I could run my tweaking and experiments on this keeping the sda3 partition as it is.

I don't think I resized sda1, but I believed I resized sda3, to make it smaller than sda1 so that partimage could restore the image.

sda5 is the swap partition for sda1

both sda5 and sda6 are grouped together (?) under sda2

sda4 is an extra partition (ext2 if I understand correctly) which I used to store the image of sda3. I know this was not necessary but when I did it I didn't know... :) 
 
I know it is  a bit messy...

I will do some cleaning up...just need a bit of practice.

---

### Post by wieman01 on 2008-01-30
> **mcarni said:**
> I don't have a complete understanding of where the problem could be but I guess I'm starting to get a hint.
Don't worry, I won't give up...

I took a quick look at the partitions with gparted, hope this tells you something more:

sda3 is the partition which I backed up with partimage.
It boots fine, and I have all the applications and data I need on it.

sda6 is the swap partition for sda3 (1.87GB)

sda1 is the partition I tried to overwrite by restoring the image of sda3 over it. It was already not booting correctly before I restored sda3 over it. I was planning to use this partition as a clone of sda3 partition, so that I could run my tweaking and experiments on this keeping the sda3 partition as it is.

I don't think I resized sda1, but I believed I resized sda3, to make it smaller than sda1 so that partimage could restore the image.

sda5 is the swap partition for sda1

both sda5 and sda6 are grouped together (?) under sda2

sda4 is an extra partition (ext2 if I understand correctly) which I used to store the image of sda3. I know this was not necessary but when I did it I didn't know... :) 
 
I know it is  a bit messy...

I will do some cleaning up...just need a bit of practice.
Understood.

Ok, I will need you to do me some more favor before we start putting the piece together. Please boot from Live CD first and run:
> blkid
Then boot from 'sda3' and do the same:
> blkid
Please post the results. If you have the time, please also attach a screenshot of GParted (Live CD).

---

### Post by mcarni on 2008-01-30
Here you go:

blkid from the CD

ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="523ff495-34f8-4530-90d9-7c6eb8bf97f2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="523ff495-34f8-4530-90d9-7c6eb8bf97f2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="b8e1ea2a-5aa3-4ded-b1fe-bdfb0ce2a5f5" TYPE="ext2" 
/dev/sda5: UUID="30457144-349c-4e7e-8b6e-2d879997a989" TYPE="swap" 
/dev/sda6: UUID="d3006903-a4d8-447e-8d26-33262c989f07" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" UUID="7446-8DFA" TYPE="vfat" 
ubuntu@ubuntu:~$ 

blkid from sda3

susini@alyosha:~$ blkid
/dev/sda1: UUID="0f143362-d486-4965-8c70-19ed1e2b5b0e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="523ff495-34f8-4530-90d9-7c6eb8bf97f2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="30457144-349c-4e7e-8b6e-2d879997a989" TYPE="swap" 
/dev/sda6: UUID="d3006903-a4d8-447e-8d26-33262c989f07" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" UUID="7446-8DFA" TYPE="vfat" 
susini@alyosha:~$ 


and the screenshot of Gparted should be attached.

thanks

M

---

### Post by wieman01 on 2008-01-30
You know, I think the problem is caused by the fact that 'sda1' and 'sda3' don't have the same size. The Live CD assign the exact same UUID to both partitions, 'sda3' different UUIDs. This does not really make sense. I don't want to throw in the towel, but I am at my wit's end.

If GRUB ("/boot/grub/menu.lst") on **'sda3'** contains a reference to "523ff495-34f8-4530-90d9-7c6eb8bf97f2" and 'fstab' on **'sda1'** says:
> /dev/sda1 / ext3 defaults,errors=remount-ro 0 1
...then it should work. If that fails, then this is a dead end.

Have we tried this combination yet?

---

### Post by mcarni on 2008-01-30
Unfortunately, I think we have already tried it....
But don't worry, I will take it as a sign from my computer to tell me to clean up the mess I made with my hard disk.
I will make sure that the size of the destination partition is identical to the size of the source partition.
Before getting started I have a couple of questions I really hope you can help me with...
Do you think formatting the destination partition before restoring is a good idea?
If so, is ext3 a good filesystem?
I read something about partition table and MBR, honestly I believe they are a bit too advanced for my level....at least at the moment....
Is backing up and restoring the partition table and MBR necessary?
My last question is about the swap partition that was supposed to be used by sda1, 
What should I do with it?

Wieman, I really appreciate your advice, you have been of great help in these days.

I'll keep you updated on how the backup goes...

THANK SO MUCH
M

---

### Post by wieman01 on 2008-01-31
> **mcarni said:**
> Do you think formatting the destination partition before restoring is a good idea?
Yes, you would have to do it the first time you create the partition. But that's about it. There is no need to format it at a later stage, since Partimage will overwrite with the source image anyway. Just ensure that both source and target partition have the same type of file system (e.g. ext3).
> **mcarni said:**
> If so, is ext3 a good filesystem?
Yes, it definitely is. I have been using it and never had a problem with it.
> **mcarni said:**
> Is backing up and restoring the partition table and MBR necessary?
No, it's not. The MBR resides on a separate location on the hard-disk. I know too little about it to give you 100% correct information, so I recommend that you read this (great source from user Herman):

[http://users.bigpond.net.au/hermanzone/p6.htm]("http://users.bigpond.net.au/hermanzone/p6.htm")

Herman is a very knowledgeable guy and is able to explain it to you in great depth.
> **mcarni said:**
> My last question is about the swap partition that was supposed to be used by sda1, 
What should I do with it?
Nothing in fact. You don't have to back it up if that's what you are referring to. 'fstab' (on each partition e.g. sda1, sda3) holds a reference to your SWAP partition. So even if you change the partition number you can aways edit 'fstab' using the Live CD to tell your system where it is. 
> **mcarni said:**
> Wieman, I really appreciate your advice, you have been of great help in these days.
Hey, my pleasure. It's a learning process for me as well and I am always eager to learn more. :-)

See you then!

---

### Post by mcarni on 2008-02-01
Hi Wieman,

I'going away for few days, so yesterday night I tried to do some clean up of my partitions. 

I resized sda1 so that sda3 (source partition) and sda1 (destination partition) had exactly the same size.

I formatted to ext3 sda1, and sda4(which I used as a repository for the image of sda3.

I follow the instructions and I think I managed to get an image of sda3, saved it onto sda4 and then restore it in sda1.

I I boot from sda3 everything looks good, I don't have the warning sign, close to the sda1 partition anymore. And the size and the used space on both sda1 and sda3 are identical.

To me it looks like sda1 and sda3 are identical copies, but unfortunatelt I still can't boot from sda1.

I think this time we are really really close to the "happy end" of this adventure.

Maybe it is something I have changed in these days on menu.lst or fstab that confuses my computer.

Do you have any suggestion



Thank you so much

cheers
M

---

### Post by wieman01 on 2008-02-01
> **mcarni said:**
> Hi Wieman,

I'going away for few days, so yesterday night I tried to do some clean up of my partitions. 

I resized sda1 so that sda3 (source partition) and sda1 (destination partition) had exactly the same size.

I formatted to ext3 sda1, and sda4(which I used as a repository for the image of sda3.

I follow the instructions and I think I managed to get an image of sda3, saved it onto sda4 and then restore it in sda1.

I I boot from sda3 everything looks good, I don't have the warning sign, close to the sda1 partition anymore. And the size and the used space on both sda1 and sda3 are identical.

To me it looks like sda1 and sda3 are identical copies, but unfortunatelt I still can't boot from sda1.

I think this time we are really really close to the "happy end" of this adventure.

Maybe it is something I have changed in these days on menu.lst or fstab that confuses my computer.
Hello, 

Sounds much better now. 

In order to go ahead, I need the following information:

Boot from 'sda3' and post:
> sudo cat /boot/grub/menu.lst
> sudo mount /dev/sda1 /mnt
> sudo cat /mnt/etc/fstab
> blkid
> sudo fdisk -l
That should do. We will put the pieces together after you have posted that stuff. :-)

---

### Post by wieman01 on 2008-02-01
> **1000lks said:**
> tell me why,   and  how to do?
Tell you what exaclty?

---

### Post by mcarni on 2008-02-01
Wieman,

here you go:

susini@alyosha:~$ sudo cat /boot/grub/menu.lst
[sudo] password for susini:
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0f143362-d486-4965-8c70-19ed1e2b5b0e ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0f143362-d486-4965-8c70-19ed1e2b5b0e ro single 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, memtest86+ (on /dev/sda1)
root            (hd0,0)
kernel          /boot/memtest86+.bin  
savedefault
boot



susini@alyosha:~$ sudo mount /dev/sda1 /mnt
susini@alyosha:~$ sudo cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d3006903-a4d8-447e-8d26-33262c989f07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
susini@alyosha:~$ 


susini@alyosha:~$ blkid
/dev/sda1: UUID="0f143362-d486-4965-8c70-19ed1e2b5b0e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="523ff495-34f8-4530-90d9-7c6eb8bf97f2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="30457144-349c-4e7e-8b6e-2d879997a989" TYPE="swap" 
/dev/sda6: UUID="d3006903-a4d8-447e-8d26-33262c989f07" TYPE="swap" 
susini@alyosha:~$


susini@alyosha:~$ sudo fdisk -l
[sudo] password for susini:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39663966

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2853        5978    25109595   83  Linux
/dev/sda2           11541       12161     4988182+   5  Extended
/dev/sda3   *        5979        9104    25109595   83  Linux
/dev/sda4               1        2852    22908658+  83  Linux
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris
/dev/sda6           11541       11784     1959867   82  Linux swap / Solaris

Partition table entries are not in disk order
susini@alyosha:~$ 

I really appreciate your help mate

take care
M

---

### Post by wieman01 on 2008-02-01
**@mcarni:**

This looks much better now in fact. It all makes sense now.

We want to make 'sda' bootable. Therefore we have to make 2 minor changes on 'sda1' and 'sda3':

1. Change 'fstab' on 'sda1':
> sudo mount /dev/sda1 /mnt
> sudo gedit /mnt/etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
[COLOR="Red"]/dev/sda1 / ext3 defaults,errors=remount-ro 0 1[/COLOR]
# /dev/sda6
UUID=d3006903-a4d8-447e-8d26-33262c989f07 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
I have replace the UUID of 'sda1' with the device number. That's perfectly safe.

2. Now we have to update GRUB which resides on 'sda3' (only the relevant section):
> sudo gedit /boot/grub/menu.lst
> # This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
**root (hd0,0)**
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=[COLOR="Red"]0f143362-d486-4965-8c70-19ed1e2b5b0e[/COLOR] ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
**root (hd0,0)**
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=[COLOR="Red"]0f143362-d486-4965-8c70-19ed1e2b5b0e[/COLOR] ro single
initrd /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 7.10, memtest86+ (on /dev/sda1)
root (hd0,0)
kernel /boot/memtest86+.bin
savedefault
boot
Since "0f143362-d486-4965-8c70-19ed1e2b5b0e" is already there, I have not changed anything at all in fact. Looks good now.

Please restart the PC and see if you can boot. All we had to change in your case was 'fstab' on 'sda1'. That's what you'd have to do in future as well once you have pulled a backup and installed it on 'sda1'.

Let's keep our fingers crossed. It should work now.

---

### Post by mcarni on 2008-02-01
I'm so disappointed, right when I thought I actually understood what was going on....

I still can't boot from sda1, just a black screen.:confused:

I left grub on sda3 as it was and modified the fstab on sda1 as follows:

susini@alyosha:~$ sudo mount /dev/sda1 /mnt
[sudo] password for susini:
susini@alyosha:~$ sudo cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
/dev/sda1 / ext3 defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d3006903-a4d8-447e-8d26-33262c989f07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
susini@alyosha:~$ 



I thought we were there....but I guess it will be for when I come back.


cheers
M

---

### Post by wieman01 on 2008-02-02
> **mcarni said:**
> I'm so disappointed, right when I thought I actually understood what was going on....

I still can't boot from sda1, just a black screen.:confused:

I left grub on sda3 as it was and modified the fstab on sda1 as follows:

susini@alyosha:~$ sudo mount /dev/sda1 /mnt
[sudo] password for susini:
susini@alyosha:~$ sudo cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
/dev/sda1 / ext3 defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d3006903-a4d8-447e-8d26-33262c989f07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
susini@alyosha:~$ 

I thought we were there....but I guess it will be for when I come back.

cheers
M
My my... I don't get it either. I have done similar things before, just don't understand why it would not work this time.

One last thing for today... Update "fstab" on "sda1":
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
/dev/sda1 / ext3 defaults,errors=remount-ro 0       1
# /dev/sda6
[COLOR="Red"]/dev/sda6 none            swap    sw              0       0
[/COLOR]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
Then restart the PC and try.

Just another question: Why do you have 2 SWAP partitions (sda5, sda6)?

---

### Post by UnCola on 2008-02-02
> **wieman01 said:**
> Please post the following:

We'll figure it out.

Hi thanks that gives this result:

> Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: xxxxxxxxxx

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         637     5116671    7  HPFS/NTFS
/dev/hda2             638        9624    72188077+   f  W95 Ext'd (LBA)
/dev/hda5             638        7011    51199123+   7  HPFS/NTFS
/dev/hda6            9503        9624      979933+  82  Linux swap / Solaris
/dev/hda7            7012        9502    20008926   83  Linux

Partition table entries are not in disk orde

---

### Post by mcarni on 2008-02-02
Wieman,
Sorry, I'm not on my computer, I will be back in the middle of next week and I will try to update fstab as you suggest.

You know, I'm no expert, but it was all starting to make sense, I really didn't expect it not to work.
I thought that maybe it is something I have done previously, before I started getting familiar with partimage.

The first time I installed ubuntu, it went on sda1 and then I played with the video card until when I just got a black screen when I tried to reboot. Is it possible that now  it actually boots from sda1 but somehow it still has the same video card problem I had previosuly?
I know I didn't explain very well, I was just wondering that maybe somehow underneath the black screen there is a prompt for my username and password....

 
Then I re-installed ubuntu (this went on sda3), I really didn't do anything with the swap partitions, for my level of knowledge they self generated...:)


Sorry again for the mess...
and thank you so much for your help
M

---

### Post by wieman01 on 2008-02-03
> **mcarni said:**
> The first time I installed ubuntu, it went on sda1 and then I played with the video card until when I just got a black screen when I tried to reboot. Is it possible that now  it actually boots from sda1 but somehow it still has the same video card problem I had previosuly?
**@mcarni:**

In fact that's a possiblity. Is the HD active after you have chosen 'sda1'? You can find out if the system has booted by pressing:
> ctrl + alt + F2
You'll switch to command line by pressing it. If you see a log-on screen in black & white, you are there.

Anyway, it was (is) a pleasure working with you, so don't worry if you have to give it this time. It'll work one day, I am sure. And we have both learned a lot in the last couple of days, so we have not actually wasted time or anything like that. :-) Quite the contrary.

---

### Post by mcarni on 2008-02-09
Hi Wieman,

as they say in the movies...I'm back.... :)


I installed some more applications on my ubuntu (I also managed to get the proper screen resolution...) so I thought it was time to give another try to backing up one partition and restoring it in a second empty partition so to have two identical ubuntu installations.But I still can't get the second partition to boot.

below you find some update on my partitions, I will spend some more time trying to understand what I'm missing, Mainly because I'm very stubborn and I think we got very close to the solution...
Anyway since sda3 is working great and I don't think I will need to play with the installation a second identical partition is not a need any more.

sda3 is the source partition, boots perfectly, everything works.

sda1 is the repository partition where I saved the image of the sda3 partition.

sda4 is the partition where I restored the image of sda3.

sda5 is some leftover partition which used to be the swap partition for sda1 when ubuntu was installed there (tried to format it or delete but couldn't do it...)

sda6 is the swap partition for sda3

sda5 and sda6 are grouped under sda2 (don't ask me how I managed that....)

here you find my fdisk:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39663966

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2852    22908658+  83  Linux
/dev/sda2           11541       12161     4988182+   5  Extended
/dev/sda3            5979        9104    25109595   83  Linux
/dev/sda4            2853        5978    25109595   83  Linux
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris
/dev/sda6           11541       11784     1959867   82  Linux swap / Solaris


if I do blkid from sda3 I get:

susini@alyosha:~$ blkid
/dev/sda1: UUID="0f143362-d486-4965-8c70-19ed1e2b5b0e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="523ff495-34f8-4530-90d9-7c6eb8bf97f2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="30457144-349c-4e7e-8b6e-2d879997a989" TYPE="swap" 
/dev/sda6: UUID="d3006903-a4d8-447e-8d26-33262c989f07" TYPE="swap" 
susini@alyosha:~$ 

sda4 is missing....:confused:

I did blkid from the live cd and I get the line for sda4 identical to the line for sda3, same UUID and all the rest.

fstab on sda3:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d3006903-a4d8-447e-8d26-33262c989f07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

if I mount sda4 I get the following for the fstab:

susini@alyosha:~$ sudo mount /dev/sda4 /mnt
[sudo] password for susini:
susini@alyosha:~$ sudo cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=d3006903-a4d8-447e-8d26-33262c989f07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
susini@alyosha:~$ 

and this is the grub:

susini@alyosha:~$ sudo cat /boot/grub/menu.lst
[sudo] password for susini:
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=523ff495-34f8-4530-90d9-7c6eb8bf97f2 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0f143362-d486-4965-8c70-19ed1e2b5b0e ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0f143362-d486-4965-8c70-19ed1e2b5b0e ro single 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 7.10, memtest86+ (on /dev/sda1)
root            (hd0,0)
kernel          /boot/memtest86+.bin  
savedefault
boot

It still has references to sda1 which doesn't contain any ubuntu installation any more...I'm very tempted to edit the second part with something like the following:

# linux installation on /dev/[COLOR="Lime"]sda4.[/COLOR]
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=[COLOR="Lime"]523ff495-34f8-4530-90d9-7c6eb8bf97f2[/COLOR] ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot

basically replacing the UUID with the same of sda3, but I don't know if having references to two identical UUID's on grub for two different partition is ok....sounds very weird...
I suspect I must change also the bit with root (hd0,0), but I don't really know with what....

Hope my post is not too long or confusing...

thanks for your help

M

---

### Post by wieman01 on 2008-02-11
**@mcarni:**

Nice to have you back. :-)

I am a bit confused here... Just to clarify, you want to ignore 'sda1' for the time being and have your normal partition on 'sda3', the spare one (backup, etc.) on 'sda4', is that correct? Please confirm that before we proceed.

So basically we have to perform 2 steps:

1. Edit 'fstab' on 'sda4'.
2. Edit 'grub' on 'sda3'.

Please let me know soon and we'll continue from here. Don't change anything in the meantime...

---

### Post by mcarni on 2008-02-11
Hi Wieman,

Yes you are right:
sda3 current ubuntu installation, everything works fine (or kind of...see below)
sda4 partition wher I want to backup sda3
sda1 partition that works as a repository

I'm actually thinking of dropping the whole thing.
Today I noticed, but I suspect it happened already some days ago. that some files I modified yesterday where for ubuntu "last saved on 26th january". And now checking it better, I would say that everything is old, I would say like if it was a restore from an old backup.
I'm afraid that having sad3 and sda4 which is an image of sda3 on the same hard disk created some problem.
Maybe my files (and my wife's.... 	](*,)) have been saved on sda4....

I'm started to feel very very confused.

Probably the best is just to give up, delete all the unnecessary partition and hope that my files get saved...

confused

M

---

### Post by mcarni on 2008-02-11
Sorry to bother you again Wieman, I rebooted and I had another check on Gparted. 
5 minutes ago sda4 had a warning sign, saying something about not being able to find the mount point.
Now there is no warning sign, and it says that used space is 7.47 GB while sda3 is less than 5.
Since sda4 is supposed to be a copy of sda3, and after I made that copy I imported some music and changed some files, sda3 should be bigger than sda4.
I would say that someone my files are there in sda4....

strange....

M

---

### Post by wieman01 on 2008-02-12
Weird... are 'sda3' and 'sda4' not the same size?

What strikes me is the fact that 'sda4' seems to have disappeared this time. No output from 'blkid'. Could it be that the image you have pulled has been corrupted? How old is the image?

Tell you what... let's try something else. There is another backup tutorial which might do a better job:

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

It's admittedly fairly old, however, still relevant. I think it is an easier solution in your case, would you want to try? I can help you with it, as Partimage seems to fail on you.

_**EDIT:**_
But don't worry, if you still want to continue here, I'll support you. :-)

---

### Post by mcarni on 2008-02-12
Hi Wieman,

thanks for all your help, you have been incredibly helpful and nice.

I really learnt a lot, without you I would have been lost....

People like you make Ubuntu, and the Linux community a better place.

Summarizing my situation with partitions:
- I believe I have a good understanding of partimage, I will make an image of the current sda3 and I will store it on the extra partition (and on a dvd).
- having two identical partitions on the same pc (same UUID's) makes my computer some kind of "multiple personality" computer. I guess sometimes it actually boots from sda4 weven if it thinks it is sda3....:confused:
- I found the files I modified on Sunday on the sda4 (booting from the live CD) I managed to make a copy of the homw directory of sda4 on sd3 (used cp -r....impressed by myself...). Now Ijust need to change permission/ownership on this folder and restore the few files I modified on Sunday. (guess I will have to use something like chown....)

I really appreciate your help, and I will definitively read the thread, but I guess at the moment what I wanted is a bit too much for my knowledge.
I also promised to my wife I will not tweak around with the computer for the next month.
I don't want to say I give up, I would say that this is a temporarily on hold project.

 
I guess I will speak to you in a while

THANKS
M

---

### Post by wieman01 on 2008-02-12
> **mcarni said:**
> Hi Wieman,

thanks for all your help, you have been incredibly helpful and nice.

I really learnt a lot, without you I would have been lost....

People like you make Ubuntu, and the Linux community a better place.

Summarizing my situation with partitions:
- I believe I have a good understanding of partimage, I will make an image of the current sda3 and I will store it on the extra partition (and on a dvd).
- having two identical partitions on the same pc (same UUID's) makes my computer some kind of "multiple personality" computer. I guess sometimes it actually boots from sda4 weven if it thinks it is sda3....:confused:
- I found the files I modified on Sunday on the sda4 (booting from the live CD) I managed to make a copy of the homw directory of sda4 on sd3 (used cp -r....impressed by myself...). Now Ijust need to change permission/ownership on this folder and restore the few files I modified on Sunday. (guess I will have to use something like chown....)

I really appreciate your help, and I will definitively read the thread, but I guess at the moment what I wanted is a bit too much for my knowledge.
I also promised to my wife I will not tweak around with the computer for the next month.
I don't want to say I give up, I would say that this is a temporarily on hold project.
 
I guess I will speak to you in a while

THANKS
M
You are always welcome, it has been a pleasure to work with you. As I said before, I cannot quite explain what is happening, but I guess we have to benefited from our discussion, so we have not really wasted time. 

Just a last word: If you want to change permissions, you have to do the following:
> sudo chown -R susini:susini /home/susini
That's it. "-R" ensures that your user will also own all subfolders and their contents.

If you have time & questions, you know where you find me. Hope you enjoy your break!

---

### Post by DamonChyld on 2008-03-10
I am trying to backup to my NAS drive but keep getting a "error: connection refused" error after entering my password (2nd screen, after entering IP/Port information). I have opened a TCP/UDP through my router and am using the correct IP and have tried regular as well as admin login user/pass sets. 

Can someone point me in the right direction?

---

### Post by swoosh on 2008-04-25
Hi wieman01,

I have these partitions,

hda1 Linux (Boot)
hda2 Extended
hda5 Swap

I have successfully backed up and tested restoration of hda1 on external drive. partimage is giving me this error when I tried to backup Extended.

Error: The file system is unknown and is not supported. Can you explain what extended partition is for and does it have to be backed up? 

That aside, can these steps be used to restore the backup on another machine?

- Install a new system
- Boot from RESCUE CD and restore hda1 using partimage

Thanks

---

### Post by Ziggy72 on 2008-04-26
I haven't read through all of this post thoroughly and so maybe I've missed something. If so, I apologize. However, I do believe that your howto needs to be updated immediately - particularly for those of us who have systems which have both ext3 and ntfs partitions.

I have spent a few frustrating hours battling with this, and my problem all came down to your instruction 1.3:
> Mount backup partition: [COLOR="Sienna"]xxxx[/COLOR] stands for your partition that serves as a backup device (e.g. hda1, sda1):[quote]mount/dev/[COLOR="Sienna"]xxxx[/COLOR]/backup[/quote]

That instruction is fine if you are backing up to an ext3 partition, but it is not at all satisfactory if you are backing up to an ntfs partition. Actually it is very bad indeed because if you are backing up to an ntfs partition entering the code in your howto gives no error at all. The errors occur further down the line and lead to intense frustration - messages like 'not enough space', etc.

Please insert an amendment to your howto to read something like this:> If you are backing up to an ntfs partition, mount your backup partition as[quote]mount -t ntfs-3g /dev/[COLOR="Sienna"]xxxx[/COLOR] /backup[/quote]

Except for that one (but very, very important omission) it's a nice howto. Thanks

---

### Post by wieman01 on 2008-04-26
> **swoosh said:**
> Hi wieman01,

I have these partitions,

hda1 Linux (Boot)
hda2 Extended
hda5 Swap

I have successfully backed up and tested restoration of hda1 on external drive. partimage is giving me this error when I tried to backup Extended.

Error: The file system is unknown and is not supported. Can you explain what extended partition is for and does it have to be backed up? 

That aside, can these steps be used to restore the backup on another machine?

- Install a new system
- Boot from RESCUE CD and restore hda1 using partimage

Thanks
Hello, 

What format is the extended file system? NTFS?

Yes, you would proceed as you have described. Make sure all partitions have the same size as the original ones, or at least the formatted part should be the same. You can extend them later on.

---

### Post by wieman01 on 2008-04-26
> **Ziggy72 said:**
> I haven't read through all of this post thoroughly and so maybe I've missed something. If so, I apologize. However, I do believe that your howto needs to be updated immediately - particularly for those of us who have systems which have both ext3 and ntfs partitions.

I have spent a few frustrating hours battling with this, and my problem all came down to your instruction 1.3:


That instruction is fine if you are backing up to an ext3 partition, but it is not at all satisfactory if you are backing up to an ntfs partition. Actually it is very bad indeed because if you are backing up to an ntfs partition entering the code in your howto gives no error at all. The errors occur further down the line and lead to intense frustration - messages like 'not enough space', etc.

Please insert an amendment to your howto to read something like this:

Except for that one (but very, very important omission) it's a nice howto. Thanks
Hello, 

Backing up to NTFS partitions has not played a role so far, because write-support for NTFS file systems is in its infancy. 

But thanks for your note, I will update the tutorial soon and mention it, although I doubt it applies to a great number of people. It is known to most advanced (!) users how to mount NTFS volumes.

---

### Post by swoosh on 2008-04-26
> **wieman01 said:**
> Hello, 

What format is the extended file system? NTFS?

Yes, you would proceed as you have described. Make sure all partitions have the same size as the original ones, or at least the formatted part should be the same. You can extend them later on.

Hi,

Is there a way I can check the format?

I did not chose any format. The partitions I have mentioned are system partitions and were created when Ubuntu was first installed.

My backup goes into an external drive formatted using FAT32.

---

### Post by wieman01 on 2008-04-26
> **swoosh said:**
> Hi,

Is there a way I can check the format?

I did not chose any format. The partitions I have mentioned are system partitions and were created when Ubuntu was first installed.

My backup goes into an external drive formatted using FAT32.
Yes, you can check by opening GParted, the partition editor. It's installed by default.

Backing up to a FAT32 volume will be difficult, because FAT32 volumes have a max. file size restriction (4 GB if I remember correctly). If your installation is smaller than that, fine. Otherwise you have to use a 'ext3' or possibly a 'NTFS' volume.

---

### Post by swoosh on 2008-04-26
> **wieman01 said:**
> Yes, you can check by opening GParted, the partition editor. It's installed by default.

Backing up to a FAT32 volume will be difficult, because FAT32 volumes have a max. file size restriction (4 GB if I remember correctly). If your installation is smaller than that, fine. Otherwise you have to use a 'ext3' or possibly a 'NTFS' volume.

Yes, you are right about the file size restriction. I worked around it by breaking the backup into files smaller than 4GB.

I do not have a spare machine to test this. Have you ever have situation where simulation of the restore is successfully but the actual restore is otherwise?

---

### Post by wieman01 on 2008-04-26
> **swoosh said:**
> Yes, you are right about the file size restriction. I worked around it by breaking the backup into files smaller than 4GB.

I do not have a spare machine to test this. Have you ever have situation where simulation of the restore is successfully but the actual restore is otherwise?
Actually no, the simulation has never let me down. So if the test is successful, there is a pretty good chance you'll get it right when you restore your system.

As for the extended partition, what's on it?

---

### Post by swoosh on 2008-04-26
> **wieman01 said:**
> Actually no, the simulation has never let me down. So if the test is successful, there is a pretty good chance you'll get it right when you restore your system.

As for the extended partition, what's on it?

gparted give no information on the format of the partition and partimage doesn't allow me to back it up. 

The partition is as big as the swap partition. I suspect restoring the boot partition is sufficient. Doing the restoration on a spare machine is probably the better idea.

---

### Post by wieman01 on 2008-04-26
> **swoosh said:**
> gparted give no information on the format of the partition and partimage doesn't allow me to back it up. 

The partition is as big as the swap partition. I suspect restoring the boot partition is sufficient. Doing the restoration on a spare machine is probably the better idea.
Oh, I got it. Your swap resides on an extended partition, therefore you cannot back it up. Nothing unusual. Plus you would not want to back up your SWAP partition anyway, right? :-) So I reckon you could just go ahead.

---

### Post by swoosh on 2008-04-26
> **wieman01 said:**
> Oh, I got it. Your swap resides on an extended partition, therefore you cannot back it up. Nothing unusual. Plus you would not want to back up your SWAP partition anyway, right? :-) So I reckon you could just go ahead.

These are the partitions on my disk,

Boot partition
extended partition
swap partition

Yea, I'm not looking to backup the swap partition.

Thanks for the help.

---

### Post by rltw on 2008-04-26
Following the procedure in the OP, I tried to back up my Xubuntu 7.1 ext3 partition (2.7G, 2G used) to an empty 2.3G ext3 partition on an external USB drive as IMAGE.000. Partimage appeared to copy about 150mb before it said the disk was full. When I restarted Partimage and tried again, it asked if I wanted to overwrite the IMAGE.000 file. When I restarted the computer and again restarted Partimage, the file was evidently gone.

So what I'm wondering is whether the file was being written to RAM (384Mb) rather than the disk, even though Gparted showed the target partition as mounted.

As an aside, I found that with PartedMagic, I could C&P the source partition to an empty space, as long as that space is at least as big as the source partition. I would think reversing the process would be just as easy, but I have no reason to test that assumption as of now.

---

### Post by kle on 2008-05-26
Question 1: I too got the "please wait" - and underneath it was the root prompt. I pressed ctrl+c but nothing happened (except that I got a new prompt) So I shut down the computer. 

Question 2: Moreover, I have not been able to find out how to exit the systemrescue otherwise than by pressing the on/off button. 


Question 3: How come the image file created is 3.2 GB while the partition I am copying uses 4,6 (according to "properties" in my file manager)?


At any rate, if this really did clone my partition (and I am not going to try to find out until I have to - i.e. if I wreck my partition) I shall be eternally grateful to you!

---

### Post by swoosh on 2008-05-26
> Question 1: I too got the "please wait" - and underneath it was the root prompt. I pressed ctrl+c but nothing happened (except that I got a new prompt) So I shut down the computer. 

Is it possible that you make reference to where others have face similar observation as yours?

> Question 2: Moreover, I have not been able to find out how to exit the systemrescue otherwise than by pressing the on/off button. 

I think solving the previous question can solve this.

> Question 3: How come the image file created is 3.2 GB while the partition I am copying uses 4,6 (according to "properties" in my file manager)?

Have you tried to do a test restore?

---

### Post by kle on 2008-05-27
In reply to Swoosh:

Sorry, Swoosh, my mistake. I thought I was replying to a "last" message in this discussion. But there were many more pages. I shall rephrase:

I have three times made a backup of my Kubuntu partition. Three times the same thing happens: I mount my backup partition, enter the parameters I want in partimage (with or without "check partition before saving") Then I get the dialogue telling me about space usage (6%) used space (3.22 GiB) etc. Then I get a progress bar telling me that it will take about 5 minutes   
- and the message "copying used date blocks". And when the progress bar reaches 100% (after about 5 minutes) it disappears, the prompt reappears, the rest of the screen turns blue and says "please wait". I wait for an hour, close down the laptop the brutal way, restart into Kubuntu, find the file.000 I wanted, and yes, it is 3.22 GiB. 
Now: 
Q 1: What was the "please wait" about? 
Q 2: How to quit systemrescuecd without closing down computer?
Q 3: Why does partimage see 3.22 GiB (6%) of used space, while Dolphin (the Kubuntu file manager) sees 5.2 GiB (12 %)? 

I suspect I should have used some option - I am baffled by the options in f2 f3 f5, etc. I Tried *rescuecd noapic*, because I had to use noapic in the early days of Gutsy (now using Hardy). 

And no, I dare not test the restore yet.

---

### Post by timzak on 2008-05-27
Is there any reason not to use Clonezilla?  It provides a more user-friendly front end for partimage.  Forgive me if this was covered elsewhere in this thread---but the thread is rather large for me to scan through.

---

### Post by swoosh on 2008-05-28
> Q 1: What was the "please wait" about? 

First, have you *carefully* followed the steps written by the thread starter?

These may help you,

Try using the latest version of systemrescuecd.
After you have downloaded systemrescuecd, do a md5sum.


> Q 3: Why does partimage see 3.22 GiB (6%) of used space, while Dolphin (the Kubuntu file manager) sees 5.2 GiB (12 %)? 

Is Dolphin seeing accumulative size of all partitions? Did you backup *only* one particular partition? 

This could explain the size difference.

> And no, I dare not test the restore yet.

You can *select* the test simulation. It *will not* overwrite your partition. I have tried.

---

### Post by swoosh on 2008-05-28
> **timzak said:**
> Is there any reason not to use Clonezilla?  It provides a more user-friendly front end for partimage.  Forgive me if this was covered elsewhere in this thread---but the thread is rather large for me to scan through.

Hi,

There are various backup systems available with different degree of ease of use.

If you ask me, I would suggest any user to choose one that is capable of doing what the user want to do. I am sure there are other threads discussing other backup systems.

Have you got links on how to use Clonezilla? You could start a thread on this and post the link. It'll help everyone.

---

### Post by kle on 2008-05-28
Thank you for your reply, Swoosh. 

Yes, I scrupulously followed the directions given by Wieman.
I downloaded the systemrescuecd directly from the project's site a few days ago. I am afraid I did not run md5sum - because I have so often painlessly downloaded the iso files, and now I have thrown away the initial file, having made a CD out of it. 

I will indeed try the simulation you recommend when I have the opportunity in a few days. 

Could you please tell me how to correctly quit with reboot out of Partimage.

---

### Post by timzak on 2008-05-28
Basically, Clonezilla goes through a series of questions similar to xserver-xorg, so you don't have to type anything, just select source, destination drives, whether to copy partition or entire disk, etc.  Then it uses partimage based on your answers.  

[http://www.clonezilla.org/](http://www.clonezilla.org/)

Clonezilla's main purpose is to mass clone one machine to many in a quick way, but it is just as capable of cloning/imaging a single system.  It uses partimage, so I thought I'd mention it in this thread.  It might help ease the process for some.  I wasn't sure if the OP was aware of Clonezilla, and perhaps had a good reason for not using it.  

Thanks.

> **swoosh said:**
> Hi,

There are various backup systems available with different degree of ease of use.

If you ask me, I would suggest any user to choose one that is capable of doing what the user want to do. I am sure there are other threads discussing other backup systems.

Have you got links on how to use Clonezilla? You could start a thread on this and post the link. It'll help everyone.

---

### Post by sofasurfer on 2008-05-28
Ok, I'm trying to use Partimage. But when I try to enter the name of a "Image file to create/use", I am not able to type anything in the text box. What am I missing or what did I do wrong?

---

### Post by sofasurfer on 2008-05-28
??

---

### Post by swoosh on 2008-05-29
> I downloaded the systemrescuecd directly from the project's site a few days ago. I am afraid I did not run md5sum - because I have so often painlessly downloaded the iso files, and now I have thrown away the initial file, having made a CD out of it. 

It may not be md5sum issue but its a good practice to check.

> Could you please tell me how to correctly quit with reboot out of Partimage.

I have not encounter this problem so I cannot tell you exactly how. After the backup, you should not have to wait more than few seconds. I suspect it may be a burn process issue or the CD is faulty.

Try downloading systemrescuecd, check md5sum, extract the iso to a new CD and repeat the backup process again.

---

### Post by wieman01 on 2008-05-29
> **sofasurfer said:**
> Ok, I'm trying to use Partimage. But when I try to enter the name of a "Image file to create/use", I am not able to type anything in the text box. What am I missing or what did I do wrong?
Press the <tab> key perhaps?

I am back, so if there are any question that have not been answered, just shoot.

---

### Post by kle on 2008-06-07
> **swoosh said:**
> It may not be md5sum issue but its a good practice to check.
,,

Try downloading systemrescuecd, check md5sum, extract the iso to a new CD and repeat the backup process again.

I stand corrected I shall make it a matter of principle to check md5sum from now on! :-)
I have now downloaded again, to desktop; checked the md5sum ok.  
Then, I simply burnt it using the directions on [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I asked the k3b to verify written data - and when it was finished with 97% it said something about changes on segment 1 (forget the wording). (I tried twice.) Did I do something wrong?

---

### Post by swoosh on 2008-06-11
> I asked the k3b to verify written data - and when it was finished with 97% it said something about changes on segment 1 (forget the wording). (I tried twice.) Did I do something wrong?


You can try to right click on the iso and write to disc.

---

### Post by carloslosgrande on 2008-06-13
[FONT="Comic Sans MS"]Hi Weiman.
I tried this last year and everything went titsup but I reckon I did something wrong.
So, in April I saved an image again.
Just now i tried to restore it.
Titsup.
I have a few partitions;
sda1 = /
sda3 = /home
sda6 = /Home (personal files)
sdb1 = /achilles
sdb2 = / is for testing (beta hardy)
I had gutsy on sda1 and hardy on sdb2.
I saved an image of sda1 to sdb1. In April I put the new hardy on sda1.
Today I restored the image to sdb2.
Restart tells me e2fsck failed because sdb1 is mounted. Ok so [COLOR="Red"]umount /dev/sdb1[/COLOR] ..and ....its busy. Go away.
So [COLOR="#ff0000"]shutdown -r now[/COLOR] and I'm taken to login. Fine, login gets me [COLOR="#ff0000"]home directory does not exist[/COLOR] and [COLOR="#ff0000"]users HOME/.dmrc file is being ignored[/COLOR].
That'd bug me too.
So it kicks me out - [COLOR="DarkOrange"]options, restart,[/COLOR] and this time I get to the grub page and try sdb2, just to see what happens.
[COLOR="Red"]error 15 file not found
[/COLOR] So back to the other choices and I tried an earlier kernel version and presto I'm in. Login works. Great. Wait a bit,....no permissions.
Restart and choose the latest kernel. I'm in, still no permissions.
I've tried what I thought were the commands to get the permissions set but no go.
In terminal sudo chown (myuser) /dev/sd...whatever and there's no error but no change.
sudo chmod ugo+rwx /dev/sd...etc, same deal.
this is mtab;
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-18-generic/volatile tmpfs rw 0 0
/dev/sda3 /home ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/knot/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=knot 0 0
/dev/sdc2 /media/Videos ext3 rw,nosuid,nodev,uhelper=hal 0 0
and this is fstab;
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9564ae6c-8e3e-4e6c-92df-4f8ebf5470e9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=55e15da7-1363-46ab-ace5-71d8aec2917f /home           ext3    relatime        0       2
# /dev/sda5
UUID=d24e8372-3545-4f78-b9e8-e51c94517e55 none            swap    sw              0       0
# /dev/sdb5
UUID=282c4492-2149-4ca5-9bad-be40625b3370 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda6   /media/Home   ext3   defaults   0   1
/dev/sdb1   /media/achilles   ext3   defaults   0   1
It seems partimage just isn't for me. There weren't any error messages in making or restoring the image.
Ideas? Suggestions welcome.[/FONT]

---

### Post by lizzie2 on 2008-06-17
A great help,
Thanks a lot,
Les

---

### Post by RobinetDeTrie on 2008-07-07
Hello fellows !
It was much easier to follow the instructions given in the [partimage manual]("http://www.partimage.org/Partimage-manual").
This Howto isn't complete.
Example : 
- To avoid the gzip problem, you have to specify the backup file like this : /backup/myfile._gz_
- Before you restore, you have to : 
[INDENT][/INDENT]- mkdir /backup
[INDENT][/INDENT]- fdisk -l
[INDENT][/INDENT]- Mount /dev/place_of_your_backupfile /backup
just like you did when backed up your hdd.:)

[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by wieman01 on 2008-07-09
> **RobinetDeTrie said:**
> Hello fellows !
It was much easier to follow the instructions given in the [partimage manual]("http://www.partimage.org/Partimage-manual").
This Howto isn't complete.
Example : 
- To avoid the gzip problem, you have to specify the backup file like this : /backup/myfile._gz_
- Before you restore, you have to : 
[INDENT][/INDENT]- mkdir /backup
[INDENT][/INDENT]- fdisk -l
[INDENT][/INDENT]- Mount /dev/place_of_your_backupfile /backup
just like you did when backed up your hdd.:)

[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
Thanks for the link. This tutorial isn't perfect, but I guess it sort of works for a number of people.

---

### Post by jnw222 on 2008-07-11
if you compress with bzip
will archive manager be able to read it?

---

### Post by wieman01 on 2008-07-12
> **jnw222 said:**
> if you compress with bzip
will archive manager be able to read it?
You need to try that out yourself, I have never used compression.

---

### Post by kle on 2008-07-18
I have been here before, asking a few questions. Now I only want to say THANK YOU to Wieman. Playing around, I ruined my system, but had made a backup of the partition, following your directions, and restoration was perfect!

---

### Post by wieman01 on 2008-07-19
> **kle said:**
> I have been here before, asking a few questions. Now I only want to say THANK YOU to Wieman. Playing around, I ruined my system, but had made a backup of the partition, following your directions, and restoration was perfect!
Great! Good to know it still works. :-)

---

### Post by nyarlatotheph on 2008-08-19
Hi Wieman,
great tutorial, in my humble opinion better than the manual partimage.
Nevertheless, I got stuck, and was wondering if somebody can help me out. I browsed through this long long long thread, but I did not find a direct answer to my problem. First question: is there any way to make a screenshot of partimage screens, for the diagnostic? 

Anyway, these are my partitions.

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3b85ee4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       12815    92697600    6  FAT16
/dev/sda3           12816       23897    89016165    5  Extended
/dev/sda4           23898       24322     3399680   12  Compaq diagnostics
/dev/sda5           12816       16462    29294496   83  Linux
/dev/sda6           16463       16705     1951866   82  Linux swap / Solaris
/dev/sda7           16706       23897    57769708+  83  Linux

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55b3757d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36483   293049666   82
```

Now, my ubuntu Hardy resides in sda3. I can't make an image of sda3 as it is extended. Then I'll make an image of sda5 and sda7.
sda6 is swap. I want to save the image in sdb1 (external harddrive) where I prepared a partition of 100 GB (more than enough, right? I tried to resize it many times...) for my linux. Following the tutorial, everything works fine up to the step of finalizing the backup. Then I got always a message saying basically
"Error! Cannot create temp file/backup/pi25c77812.tmp/ space is not enough and dont have access rights"

Eggstreamly grateful,

Acer/Hardy Heron/Core2Duo 2GHZ/NVIDIA8600/Maxtor3200

---

### Post by wieman01 on 2008-08-22
nyarlatotheph, 

Sorry, I have not been on line for a while. Is this still an issue?

---

### Post by nyarlatotheph on 2008-08-23
> **wieman01 said:**
> nyarlatotheph, 

Sorry, I have not been on line for a while. Is this still an issue?

Yes, if you have time  :)
I was meanwhile in the partimage official forum, and found it a rather sad place. Imagine an hospital without a doctor, a pub without beer, or a forum without moderator, with a couple of new people every month reporting different problems and nobody answering. Well, that's pretty much it. Wieman01,if you have a clue it would be great. Besides, I am around because of my job and I won't have access to my linux box until next friday, so no hurry...
Cheers,

---

### Post by Xer0mus on 2008-08-23
Hi there, 

I'm running Ubuntu 8.04.1 x64, and have a total of 2 Partimage backups residing in my / and /home directories. Every time I try to use Brasero to burn these images into a data DVD, Brasero gives me a "The file (backup_filename_here.000) is unreadable" error. I thought this was initially a permissions problem and thus ran Brasero as root, but this would result in a segmentation error (but strangely this would only happen if there is a blank dvd already inside).

Short of using an external HD and transferring these partimage backups, is there any other way of getting these off my internal HD?

Thanks for the help in advance.

---

### Post by wieman01 on 2008-08-24
> **nyarlatotheph said:**
> Hi Wieman,
great tutorial, in my humble opinion better than the manual partimage.
Nevertheless, I got stuck, and was wondering if somebody can help me out. I browsed through this long long long thread, but I did not find a direct answer to my problem. First question: is there any way to make a screenshot of partimage screens, for the diagnostic? 

Anyway, these are my partitions.

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3b85ee4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       12815    92697600    6  FAT16
/dev/sda3           12816       23897    89016165    5  Extended
/dev/sda4           23898       24322     3399680   12  Compaq diagnostics
/dev/sda5           12816       16462    29294496   83  Linux
/dev/sda6           16463       16705     1951866   82  Linux swap / Solaris
/dev/sda7           16706       23897    57769708+  83  Linux

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55b3757d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36483   293049666   82
```

Now, my ubuntu Hardy resides in sda3. I can't make an image of sda3 as it is extended. Then I'll make an image of sda5 and sda7.
sda6 is swap. I want to save the image in sdb1 (external harddrive) where I prepared a partition of 100 GB (more than enough, right? I tried to resize it many times...) for my linux. Following the tutorial, everything works fine up to the step of finalizing the backup. Then I got always a message saying basically
"Error! Cannot create temp file/backup/pi25c77812.tmp/ space is not enough and dont have access rights"

Eggstreamly grateful,

Acer/Hardy Heron/Core2Duo 2GHZ/NVIDIA8600/Maxtor3200
What file format is "sdb1"? A FAT32 system?

I have never seen this error message before, but perhaps the image you are pulling is greater than 3GB and conflicts with the constraints of FAT32. 

Let me know what file system "sdb1" is and how you mounted is (i.e. the command you used). See you next week!

---

### Post by wieman01 on 2008-08-24
> **Xer0mus said:**
> Hi there, 

I'm running Ubuntu 8.04.1 x64, and have a total of 2 Partimage backups residing in my / and /home directories. Every time I try to use Brasero to burn these images into a data DVD, Brasero gives me a "The file (backup_filename_here.000) is unreadable" error. I thought this was initially a permissions problem and thus ran Brasero as root, but this would result in a segmentation error (but strangely this would only happen if there is a blank dvd already inside).

Short of using an external HD and transferring these partimage backups, is there any other way of getting these off my internal HD?

Thanks for the help in advance.
Weird.

Using an external USB storage device would be the simplest solution if you ask me. If that's not an option, you could try to change ownership of the file. Use an unprivileged user and try to burn the image once again. Really sounds like a permission/ownership problem.

---

### Post by nyarlatotheph on 2008-08-31
Hi Wieman,

> **wieman01 said:**
> What file format is "sdb1"? A FAT32 system?

I have never seen this error message before, but perhaps the image you are pulling is greater than 3GB and conflicts with the constraints of FAT32. 

Let me know what file system "sdb1" is and how you mounted is (i.e. the command you used). See you next week!

I have tried to partition again sdb: here you go
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       12815    92697600    6  FAT16
/dev/sda3           12816       23897    89016165    5  Extended
/dev/sda4           23898       24322     3399680   12  Compaq diagnostics
/dev/sda5           12816       16462    29294496   83  Linux
/dev/sda6           16463       16705     1951866   82  Linux swap / Solaris
/dev/sda7           16706       23897    57769708+  83  Linux

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55b3757d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650       15298    61440592+   7  HPFS/NTFS
/dev/sdb3           15299       22947    61440592+   7  HPFS/NTFS
/dev/sdb4           22948       34723    94590720    7  HPFS/NTFS
```

I had tried again to transfer my sda5 to sdb4, getting the usual cannot create temp file error. The mount command I used was:
```
mount /dev/sdb4 /backup
```
I did not use any compression and I broke the files at the suggested size.
Any idea? Thanks in advance!

---

### Post by nyarlatotheph on 2008-09-03
Ehm...bump?

---

### Post by wieman01 on 2008-09-04
> **nyarlatotheph said:**
> Hi Wieman,

I have tried to partition again sdb: here you go
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       12815    92697600    6  FAT16
/dev/sda3           12816       23897    89016165    5  Extended
/dev/sda4           23898       24322     3399680   12  Compaq diagnostics
/dev/sda5           12816       16462    29294496   83  Linux
/dev/sda6           16463       16705     1951866   82  Linux swap / Solaris
/dev/sda7           16706       23897    57769708+  83  Linux

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55b3757d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650       15298    61440592+   7  HPFS/NTFS
/dev/sdb3           15299       22947    61440592+   7  HPFS/NTFS
/dev/sdb4           22948       34723    94590720    7  HPFS/NTFS
```

I had tried again to transfer my sda5 to sdb4, getting the usual cannot create temp file error. The mount command I used was:
```
mount /dev/sdb4 /backup
```
I did not use any compression and I broke the files at the suggested size.
Any idea? Thanks in advance!
Problem seems to be that 'sdb' is an NTFS file system. So I guess RescueCD is complaining that it cannot write to it. Do you experience the same issue when you try to write stuff on an EXT2/3 
hard-disk?

---

### Post by nyarlatotheph on 2008-09-08
> **wieman01 said:**
> Problem seems to be that 'sdb' is an NTFS file system. So I guess RescueCD is complaining that it cannot write to it. Do you experience the same issue when you try to write stuff on an EXT2/3 
hard-disk?

Thanks wieman and apologies for my late answer...basically my Liteon power supply for the linux box exploded (!) and I am waiting for the replacement...Cheers

---

### Post by Halibutt on 2008-09-11
One thing nobody mentioned so far. Should partimage have problems reading or finding your backup files when restoring, you should start partimage **in the directory where the files are located**. In my case it involved 
```
cd /media/External_hd/ubuntu_backup
sudo partimage
```

And then point the program to the file located in /media/External_hd/ubuntu_backup. I spent several hours trying to figure that out, hope it helps someone. 
Cheers

---

### Post by SilverWave on 2008-09-11
I had a problem with restoring from a previously saved image.
This may have had nothing to do with partimage, it could have been caused by the usb drive it was stored on or the image could have been corrupted ...but that's exactly the point. 

You need to do a full restore to ensure that the image you are depending on is actually valid!

This experience caused me to investigate other solutions that do not rely on a single vulnerable file (the all your eggs in one basket problem).

The best I have came up with is rsync. The link below will get you up and running in about 5 mins if you choose to go this route.

[RLB (Rsync Local Backup). An easy way to backup your system](http://ubuntuforums.org/showthread.php?p=5740624#post5740624)

---

### Post by PunisherP on 2009-03-15
Wow, thank you! [right][[color=#FFFFFF]_simulation credit_[/color]](simulationcredit1.com)[/right]

---

### Post by rmartinus on 2009-05-03
Thanks.. I'll give this a try on my laptop!

---

### Post by Wookiee on 2009-05-10
Well, I've hit a snag.

After running for a minute or two, it gives an error message that the volume I'm trying to save to is full. But the drive is a nearly empty 1 TB drive! However, after rebooting and looking at the drive's contents, partimage hadn't saved anything to it.

It's an NTFS drive, if that makes a difference.

Yes, I'm certain I specified that particular drive as the target.

---

### Post by wieman01 on 2009-05-10
> **Wookiee said:**
> Well, I've hit a snag.

After running for a minute or two, it gives an error message that the volume I'm trying to save to is full. But the drive is a nearly empty 1 TB drive! However, after rebooting and looking at the drive's contents, partimage hadn't saved anything to it.

It's an NTFS drive, if that makes a difference.

Yes, I'm certain I specified that particular drive as the target.
It's likely you haven't correctly mounted your HD. Could you check that once again? Sounds familiar.

---

### Post by colau on 2009-05-10
> **Wookiee said:**
> Well, I've hit a snag.

After running for a minute or two, it gives an error message that the volume I'm trying to save to is full. But the drive is a nearly empty 1 TB drive! However, after rebooting and looking at the drive's contents, partimage hadn't saved anything to it.

It's an NTFS drive, if that makes a difference.

Yes, I'm certain I specified that particular drive as the target.
You did not mount your partition where you would like to save your backup.
mount /dev/sdaX /mnt/backup

X is the value where you want to save the backed up file.

Then selecting the partition which you want to back up
typing
/mnt/backup/filename in the blue dialog press F5 then continue...

---

### Post by Wookiee on 2009-05-10
Yes, I did that. It's dev/sdc1.

---

### Post by wieman01 on 2009-05-11
What does...
> fdisk -l
...say?

---

### Post by already710 on 2009-05-14
My thoughts and prayers are with you buddy.  Everything will be ok, good luck! 

[url=http://simulationcredit1.com][color=#F8F8F3][u]simulation
credit[/u][/color][/url]

---

### Post by already710 on 2009-05-14
My thoughts and prayers are with you buddy.  Everything will be ok, good luck! 

[url=http://simulationcredit1.com][color=#FFFFFF][u]simulation
credit[/u][/color][/url]

---

### Post by wieman01 on 2009-05-15
> **already710 said:**
> My thoughts and prayers are with you buddy.  Everything will be ok, good luck! 

[url=http://simulationcredit1.com][color=#FFFFFF][u]simulation
credit[/u][/color][/url]
Whatever...

---

### Post by already710 on 2009-05-29
:popcorn:That's great work. Thank you so much for your valuable post
[[color=#FFFFFF]_simulation credit_[/color]](http://simulationcredit1.com)

---

### Post by tedrogers on 2009-06-02
Hi Wieman,

I've been using partimage now on a Linux System Rescue CD for some time now, and I love it. Very reliable. Very easy, once you know the steps.

However, I have got to a stage in my ubuntu life where I have a lot of media which bloat my backup, and I want to omit / exclude certain folders from my backup.

I have looked into this but can't find an option in partimage to do this.

Is there such a function to omit / exclude specific folders, or is there another backup application that might help?

I have looked into remastersys, but it's not that clear how to restore from any live .iso it will create and the exclude folder option seems flaky.

Thanks in advance.

---

### Post by wieman01 on 2009-06-02
Hi Ted, 

Nice to see you around. It's been a while.

No, Partimage won't be a good choice in this case. You could look into 'rsync' if you want to back up media and stuff like that. Used it before? I sort of prefer that to Partimage for non-system backups.

---

### Post by tedrogers on 2009-06-02
> **wieman01 said:**
> Hi Ted, 

Nice to see you around. It's been a while.

No, Partimage won't be a good choice in this case. You could look into 'rsync' if you want to back up media and stuff like that. Used it before? I sort of prefer that to Partimage for non-system backups.

Hi wieman, it has been a while...guess I'm getting better these days! :) A sad fact about about needing less help is that you lose touch I guess. :( 

I am glad to see you're still around though, serving the community and building your beans! LOL :D

No, I think you misunderstand me, I don't want to backup my media...I want to omit those folders and just backup my raw OS and applications, custom settings etc. My fault for not making it clearer.

I'd like partimage to be able to exclude folders like MUSIC, PICTURES, VIDEO and DOCUMENTS in the HOME directory.

So I guess it won't huh?

I will look into rsync though, but don't think it will do what I need.

---

### Post by wieman01 on 2009-06-02
> **tedrogers said:**
> Hi wieman, it has been a while...guess I'm getting better these days! :) A sad fact about about needing less help is that you lose touch I guess. :( 

I am glad to see you're still around though, serving the community and building your beans! LOL :D

No, I think you misunderstand me, I don't want to backup my media...I want to omit those folders and just backup my raw OS and applications, custom settings etc. My fault for not making it clearer.

I'd like partimage to be able to exclude folders like MUSIC, PICTURES, VIDEO and DOCUMENTS in the HOME directory.

So I guess it won't huh?

I will look into rsync though, but don't think it will do what I need.
I am sorry, Ted. It's late so I misread your post.

Partimage cannot do that afaik. However, you could create a separate partition for your media. That's what I do, so when I run Partimage it only backs up my system/home partitions. My actual data does not reside in /home but on a separate data partition.

Would that make sense?

Yeah, beans been going up, have to say I still enjoy my time in here. Would be nice to see you around a bit more. :-)

---

### Post by tedrogers on 2009-06-02
> **wieman01 said:**
> I am sorry, Ted. It's late so I misread your post.

Partimage cannot do that afaik. However, you could create a separate partition for your media. That's what I do, so when I run Partimage it only backs up my system/home partitions. My actual data does not reside in /home but on a separate data partition.

Would that make sense?

Yeah, beans been going up, have to say I still enjoy my time in here. Would be nice to see you around a bit more. :-)

Maybe I'll do that then Wieman...I'll need to spend some time with my friend gparted...but it should be possible. :)

Cheers bud!

---

### Post by Nyken on 2009-06-11
Just want to say thank you a billion times for this thread and for it letting me know this application exists! Been wanting a "Ghost" program for a long long looooong time, so major kudos to the Open Source community for thinking of this. If I can get EverQuest to really run with nothing but GNU apps, I will never have to go back to Windows again.

---

### Post by wieman01 on 2009-06-11
> **jamiyoel said:**
> I tried this method but my backup image got corrupted. How can I secure image?
Mmm... You mean recover your image? I am afraid I don't know a solution here.

---

### Post by viking_maniac on 2009-09-01
First of all, you don't need a rescue-CD. Just use your Ubuntu install-CD/DVD (Live).
I have a second partition (/misc), on there I put partimage and made a new folder for the images themselves.
I booted with the Ubuntu install disc and mounted the second partition. Note: do not mount the partition (main SDA1) that you're going to backup/restore.
Then i run /misc/pi/partimage from the terminal as sudo.
The GUI is simple and effective.
I did use the default compression without any problems during this test. No errors and things work well as far as I've tried to now.

It looks great and it will save you a lot of time. What I do miss, is a "verify volume" option like you have on Partition Magic and Norton Ghost for Windows. Though, of all the zillion times I've created and restored partitions on Windows, the verify never failed. But it would've given me more piece of mind--unless I'm missing something here.

I downloaded "partimage 0.6.7" from the package manager.

:)

---

### Post by Mo (Beginner) on 2011-01-07
Is it possible to burn DVD's with partimage?
I've made a backup of my main partition and I've saved it to an external hard drive, but if my computer crashes, isn't there a big chance this hard drive crashes also? I'm searching for a safe way to save the backup file, any other options are welcome too. :)

---

