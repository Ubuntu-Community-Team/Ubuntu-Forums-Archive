---
title: "Installing Lucid 64 bit over Lucid 32 bit on laptop partition"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by aka-John99 on 2012-01-12
Hi,

Can anyone help a newbie please by explaining how to install 64 bit Lucid over the existing 32 bit installation.

I already have a bootable Lucid 32 bit USB stick and the required live CDs. I am hoping to be able to install 64 bit version over the top of the 32 bit version in the existing Ext4 partition, or its space.


Installing Lucid 64 bit over Lucid 32 bit on laptop partition
This is a recent laptop, Windows 7 installed on primary MBR NTFS
Single internal 750GB hdd,  USB connectors, and internal CD/DRD rewriter
Lucid 32 bit installed and working on 2nd partition
Bootable Lucid 32 bit USB stick is available.
Integrity checked 64 bit Lucid desktop and Alternative install disks being prepared now.

I am not sure if there would be any advantage in tying to use something other than the MBR system, but I suspect that is not an important issue right now. I am bot concerned about retaining settings or files from the Lucid 32 bit installation, any thing I want i.e, personal files, and bookmarks is backed up and available.


N.B.
It may be of help to read an adjacent question I have just asked about a loosely related matter,
[http://ubuntuforums.org/showthread.php?t=1907850](http://ubuntuforums.org/showthread.php?t=1907850)                           [Installing 32 bit LTS Lucic on 2nd HDD 2nd primary partition]("http://ubuntuforums.org/showthread.php?t=1907850")

Another reason to avoid unnecessary use of CLI I make too many typos even when there is a spell checker  :(

---

### Post by oldfred on 2012-01-12
If you have nothing you want to save, you just use manual install and choose the existing / (root) partition to install to. It should find your existing swap automatically. Only if you want to change partitions, then you can use gparted from liveCD (swapoff to unmount swap) to adjust partitions.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Most users might want to backup from 32bit install, I will just link to this in case someone is interested.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by lechien73 on 2012-01-12
The best thing to do is just to start the installation procedure as if it's a new install, but point it towards the existing Ubuntu partitions.

If you have information in your /home folder that you wish to keep (documents etc.), then back these up first; however you can also stipulate that Ubuntu doesn't touch /home during the installation process.

There isn't a direct 32-bit to 64-bit upgrade path, so completely re-installing is the best option.

**EDIT:** @oldfred - my goodness...you type at the speed of light :D

---

### Post by aka-John99 on 2012-01-12
Thanks everyone. I may leave taking action on this till next week. I do not want to work on two computers at the same time and have both US.

> **lechien73 said:**
> The best thing to do is just to start the installation procedure as if it's a new install, but point it towards the existing Ubuntu partitions.

If you have information in your /home folder that you wish to keep (documents etc.), then back these up first; however you can also stipulate that Ubuntu doesn't touch /home during the installation process.

There isn't a direct 32-bit to 64-bit upgrade path, so completely re-installing is the best option.

**EDIT:** @oldfred - my goodness...you type at the speed of light :D

Not sure I remember from the last install an option to point the install at a specific partition. I seem to recall the options as

[LIST]
[*]Install as single OS on the HDD replacing any existing OS, 
I do not want that, I am keeping the Windows 7 OS
[*]Install alongside existing OS s
[LIST]
[*]I could live with that and have the space to do it,
No doubt I could use a simple graphical tool to adjust partitions later
[/LIST]
 
[*]Install specifying partition details
[LIST]
[*]That could be problematic and dangerous,i could easily make a mistake
[*]Are there any guides on how that works ?
[B]
Edit[/B] having just installed 11.10 on USB stick partitioning asI installed I am now more familiar with the install process (GUI on the partitioning)
[/LIST]
 
[/LIST]
I already have a problem that I am going to need to sort out. If I use the disk utility at present I get a warning about the partition alignment. Not sure how important it is. I will try to attach a screen shot.
(Bumlbing along blindly without reading instructions, no idea if they need to be in specific formats, or how to convert within Ubuntu -- ahh thats good, it tells you as you attempt it)

Do not know whether you will answer that here or would prefer another thread started.

---

### Post by oldfred on 2012-01-12
The install process is the same with every version with minor changes in screens. Herman's site has lots of detail (some may thing too much for a new user, but it is good) and aysiu's is straight forward.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by aka-John99 on 2012-01-12
Thanks Fred,

I had already found the Psychocats tutorials, but had missed the article  you linked to, I don't think it was listed in the sidebar.
I will look at Herman's site later, looks useful. 
I did not want to get half way through an install and find it was asking something I do not yet understand.

Any comments on the partition alignment warning?
Am I merely wasting a bit of space, or is it going to affect hdd  performance, and if so what is the solution, will GParted fix that?  (e.g. by leaving round to cylinders option ticked/checked).

Its past bedtime here and have work tomorrow, 
goodnight all,
John.

---

### Post by oldfred on 2012-01-13
It is not round to cylinders any more. Are you using a older version of gparted? The older versions would move Windows Vista that had a new default of 2048 as the start sector to the old start that XP or Linux was using of 63. Now all systems start at 2048 for better compatibly with SSD & 4k drives.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by aka-John99 on 2012-01-16
Am I correct in saying that I could in my circumstances ignore the Disk utility warning as it only relates to an extended partition from a post you linked


[LIST]
[*]You can ignore any extended partitions; you're only interested in primary and logical partitions
[http://ubuntuforums.org/showpost.php?p=10450466&postcount=9]("http:///")
[/LIST]
My currrent partitions
```
 Model: ATA WDC WD7500BPVT-2 (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start        End          Size        Type      File system  Flags
 1      2048s        327682047s   327680000s  primary   ntfs         boot
 2      756082686s   1465147391s  709064706s  extended
 5      756084736s   1444001791s  687917056s  logical   ext4
 6      1444003840s  1465147391s  21143552s   logical
 
``````
 Rem  not divisible by 8
2 start 756082686 / 8 =  94510335.75 but extended 
```> **oldfred said:**
> It is not round to cylinders any more. Are you using a older version of gparted? The older versions would move Windows Vista that had a new default of 2048 as the start sector to the old start that XP or Linux was using of 63. Now all systems start at 2048 for better compatibly with SSD & 4k drives.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

I have several versions of GParted available, so should be able to use whichever is best. For instance I have GParted on on the Live CDs for Ubuntu 10.4 and 11.10 besides some other versions of GParted.

It seems a good idea to try to remove the error, what would the recommended method be to do that, if possible without re-installing everything. Note the NTFS partition has Windows 7 on it. I am not 100% certain but do not think the Windows disk image will re-install to a preformatted disk, I am assuming it needs an unalocated hdd.

It appears if I can shift the start point of the extended partition ( **edit **[s]3/4 GiB [/s] ) in to the adjacent free space I will get the correct alignment. Is that correct ? Will GParted do that (running from a CD/DVD) ok without data loss ? (I have backups and so am able to cope with data loss, but if the Windows Partition is unbootable it takes me around 2 hours to restorer it, then I am back at square one with a misaligned partition warning once I install Ubuntu )

Or am I going about all this the wrong way ?

**edit **[I]incorrect above, misalignment calculated on starting sector being divided by 8 is 3/4
these sectors are reported as 512Bytes, so relating to a 4kiB blocks mis alignment of start was; depending on which direction the boundary is; was only 1kiB or 3kiB   
[/I]

---

### Post by oldfred on 2012-01-16
I do not think the extended matters. You do not write into the extended partition directly as it is just the container for all the logicals. So the start of the extended can be anywhere.

I try to use the newest gparted either a new gparted liveCD or the latest Ubuntu liveCD with gparted, or Parted Magic's liveCD.

If you have space you can move extended and you should not have data loss. But anything can happen, so it is always best to have good backups.

---

### Post by aka-John99 on 2012-01-17
Preventing Alignment errors  ( as being reported by disk utility.) on extended partition container

As I remarked above, this may not be important in this instance, but it is later on in the procedure.

AFAIK the Ubuntu installer will not necessarily align partitions correctly. Recent versions of GParted do have the option to align to MiB boundaries, which does resolve the issue. Decrementing the preceeding value by any value I tried brings the  boundary value back into alignment. (There is not the fine control needed to scecify start positionsin 512B sectors )

---

### Post by aka-John99 on 2012-01-17
Final solution, this is what I did.

[LIST=1]
[*]Changed my mind about installing over the old version, I have plenty of space for two versions
[LIST]
[*]I shrank the original partition, using GParted
[/LIST]
[*] Using Ubuntu 11.10 install disk created partitions I required in the unalocated space created above
[LIST]
[*]I used the something else option, so i could create multi partitions for the install
[*]I had already practiced doing a USB stick full install
[*]this resulted again in a partition not being aligned when viewed in Disk Utility
[*](trying 10.10 LTS I seemed to get several partitions out of alignment)
[/LIST]
[*]Ran GParted to clear up the reported mis alignment
[LIST]
[*]I know this probably is not necessary, but it does seem best to not have errors reported.
[/LIST]
[/LIST]
Guides documentation and links in this thread mention the partition arrangements,and suggested sizes. What I did not come across was explanations about how the installer dealt with installing into specific partitions, and creating partitions for /home or other directories, that is where the practice on the full install onto a USB came in useful.

---

