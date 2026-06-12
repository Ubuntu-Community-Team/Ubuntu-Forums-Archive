---
title: "missing hard drive."
date: 2012-07-20
forum: New to Ubuntu
---

### Post by Newuser901 on 2012-07-20
I had a harddrive that I formated for extra space. It hasn't recognized or shown it in ages. I'm trying to figure out how to get it to show.

I had some data on it because I was going to use it to store all my large data like games. How do you get it to find it again and set it up properly as a second harddrive for storage purposes only?

I beleive it still shows up in lshw or some other command. But I have no idea what to do and mounting hard drives and stuff like this is very new to me.

Thanks for any help.

---

### Post by sudodus on 2012-07-20
> **Newuser901 said:**
> I had a harddrive that I formated for extra space. It hasn't recognized or shown it in ages. I'm trying to figure out how to get it to show.

I had some data on it because I was going to use it to store all my large data like games. How do you get it to find it again and set it up properly as a second harddrive for storage purposes only?

I beleive it still shows up in lshw or some other command. But I have no idea what to do and mounting hard drives and stuff like this is very new to me.

Thanks for any help.
Please post the output of ```
sudo fdisk -lu
``` and await further help :-)

---

### Post by Newuser901 on 2012-07-20
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065a77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488396799   244197376   83  Linux

Disk /dev/sdb: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```

---

### Post by NikTh on 2012-07-20
> **Newuser901 said:**
> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065a77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488396799   244197376   83  Linux

Disk /dev/sdb: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Hi , 
it seems that your second hard drive (sdb) has a problem with partition table. 
Run this command and post back the results 
```
sudo parted -l
``` 
**Please put the results inside [CODE] tags , by highlighting the text and click # symbol on top of message pane. **
Thanks.

---

### Post by Newuser901 on 2012-07-20
```
Model: ATA ST3250310AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary  ext4         boot


Error: /dev/sdb: unrecognised disk label                                  

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
```

---

### Post by NikTh on 2012-07-20
Hi , 
you can try to fix this problem . 
2 suggestions: 

1.) 
With **Fdisk** tool. 

Open a terminal and 
```
sudo su 
fdisk /dev/sdb
```> n= create a new partition 
1 = partition number 
w= write changes to diskclick "m" for more options. 

2.)
With **e2fsck** tool. 
e2fsck tool its a check and repair tool for Linux filesystems.
Open a terminal and 
```
sudo e2fsck  -f -v /dev/sdb
```[B][COLOR=Red]
[/COLOR][/B][COLOR=Red][COLOR=Black]Post the results back here. [/COLOR]
[/COLOR][COLOR=Black]```
man e2fsck
``` for more.[/COLOR][B][COLOR=Red]

Attention:[/COLOR] Both ways pose risks to lose all your data .
[/B]
Thanks

---

### Post by Newuser901 on 2012-07-20
```
Model: ATA ST3250310AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary  ext4         boot


Model: ATA WDC WD2500JD-00F (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  250GB  250GB  extended


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label  
```

---

### Post by NikTh on 2012-07-20
Hi , 
what result is that ? from what command ? **sudo parted -l **?  
Did you try the e2fsck tool ? 
As you can see , you still have no file-system at /dev/sdb . 
Thanks

---

### Post by lrcaballero on 2012-07-20
I find GParted a much easier tool to use, try this tutorial after installing gparted:

sudo apt-get install gparted

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

good luck and cheers,

---

### Post by Newuser901 on 2012-07-21
```
 sudo parted -l
Model: ATA ST3250310AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary  ext4         boot


Model: ATA WDC WD2500JD-00F (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  250GB  250GB  extended


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label      
```

I ran the e2fsck command you gave me first but it make me hold enter down forever and seem to need me to answer thousands up on throusands of things and never stoppped. So I stopped the process and did fdisk.


I'll check out gparted.

after gparted.

```
sudo gparted
======================
libparted : 2.3
======================
aital@aital-EP35-DS3R:~$ sudo parted -l
Model: ATA ST3250310AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary  ext4         boot


Model: ATA WDC WD2500JD-00F (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  250GB  250GB  extended
 5      2097kB  250GB  250GB  logical   ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
```

Now it shows up in my home folder but i can't access it. It have the option to mount but it doesn't do anything when I click it. Is it bad there are two 250gig partitions seemingly on the same drive? It's only 250gigs to start.

---

### Post by NikTh on 2012-07-21
> **Newuser901 said:**
> I ran the e2fsck command you gave me first but it make me hold enter down forever and seem to need me to answer thousands up on throusands of things and never stoppped. **So I stopped the process and did fdisk.**

Hi , 
for future knowledge : It is dangerous to crack a command in the middle of a job. 

Ok, try gparted , but i assume that you have already lost your data. (cause e2fsck cracked). 
Will see. 

GOOD LUCK ! 

Thanks.

---

### Post by sudodus on 2012-07-21
If you have some very valuable files on that second hard drive, you might still be able to save them without a working file system. In that case try ***PhotoRec***.

It can recover the files because it recognizes the data on the disk, but it cannot recover the file names. It's a lot of work and takes long time, so PhotoRec is an option only if you really need to recover some files.

Otherwise I suggest you follow the instructions by *NikTh*. Gparted is a good and intuitive GUI tool to edit partitions and make file systems.

Good luck :-)

---

### Post by Newuser901 on 2012-07-21
It was just MMO directories. It's stuff I can redownload. If I don't remember I won't care. It's fine. I just want it working. I need to put the rest of my games on it. 8)

I'm down to 20 gigs and have games that large on my main drive. I need room fast. 8p

ON an odd side note anyone ever broken the plastic tab off an SATA HDD just above the 5 or so data metal contacts on the data connection? I had a third drive of the same size but accidently pulled the SATA cable off forgetting it had little things i had to push that secured it and broke it off. Lost a whole drive so far(blank drive) and have been curious if there is a way to get one fixed. I was thinking gorrila glue. It sadly has two power connections(SATA and Molex) but sadly only an SATA data connection. I broke the wrong connection. 8) I'm assumming the vibrations can cause problems but anyone ever heard off that problem on the off hand?

---

### Post by sudodus on 2012-07-21
I've been lucky so far with the SATA connections. By the way, I have not noticed such little things you had to push that secured it.

Finally, please let us know about your progress with partitioning and formatting file systems on that drive :-)

---

### Post by Newuser901 on 2012-07-21
yea I put this up in the last post on the first page. I thought everyone saw it. 8) I'm not sure what else to do after this. I was waiting for someone to respond to this.

> after gparted.

```
sudo gparted
======================
libparted : 2.3
======================
aital@aital-EP35-DS3R:~$ sudo parted -l
Model: ATA ST3250310AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary  ext4         boot


Model: ATA WDC WD2500JD-00F (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  250GB  250GB  extended
 5      2097kB  250GB  250GB  logical   ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
```

Now it shows up in my home folder but i can't access it. It have the option to mount but it doesn't do anything when I click it. Is it bad there are two 250gig partitions seemingly on the same drive? It's only 250gigs to start.

---

### Post by NikTh on 2012-07-22
Hi , 
it seems that e2fsck managed to fix something (?) . 

Try to mount the partition with super user privileges. 

Open a terminal and 
```
mkdir sdb 
sudo mount /dev/sdb1 sdb 
cd sdb
ls 
``` 
can you see anything ? 
Give the results here.. 

Thanks

---

### Post by Wim Sturkenboom on 2012-07-22
> **Newuser901 said:**
> ```
Model: ATA WDC WD2500JD-00F (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  250GB  250GB  extended
 5      2097kB  250GB  250GB  logical   ext4

```

...Is it bad there are two 250gig partitions seemingly on the same drive? It's only 250gigs to start.
No, not bad. The first one is an extended partition that contains logical partitions (in  your case just one).

Your partition in the system will be /dev/sdb5; so replace *sdb1* in NikTh's code to *sdb5*

---

### Post by Newuser901 on 2012-07-22
```
ls
lost+found

```

That is the output of folder sdb.

And I made the partition with gpart after I ran fdisk if that is important to anything.

---

### Post by sudodus on 2012-07-22
You seem to have mounted the partition. Probably you are also able to write and read files there now. Try with your file browser (usually Nautilus in Ubuntu).

But you can also check the permissions. First run ```
df
``` and then run ```
ls -l /media
``` (assuming you have automounted the partition to a sub-directory of /media).

---

### Post by Newuser901 on 2012-07-22
```
 df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda1      243895324 208577108  23108348  91% /
udev             4046304         4   4046300   1% /dev
tmpfs            1635232      1120   1634112   1% /run
none                5120         0      5120   0% /run/lock
none             4088076       156   4087920   1% /run/shm
/dev/sr0         3001472   3001472         0 100% /media/X3 Reunion 2.0
/dev/sdb5      243893276   3722928 227960584   2% /home/*****/sdb

```

```
ls -l /media
total 6
lrwxrwxrwx 1 root  root     7 May 26  2011 floppy -> floppy0
drwxr-xr-x 2 root  root  4096 May 26  2011 floppy0
dr-x------ 1 ***** ***** 2048 Jan 29  2009 X3 Reunion 2.0

```

I think the mounting is only temporary. If I restart the computer I have to follow the prior instructions again and mount it. When I restarted the computer last the sdb folder was empty again. And what is the unaccesable lost+found folder. The sdb folder has a lock on it as well but I can open it. Is lost+found my old files?

---

### Post by Wim Sturkenboom on 2012-07-23
The mount is indeed temporary; you need to modify /etc/fstab (root permissions required).

A line like 
```

/dev/sdb5 /pathto/whatever ext3_or_whatever_formatting_you_used defaults 0 0

```

Personally, as your data does not seem all that important to you, I would start from scratch, use fdisk to remove all partitions and create a new primary one, format the partition with mkfs and mount it. You can (obviously) also use something like gparted.

---

### Post by NikTh on 2012-07-23
> **Newuser901 said:**
> I think the mounting is only temporary. If I restart the computer I have to follow the prior instructions again and mount it. When I restarted the computer last the sdb folder was empty again. And what is the unaccesable lost+found folder. The sdb folder has a lock on it as well but I can open it. Is lost+found my old files?

Hi , 
yes the sdb folder we created earlier its a temporary mount folder. You can delete it if you want. 
```
 rm -rf sdb
```Ubuntu will mount your drive (under /media) when you tell it to do. If you open nautilus (file browser) you will see , under devices section , your new (formated) partition. Probably be referred as 250GB filesystem. When you click upon , it will be mounted. 

As for your files.. hmm i think have bad news. 
You said that used Gparted to correct the partition 
> **Newuser901 said:**
> 
**And I made the partition with gpart** after I ran fdisk if that is important to anything.
how exactly did you do that ?

For Lost+Found folder ,  you can read here -->  [http://askubuntu.com/questions/2115/whats-lostfound-and-where-did-it-come-from](http://askubuntu.com/questions/2115/whats-lostfound-and-where-did-it-come-from)
Thanks

---

### Post by sudodus on 2012-07-23
> **NikTh said:**
> Hi , 
yes the sdb folder we created earlier its a temporary mount folder. You can delete it if you want. 
```
 rm -rf sdb
```Ubuntu will mount your drive (under /media) when you tell it to do. If you open nautilus (file browser) you will see , under devices section , your new (formated) partition. Probably be referred as 250GB filesystem. When you click upon , it will be mounted. 

> And I made the partition with gpart after I ran fdisk if that is important to anything.

As for your files.. hmm i think have bad news. 
You said that used Gparted to correct the partition 

how exactly did you do that ?

For Lost+Found folder ,  you can read here -->  [http://askubuntu.com/questions/2115/whats-lostfound-and-where-did-it-come-from](http://askubuntu.com/questions/2115/whats-lostfound-and-where-did-it-come-from)
Thanks
+1
And may I add a question: there is a recovery program with the name gpart. It is not gparted. Which of these programs were you using?

---

### Post by Newuser901 on 2012-07-23
I'm not realy sure what I used. I'll just start from scratch. If I just delete the lost+found can I use it as it. It was not ext4 before. I just did that. I forget what it was before.

Ok, I used gparted to make a new table and remade the partition. I still can't get rid of the lost+found. It's still there and using 16 gigs up. How do I truly redo the drive from scratch? and have it auto mounted?

---

### Post by westie457 on 2012-07-23
To see what is inside the 'Lost and Found' folder you need to use from a terminal ```
gksudo nautilus
```
It may contain your files. If so they might even be recoverable using 'photorec'.
Also if you want to delete the folder that locked, the safest way is using the above command. BE AWARE you will be able to remove anything from your system so double-check every step of the way.

The command opens Nautilus with Root privileges.

---

### Post by Wim Sturkenboom on 2012-07-23
**repartition**
[COLOR="Red"]_*make sure that /dev/sdb is the harddisk that you want to work on*_[/COLOR]
```

sudo fdisk /dev/sdb

```

'd' will prompt for partition to remove; select '1'
'n' will prompt for a new partition to be created; select 'p' for primary and next '1' for number; use <enter> for default values
'w' will write the changes to disk

Run *sudo fdisk -l* and you should see a '/dev/sdb1'


**format** (as ext3)
```

mkfs.ext3 -c /dev/sdb1

```

**mount**
see post #21 above

---

### Post by sudodus on 2012-07-23
> **westie457 said:**
> To see what is inside the 'Lost and Found' folder you need to use from a terminal ```
gksudo nautilus
```
It may contain your files. If so they might even be recoverable using 'photorec'.
Also if you want to delete the folder that locked, the safest way is using the above command. BE AWARE you will be able to remove anything from your system so double-check every step of the way.

The command opens Nautilus with Root privileges.
Yes you can check what is inside 'Lost and Found'. Maybe you need to set Nautilus to show hidden files (menu: Show -- show hidden files). But bear in mind that the journaling system needs space, which seems to be used, but cannot be seen as files. Your partition might be OK as it is now :-)

---

### Post by Newuser901 on 2012-07-23
```
 sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065a77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   488396799   244197376   83  Linux

Disk /dev/sdb: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bf047

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   488394751   244196352   83  Linux

```

I made this earlier. How do I know which type of partition I want. Do I want a primary over and extended? Does it make a difference? Is what I have ok or is there a problem with it? If not I'll run the commands a few comments back. This is using the disk utility that came with ubuntu. I thought I wanted extended before and made one with gparted. But I'm not sure which type the regular gui disk manager did. I'm assuming this is extended since it doesn't have boot marked. I reformated the disk completely.

Does what I have look setup properly? 

How do I automount with my setup? "/dev/sdb1 /media/Games ext4 defaults 0 0" ? And do I want ext4 under type or do I want auto?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=4f4947c4-e141-410d-bc1f-9b5b2cb1806f /               ext4    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=7de96088-15a4-43a7-82e3-2f12024ac12f /               ext4    errors=remount-ro 0       1
/dev/sdb1	/media/Games	auto	default	0	0

```

gave me an error mounting on restart. I'm assuming I'm missing the UUID like for the cd rom drive. Not sure if that is the correct UUID or not. It was one of two using the blkid command. The other was the cdrom.

---

### Post by sudodus on 2012-07-23
> **Newuser901 said:**
> ```
 ...
I made this earlier. How do I know which type of partition I want. Do I want a primary over and extended? Does it make a difference?
> 
Windows wants to boot from a primary partition, but Linux works well with logical partitions inside an extended partition. I don't think it is a problem, as long as you are only using Linux. You need to install a program in order to read a linux file system (ext2, ext3 or ext4) from Windows.

You have only one partition now, /dev/sdb1, on the second drive, and it it a primary partition with a linux file system.

Is what I have ok or is there a problem with it? If not I'll run the commands a few comments back. This is using the disk utility that came with ubuntu. I thought I wanted extended before and made one with gparted. But I'm not sure which type the regular gui disk manager did. I'm assuming this is extended since it doesn't have boot marked. I reformated the disk completely.

Does what I have look setup properly? 

How do I automount with my setup? "/dev/sdb1 /media/Games ext4 defaults 0 0" ? And do I want ext4 under type or do I want auto?

[COLOR="Red"]I suggest that you mount it using UUID instead of the device name, because it will identify the drive better. Run [CODE]sudo blkid
``` to find the device id, and use it (without quotes).
[/COLOR]
I mount a data partition on my computer like this (edit your [FONT="Courier New"][SIZE="3"]/etc/fstab[/SIZE][/FONT] file)
```
# /dev/sdb1
UUID=[COLOR="Red"]b1f3f4a3-3d5c-4e4f-8e1a-c2f0de792b82[/COLOR] /mnt/Games  ext4  defaults  0  2
```

and create a subdirectory of /mnt (leave /media for automounting)
```
sudo mkdir /mnt/Games
```

After reboot your drive should mount properly. Check with ```
df
``` and/or your file browser :-)

---

### Post by Newuser901 on 2012-07-23
```
df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda1      243895324 181728152  49957304  79% /
udev             4046304         8   4046296   1% /dev
tmpfs            1635232      1052   1634180   1% /run
none                5120         0      5120   0% /run/lock
none             4088076       152   4087924   1% /run/shm
/dev/sdb1      243894300   3722956 227961528   2% /mnt/Games
/dev/sr0         3001472   3001472         0 100% /media/X3 Reunion 2.0

```

And it appears to be working. 8) Thanks!

---

