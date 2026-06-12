---
title: "Help with External Hard Drive"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by RussW210 on 2008-11-21
Hello,

I am using Ubuntu 8.10 and just received my LaCie External Hard Drive.  It is connected and mounted properly however I have two issues.

#1 It says I only have a total capacity of 10MB.  It is a 1TB hard drive.  I just opened it and put nothing on it.  What is going on?

#2 It is formatted in FAT32.  I am primarily using it on my Linux Computer though I may be plugging it into Mac and Windows computers on occasion.  The main purpose is to store large movie files (4.3gb), music, pictures, documents, etc.  FAT32 or NTSC?

... (1) is my more pressing concern.

---

### Post by cmnorton on 2008-11-21
What is telling you there are only 10MB visible? I have a 1TB Lacie, and have never had a problem with it. Will FAT32 go up to 1TB? (This is not a trick question; I actually do not know.)

---

### Post by RussW210 on 2008-11-21
When I right click the drive then go to properties it says "Total capacity: 10.0 MB" under the Basic tab.

---

### Post by RussW210 on 2008-11-21
I can't even copy a 2gb file over... it says there isn't enough space.  Any idea?

---

### Post by drs305 on 2008-11-21
I think the 10MB may be a setup partition. If you can run it in Windows or have a manual it will probably tell you what it is for. The rest of the drive just probably hasn't been formatted yet. Look at any documentation or search their site for instructions/information.

---

### Post by taurus on 2008-11-21
Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
df -h
```

---

### Post by RussW210 on 2008-11-21
When I type "sudo fdisk -l" it says:

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24796452

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              21          22       10239    c  W95 FAT32 (LBA)
russell@russell-desktop:~$ 

I know there is the space in there somewhere.  But how do I use it?

---

### Post by adult swim on 2008-11-21
have you tried to put anything larger than 10mb on there? as an aside, you may want to rethink fat32, it doesnt play nicely with files larger than 4gb.

---

### Post by Coreigh on 2008-11-21
Do you have a different computer available to try?

I think the FAT32 size limit is related to the OS and not the filesystem architecture but I could not find confirmation on that.

When it is plugged in and turned on what is the output of
```
sudo fdisk -l
```

Does fdisk claim a different size than what you have seen, or did you get that information from fdisk already?

---

### Post by RussW210 on 2008-11-21
Here is the "df -h" output:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              38G  3.3G   33G  10% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  224K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  112K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda1              15G  195M   14G   2% /boot
/dev/sda5             455G  233G  199G  54% /home
/dev/sda7              29G  174M   27G   1% /tmp
/dev/sda8              38G  551M   36G   2% /var
/dev/sda9              14G  164M   13G   2% /var/tmp
/dev/sdb1              10M  5.7M  4.4M  57% /media/LaCie

---

### Post by RussW210 on 2008-11-21
My df -h and fdisk outputs are above.  I heard about FAT32 not working well with files larger than 4GB.  What are the cons of me reformatting to NTSC?

---

### Post by Coreigh on 2008-11-21
That shows /dev/sdb1, indicating the first partition. fdisk -l will show all partitions. If any more exist.

---

### Post by RussW210 on 2008-11-21
Here are my fdisk and df -h as I listed above:

fdisk:

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24796452

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              21          22       10239    c  W95 FAT32 (LBA)



df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              38G  3.3G   33G  10% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  220K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  116K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda1              15G  195M   14G   2% /boot
/dev/sda5             455G  233G  199G  54% /home
/dev/sda7              29G  174M   27G   1% /tmp
/dev/sda8              38G  551M   36G   2% /var
/dev/sda9              14G  164M   13G   2% /var/tmp
/dev/sdb1              10M  5.7M  4.4M  57% /media/LaCie

---

### Post by RussW210 on 2008-11-21
> **Coreigh said:**
> That shows /dev/sdb1, indicating the first partition. fdisk -l will show all partitions. If any more exist.

Sorry I am still fairly new to Ubuntu.  I guess my problem is that I have not yet created another partition for the external hard drive... is that the case?

---

### Post by Coreigh on 2008-11-21
I am a little fuzzy on blocks but I think your fdisk output (from before) shows a very small partition, it is only showing 10239 blocks. My 50GB partition is showing 49415940.

Have you tried gparted yet? System >> Administration >> Partition Editor

It is a graphical tool that will show you partitions and available space.

I should know how to do that in fdisk, but I am a little rushed.

I gotta go for the weekend, good luck.

---

### Post by RussW210 on 2008-11-21
Yes, but above that it says:

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes

So the Disk has enough space, but the device for some reason doesn't...

---

### Post by silverglade00 on 2008-11-21
Did you try to rename the drive icon in Ubuntu? I had a similar problem with a 4 gig thumbdrive that I changed the label on by right-click rename. After that, it would only see a couple MB. I changed the label back in Windows and it works fine now.

---

### Post by RussW210 on 2008-11-21
> **silverglade00 said:**
> Did you try to rename the drive icon in Ubuntu? I had a similar problem with a 4 gig thumbdrive that I changed the label on by right-click rename. After that, it would only see a couple MB. I changed the label back in Windows and it works fine now.

No, it won't let me rename the icon.  I think my issue has to do with formatting so I am going to reformat it to NTSC.

---

### Post by cmnorton on 2008-11-22
> **RussW210 said:**
> No, it won't let me rename the icon.  I think my issue has to do with formatting so I am going to reformat it to NTSC.

You mean NTSF, right?

Please remember that you can put the ext3 file system on this drive, and then let Windows clients access this drive using your Ubuntu system and running samba.

I'd search these forums for already written great instructions on formatting a drive.

---

### Post by nixscripter on 2008-11-23
I thought he meant NTFS ;-)

Anyway, I would suggest creating a new partition at the end of the drive with **gparted** (which you can install from Synaptic package manager). I am not sure whether it will let you do NTFS, but I am certain about XFS and ext3.

Also, make sure there's nothing on that DOS partition you want to save, or make a copy. Repartitioning can be dangerous.

---

