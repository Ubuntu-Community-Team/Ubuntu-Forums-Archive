---
title: "Is Understanding partitions harder than you think ?"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by hebdave on 2014-02-16
High sorry about my title I am not sure if it fits my situation or not. I have been reading up on partitions recently. As I understand it you can have 4 primary partitions or instead for example 3 primary and one extended. My system is the latter. When I made the linux install I used there default install which gave me an extended partition with what I understand to be a logical one inside it. Now yesterday I took a partition backup with redo backup. It went well and backed up. It took an image and the image was 2 GB. I then decided I would go for a restore. I selected the backup from my external hard drive as the source. Then it asked me which destination drive to restore it too. Oddly it only showed the windows disk which was 420 GB approximately. I could not work out why it did not show the linux partition to which I wanted to restore it back to again. Google has not got any help at all on this unfortunately in terms of what I needed to know. From my limited computer knowledge I am assuming that since the system primary partition is extended therefore it is all effectively the same partition with ubuntu. I can then restore it back hopefully to the ubuntu logical partition contained in the extended one ? The partition including the extension is made up of 200 GB windows and 200 GB ubuntu ,swap and unallocated of ( 5 Gb each). This was created like that by the linux default install. So if redo backup wants to restore it back to the windows based system partition it will restore it back to the linux logical partition where it belongs hopefully since it is extended and part of it ? Either that or redo backup should not be used in future perhaps. Thanks all I much appreciate your answers and the help I had the other day from monkeybrain was very helpful. Hope you don't mind me showing up here again. Thanks !

---

### Post by deadflowr on 2014-02-16
Perhaps an edit to post#1 would help others understand what the problem is.
Long run-on paragraphs can be hard to follow, and what the actual problem is can get lost in the muck.

---

### Post by grahammechanical on 2014-02-16
You might find more help here

[http://sourceforge.net/p/redobackup/discussion/1169664/](http://sourceforge.net/p/redobackup/discussion/1169664/)

Regards.

---

### Post by Bashing-om on 2014-02-16
hebdave; DUHH,

+1 to deadflower's advise.

Show us what you are really working with partition wise, so all doubt is removed:
post back the output - between code tags - of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
Legacy (4 primary partitions) tutorial:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Using the above outputs as a common reference, we can advise further.

all in the 
[INDENT][INDENT]care and feeding of your ubuntu[/INDENT][/INDENT]

---

### Post by PerryTanko on 2014-02-16
you might find this youtube video useful.

v=eSMMs4cfMqY

sorry i can't post full links yet, it goes after the ? mark.

---

### Post by Vladlenin5000 on 2014-02-16
> **PerryTanko said:**
> you might find this youtube video useful.

v=eSMMs4cfMqY

sorry i can't post full links yet, it goes after the ? mark.

Very nice video. Nothing new to me but it's always a pleasure to watch Nixie.

---

### Post by deadflowr on 2014-02-16
> **PerryTanko said:**
> you might find this youtube video useful.

v=eSMMs4cfMqY

sorry i can't post full links yet, it goes after the ? mark.

[http://www.youtube.com/watch?v=eSMMs4cfMqY](http://www.youtube.com/watch?v=eSMMs4cfMqY)

---

### Post by hebdave on 2014-02-17
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xaa9693fe


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    52430847    26214400   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    52430848   514599959   231084556    7  HPFS/NTFS/exFAT
/dev/sda3       514600958   976771071   231085057    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       964648960   976771071     6061056   82  Linux swap / Solaris
/dev/sda6       514600960   952524799   218961920   83  Linux
/dev/sda7       952526848   964638719     6055936   82  Linux swap / Solaris

```[COLOR=#000000]

I may of complicated things by deleting via windows the linux partition and then re-installing linux back to that deleted partition. Apparently it overwrited and reused it though. If you don't understand what this means no problem the results are above and its most likely less relevant. Many thanks.[/COLOR]

---

### Post by mastablasta on 2014-02-17
i could be wrong (don't have the redo disk at my hand) but just as creating backup when restoring you would first choose the disk where you want to restore and then i don't know with partitions since i only restored it once so far and it was 2 partitions to a full disk. perhaps it might help if you had unalocated disk space to restore to. 

if i am not mistaking Redo is using partclone for this and is just a nice user interface to that. you might find more documentation on that program.

> [h=3]Q: Can I restore a backup to a smaller drive?[/h]A: No. Doing so likely would require modifying the bootloader, which defeats the simplicity of Redo Backup. Backups must be restored to a drive of equal or greater size.
However, you can always restore to a larger drive, resize the partition, and back up the smaller partition if needed. Partitions can easily be resized using the included partition editor utility (GParted).



you need free disk space of same or large size it seems.

---

### Post by hebdave on 2014-02-17
Hi the quote below is from soureforge Redo backup forum -

> [COLOR=#555555][FONT=sans-serif]RedoBackup does not back up and restore individual partitions. It backs up and restores the [/FONT][/COLOR]*entire*[COLOR=#555555][FONT=sans-serif] disk. If you have anything on the target disk when you restore, it will be [/FONT][/COLOR]*completely erased*[COLOR=#555555][FONT=sans-serif] before RedoBackup restores the disk.[/FONT][/COLOR][FONT=sans-serif][COLOR=#555555]If you need to back up and restore individual partitions rather than the entire disk, you can't use RedoBackup. Try [/COLOR][/FONT][CloneZilla]("http://clonezilla.org/")[FONT=sans-serif][COLOR=#555555], which is not that user-friendly but is much more flexible.[/COLOR][/FONT]

I understand from this without having read the partclone documentation that this means although you can backup a partition you can only restore that back erasing the rest of the disk. So effectively you would end up with one big partition filling the whole drive and a succesful restored ubuntu. However it may be interesting to see if that would work out that way. It may be safer to just use it for a full disk backup and restore rather than anything else ?

I have gone through over half of the ubuntu documentation on disk partitioning this morning. The way I see it is I have a choice to use redo backup for the whole disk or use  partimage which I learnt 2 days ago for one partition restore(not yet tried it out) . We need someone to create a simple program just like Redo but that restores one partition without it being semi GUI based. Partimage may be best for me currently since clonezilla is to big a jump for me to make at the moment. I'd appreciate comments on my analysis of the situation to see if I am first correct in the second paragraph. 

Thanks for all your help its very useful indeed. :smile:

---

### Post by hebdave on 2014-02-17
Hi I am currently reading clonezilla and partimage tutorial which is recommended by the Ubuntu documentation [http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html) . It is the best description of clonezilla so far. I had not understood the other blogs I read on the internet. This post is for any beginners so I thought I better put it here. Any confirmations would be handy of the above assumptions for myself and others if you could take the time - many thanks !

---

### Post by Dedoimedo on 2014-02-18
Take a look at this too, and thanks for the compliments:
[http://www.dedoimedo.com/computers/clonezilla.html](http://www.dedoimedo.com/computers/clonezilla.html)

Dedoimedo

---

### Post by mastablasta on 2014-02-18
problme wiht clonezilla iz you can't really go back to previous settings screeen. you can cancel and start it all over. otherwise it's a good program.

---

