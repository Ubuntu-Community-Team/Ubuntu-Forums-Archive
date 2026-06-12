---
title: "Ubuntu Installation goes bad"
date: 2015-12-15
forum: New to Ubuntu
---

### Post by stamatis3 on 2015-12-15
Hello fellas, 

I am kinda new on this OS and I am trying to install Ubuntu allongside Windows 7 which are currently installed on my computer. The problem I meet is that during the installation no partitions are found. Any ideas are welcome, keep in mind i am totaly new so well explained instructions are more than welcome.
[ATTACH=CONFIG]266179[/ATTACH]

---

### Post by Vladlenin5000 on 2015-12-15
Hi and welcome.

One possible cause of what you're experiencing is hibernated (Windows) partitions. So, first of all, make sure you're booting from a fully shutdown Windows when installing. Before that, however, you should make space for Ubuntu by shrinking one or more of the existing partitions *IN WINDOWS* using Windows tools. Then reboot and allow it to check the drives and assure Windows is booting properly before shutting it down, inserting the Ubuntu installation media and booting from it.

Another possibility is the existence of dynamic partitions, a Microsoft proprietary technology that prevents other OSs from correctly "seeing" the drive's partitions.

---

### Post by Bashing-om on 2015-12-15
stamatis3; Hello;

^^
'Nother possibility is in MBR partitioning Windows using up all 4 available primary partitions ?

Would be good to see what the current partitioning is ;
Post back - Between code tags - the output of linux terminal command ( from the live installer -> try ubuntu  mode :
```

sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]we work hard
[INDENT][INDENT]so you can tell others 
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Vladlenin5000 on 2015-12-15
> **Bashing-om said:**
> 
'Nother possibility is in MBR partitioning Windows using up all 4 available primary partitions ?

A typical situation found in old ACER notebooks (and a few others). Usually the previous dialog screen shows the "install alongside..." option grayed out and the screen shown in the OP usually presents all the partitions as they should be. As such I suspect something else is at play here. 

That said, please follow the instructions in the previous post so we can know what the situation really is and then, hopefully, provide an easy solution.

---

### Post by stamatis3 on 2015-12-18
Hello fellas,

Thank you for your time and replies. I was away and i didnt had the chance to answer to you earlier

> Another possibility is the existence of dynamic partitions, a Microsoft  proprietary technology that prevents other OSs from correctly "seeing"  the drive's partitions.

I followed the video of this guy in youtube : [https://www.youtube.com/watch?v=XYVOtwsukEQ](https://www.youtube.com/watch?v=XYVOtwsukEQ) and i changed my disk from dynamic to basic,

Then I used AOMEI to create another partiotion which i formated to ext3


> Post back - Between code tags - the output of linux terminal command

```
odel: ATA HGST HTS725050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  316MB  315MB   primary   ntfs         boot
 2      316MB   422GB  422GB   primary   ntfs
 3      422GB   476GB  53.7GB  primary   ext3
 4      476GB   500GB  24.3GB  extended               lba
 5      476GB   500GB  24.3GB  logical   ntfs


Error: /dev/sdb: unrecognised disk label                                  

Model: JetFlash Transcend 16GB (scsi)
Disk /dev/sdc: 16.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      3015kB  16.2GB  16.2GB  primary  fat32        boot, lba


```

There are the resutls.
PS1 : ty for the tag code guide !
PS2 : I dont know if it helps but the laptop i am trying to install the Ubuntu is an HP 8570w

---

### Post by Bashing-om on 2015-12-18
stamatis3; Well ...

1st the good news .
The system is bios based and as such "msdos' is the correct partitioning and as well as this is "msdos" then booting from Master boot Record (MBR) is also correct.

Now for the problems 
1) you have set the ubuntu file system as ext3, while doable, ext4 ( 4th generation) has been tested now for several years and is stable as a rock. ext4 is the standard  and has many enhancements and improvements over ext3 . ( file journaling for only 1 of the enhancements )

2) you have made no provision in that 'extended' partition for ubuntu's swap partition. Be a bit if a pain now to make it up . Depending on how much ram you have installed is how large to make this partition. 

I would be highly in favor of starting all over; simply wiping the ext3 partition, in the extended partition shrink the present ntfs partition and make up a new ubuntu swap partition - we can have an additional 128 logical partitions in this 'extended' partition - and install afresh  with ext4 for the ubuntu operating system .. the swap partition takes no file system  - just tell the installer this partition is swap & the installer will take care of it .

If you leave what is now the ext3 partition as "unallocated space - after it is deleted -  then in the install process choose the option " something else "  One can then install onto this space .

[INDENT][INDENT]once you have done 3 or 4 installs
[INDENT][INDENT][INDENT]ain't nothing to it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stamatis3 on 2015-12-19
Dear Bashing-om,

  Although i appriciate the fact that you spend your time to solve my problem i am afraid i didnt understood anything. The only think that i understood is to reformat the ext3 partition to ext4 which i can do. Please give me detailed adivce for the rest

---

### Post by buzzingrobot on 2015-12-19
Reformatting the ext3 partition won't solve your problem. Linux needs a swap partition. Not a file, like Windows uses, but a separate partition. 

 Currently, you have no partition available that can be used as a swap partition. So, you must create one. Bashing-om has given you good advice. The size of your swap partition can vary. But I'd suggest sizing it to be equal to the amount of RAM in the machine if that is 4 gigs or more, and approx. twice the amount of RAM if you have a small amount, like 2 gigs or less. (There is no formula to determine the perfect size of a swap partition. One caveat:  If your machine is capable of hibernating and you want to hibernate it in Linux, the swap partition must be at least as large as the total amount of RAM.)

---

### Post by stamatis3 on 2015-12-19
Dear buzzingrobot,

Thank you for your advice it seems now that i read it more carefully to udestand it better. So I need two particions my machine has a 4gib ram so I need to make a partition of 4 gigs to install ubuntu ? is that what you tell me ? or i have to make a partition inside a partition ?

PS: Any guide to make this swap partition would be welcome.

---

### Post by Herdo on 2015-12-19
I assume that ext3 partition is what you've allocated for Ubuntu correct?  If so, wipe it using the "disk management" tool in Windows 7.  This is very easy to do, and when you are done it should say "Unallocated" or "Free Space" or something similar.

[https://www.youtube.com/watch?v=vSshONNf4dM](https://www.youtube.com/watch?v=vSshONNf4dM)

After that, renter the Ubuntu installation again.

When you are asked how you want to install Ubuntu (overwrite Windows, along side Windows, or "Something Else"), choose "Something Else".

You should see the 50GB listed as free space.  

Create a swap partition of 4GB, a "/" partition (ext4) of 20GB and with the rest of the free space (about 26GB) create a home partition (ext4), as shown here:

[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

Follow the instructions under "If you have a blank disk" starting at step 3, and don't create the optional /boot, /var, or /tmp partitions.  Then click install now.

---

### Post by stamatis3 on 2015-12-19
Dear Herdo,

I did as you said i deleted the partition formated as ext3 and at the windows manager it said Unllocated space. Then i run the install and when i was about to choose the partiotion the problem was not solved 

I attach an image of the installation proccess

---

### Post by Bashing-om on 2015-12-19
stamatis3; Hey hey ... 

You are making progress ..

let me give you the background on what and why you are doing .

In the hard disk partitioning scheme that is present on your system - msdos - one may have a maximum of 4 primary partitions due to addressing constraints .
The way around this limit of 4 is to make one of those 4 primary partitions as extended, now in this 'extended' partition we can make up "logical" partitions - up to 128 additional partitions.

Now currently as of your last posted 'parted' you have
2 primary partitions devoted to Windows
1 primary partition devoted to ubuntu
and an extended partition containing 1 logical partition. -> this logical partition also devoted to windows.

So, we require
a) the space that was partition sda3 ( sda = 1st hard drive and the 3 designates the 3rd partition ) that was of file system ext3 - now unallocated .. and available for use . We will in " something else" point the installed to this usable space.

b) we need in addition to the space to install the ubuntu operating system, a partition to act as paging from memory and/or overload. That is the function of the swap partition . In order to make up this swap partition it MUST be contained as a 'logical' partition in that ' extended' partition. Presently there is a ntfs logical partition ( sda5 ) taking up all the space in that extended partition ( sda4 ). In Windows we must make a means of allocating space for ubuntu's swap partition in this container . If possible the easier thing to do is shrink the " 5      476GB   500GB  24.3GB  logical " that is presently 24.3 gigs to allow you to make up a ubuntu swap partition of 4.3 gigs .

Now if it proves that you can not allocate that 4.3 gigs from sda4, then it gets a bit more complicated to rob Peter and pay Paul.
We must then make that 'extended' partition larger by taking space away from ubuntu's primary partition sda3 . Extending the 'extended' partitiion's boundry into what is now that unallocated space  by the needed 4.3 gigs. This change will alter Window's partition table and you have to make Windows reset the table by running Windows tool "chkdsk" . 

Be a great idea and a thing to do regardless is the make sure that Windows has updated it's partition table; You have run Windows 'defrag' twice ? and have run Windows chkdsk twice ? Yes ?

All in the set up ; Generally it is not this demanding . However this is a good 
[INDENT][INDENT]learning experience
[/INDENT][/INDENT]

---

### Post by Geoffrey_Arndt on 2015-12-19
Excellent 1st Post by Herdo! . . . . 

Additionally, in the legacy (now becoming antiquated) MS-Dos MBR (master boot) disk system, the 4th partition is always like a container with a label being simply the name of the 4th partition (sdaxx),  _but inside_ the container will be 2 or more "logical" (psuedo) partitions, including swap.    

SO, if you had 10 different Linux distributions inside the 4th partition, you would then have 11 partitions as all the distros would share the 1 swap partition.

Oops!  Looks like some further updates posted before I entered this . . . by the way . . in the install process, did you choose the something else option?    Also, my personal preference is to pre-format the partition where Ubuntu will be installed by making it ext4 . . . . it seems to provide a smoother install experience (in my opinion).

G

---

### Post by stamatis3 on 2015-12-20
Dear Bashing-om,

Thank you for your extended explanation on the problem. I think I do undestand what I need to do but I still have questions.

So this is the current partition table.

```
Model: ATA HGST HTS725050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  316MB  315MB   primary   ntfs         boot
 2      316MB   422GB  422GB   primary   ntfs
 3      476GB   500GB  24.3GB  extended               lba[COLOR=#ff0000]  <---- So you ask me to change this to 20GiB and split it to two partitions in order to have an extended partition for Ubuntu.[/COLOR]
 5      476GB   500GB  24.3GB  logical   ntfs


Error: /dev/sdb: unrecognised disk label                                  

Model: JetFlash Transcend 16GB (scsi)
Disk /dev/sdc: 16.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      3015kB  16.2GB  16.2GB  primary  fat32        boot, lba

```

What I dont understand is why I cant split the 50 GB which are not partitioned at the moment ( you can notice this gap of space usage between 2 and 3 ) in order to make an extended partition ?


Now if this is not possible how i am going to shrink the extended partition of windows since the disk manager does not reveal that partition (I think at least)

---

### Post by Bashing-om on 2015-12-20
stamatis3; Hey !

You are quite correct in there being existing unallocated space between sda2 - primary partition and the extended partition sda3.

That extended sda3 partition is a container for additional 'logical' partitions. There should exist no reason why in ubuntu's partition editor - GParted ; from the liveDVD - that you can not extend sda3 to the left and take up that unallocated space for sda3. Once this is done, then one can make up additional partitions ( as logical ) and one of these additional partitions make up ( somewhat in excess of 4 gigs ) ubuntu's swap partition.
Now at this time, you have to make up provisions of where to install ubuntu . That ext3 partition no longer exist and is now that unallocated space.
You must decide if you want that partition as a 'primary' partition or as a 'logical' partition . Understand, that you still must make provisions in the 'extended' partition to make up a 'logical' swap partition. Unlike Windows, 'buntu will happily install to a logical partition . You are the system administrator, If you want to keep future expansion options open, make up ubuntu in that 'extended' partition. That will leave a 'primary' partition available in the event of in the future expansions, by further reducing Windows partitions and having access to this additionally available 'primary' partition .

Keep in mind that in moving partitions sizes ... must have "unallocated" space next to the partition that is being moved in that direction. In this instance of moving sda3 to the left, you have it . Always a good idea to defrag Windows' file system prior to moving data ( here sda5 is involved ) Then one MUST tell Windows that the partition table is to be changed . run Windows 'chkdsk' twice .

a) 45.7 Gigs as a 'primary' partition for the ubuntu operating system , having expanded the 'extended partition to the left by 4.3 Gigs AND making up the swap partition as logical within that extended partition.

b) Move the present 'extended' partition to the left taking up all the unallocated space; and in this newly expanded partition make up the 'logical' partitions to hold the ubuntu operating system AND the swap partition.

If you have any doubts about the procedure -  provide a screen shot of what GParted relates to the sda drive . Here is true that a picture is worth a thousand words .

It is good to have options
[INDENT][INDENT]but options means making choices -> opportunity cost
[/INDENT][/INDENT]

---

### Post by Kris_M on 2015-12-22
noob. The first time(s) I tried to install the iso(dvd) I powered down, then turned computer back on.  It could never find Win7.  Then I found this thread and spent some time chasing my tail - my drives are already basic, but it didn't seem able to create an ext4 in the 70gb gap in the middle of my SSD. 

I then rebooted from 7 w/o shutting it completely off and it found 7 and nicely automatically created an ext4 and swap partitions and install went well. Dual boot works great.

Hope that helps a tiny bit.

GA-Z87N-WIFI mobo, i5 4670K, CoolerMaster Hyper TX3 hsf, 8GB ballistix  1600(2x4), Win7 Pro x64 SP1 current, Sammy 250GB Evo SSD, BitFenix  Prodigy black case.

---

