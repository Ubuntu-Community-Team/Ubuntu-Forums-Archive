---
title: "Asus eeepc 900"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by spark001uk on 2014-05-11
Hi, just joined here,
I'm about to give ubuntu a try. I have an old asus eeepc 900 (with 4GB system ssd and 8GB ssd for storage). Now, I've trawled online and there's so much conflicting info that I thought I'd be better placed asking the community here!
So far all I can glean is that standard ubuntu may be a bit heavy on this old eeepc, both on speed and space, and that I may be better off with xubuntu or even Lubuntu, is that correct? I'm looking at installing the latest, 14.04 I gather?
Currently I have xp installed on the 4GB, and the 8GB for storage. If I could get some brief instructions that would be great? My installation medium I have ready is a 4GB sd card (currently has standard 14.04 iso on it).

Many thanks

---

### Post by sudodus on 2014-05-11
Welcome to the Ubuntu Forums :-)

I would recommend Lubuntu 13.10 or 14.04, 32-bit desktop iso files for your eeepc 900. The version 13.10 is better debugged now, but has end of life late in July this year. By that time 14.04 LTS should be better debugged and polished, so you can upgrade. But try both versions now, try live without installing, and if you are happy with 14.04 LTS, install it now.

You can install it into 4 GB, or maybe even better, use

- the 4 GB drive for the root partition /
- the 8 GB drive for the home partition /home and a small swap partition (maybe 512 MB), unless you want to hibernate. Then the swap must be as big as the RAM (in gibibytes). 1 gibibyte RAM needs 1.1 GB swap.

Avoid swapping as it will wear the flash memory: this means that you should ***not*** have many programs or tabs open at the same time.

Use the options noatime and discard in /etc/fstab for the file system partitions.

See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by fatriff on 2014-05-11
Hardly any point in advising installing 13.10 since support for it ends in 2 months. You should go for 14.04 if you can.. If you want something lightweight which is Ubuntu based try LinuxLite or Bodhi Linux or Peppermint OS. I have used Peppermint on a couple of netbooks and it is zippy.

---

### Post by spark001uk on 2014-05-11
> **sudodus said:**
> 
- the 4 GB drive for the root partition /
- the 8 GB drive for the home partition /home and a small swap partition (maybe 512 MB), unless you want to hibernate. Then the swap must be as big as the RAM (in gibibytes). 1 gibibyte RAM needs 1.1 GB swap.


I did try this, but when I selected the 8GB for /home , it said I can't have a partition outside the disk?

---

### Post by sudodus on 2014-05-11
Is the 8 GB recognized as an own drive (or device)? Did you format it to ext4? Is there some traces from some kind of RAID setup?

Maybe you can use ***gparted*** (when running a live session from the install disk) to edit the partitions (remove the old ones and create new and good partitions.

Please post the output of these terminal commands (when running a live session from the install disk). Press the red 'Go Advanced' button, copy and paste the output, mark it in the editing window and click on the **#** icon above the editing window to put the text within code tags.

```
sudo parted -l
```
```
sudo blkid
```
```
df
```

---

### Post by spark001uk on 2014-05-11
> **sudodus said:**
> Is the 8 GB recognized as an own drive (or device)? Did you format it to ext4? Is there some traces from some kind of RAID setup?

Maybe you can use ***gparted*** (when running a live session from the install disk) to edit the partitions (remove the old ones and create new and good partitions.

Please post the output of these terminal commands (when running a live session from the install disk). Press the red 'Go Advanced' button, copy and paste the output, mark it in the editing window and click on the **#** icon above the editing window to put the text within code tags.

```
sudo parted -l

Model: ATA ASUS-PHISON OB S (scsi)
Disk /dev/sda: 4035MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4022MB  4022MB  primary  ntfs         boot


Model: ATA ASUS-PHISON SSD (scsi)
Disk /dev/sdb: 8070MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8061MB  8061MB  primary  ntfs


Model: USB2.0 CardReader SD0 (scsi)
Disk /dev/sdc: 3942MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 4      131kB  3942MB  3941MB  primary  fat32        boot


```
```
sudo blkid

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="54C4AB32C4AB14F0" TYPE="ntfs" 
/dev/sdb1: UUID="5E54ECC854ECA3CD" TYPE="ntfs" 
/dev/sdc4: LABEL="Ubuntu 14.0" UUID="B4FE-5315" TYPE="vfat" 


```
```
df

Filesystem     1K-blocks   Used Available Use% Mounted on
/cow              508728  66924    441804  14% /
udev              498432      8    498424   1% /dev
tmpfs             101748   1072    100676   2% /run
/dev/sdc4        3841280 992324   2848956  26% /cdrom
/dev/loop0        957696 957696         0 100% /rofs
none                   4      0         4   0% /sys/fs/cgroup
tmpfs             508728     12    508716   1% /tmp
none                5120      4      5116   1% /run/lock
none              508728     76    508652   1% /run/shm
none              102400     76    102324   1% /run/user


```

ADD: I must say, so far I like the feel of regular ubuntu. (used it to give the above). Seen a few pictures of lubuntu and it visually resembles windows a bit much for my liking!? Wanted to get away from that if possible. Could I not do a "minimal cd" install of ubuntu?

---

### Post by stalkingwolf on 2014-05-11
Yes you should be able to do a minimal install.  I have a 1005 and 2 hp mini 110's all with mint 13 installed albeit to 160gb hdd's that run fine. I cant comment on 14.04 I just installed a copy yesterday to test.

---

### Post by sudodus on 2014-05-11
> **spark001uk said:**
> ```
sudo parted -l

Model: ATA ASUS-PHISON OB S (scsi)
Disk /dev/sda: 4035MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4022MB  4022MB  primary  [COLOR=#ff0000]ntfs[/COLOR]         boot


Model: ATA ASUS-PHISON SSD (scsi)
Disk /dev/sdb: 8070MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8061MB  8061MB  primary  [COLOR=#ff0000]ntfs[/COLOR]


Model: USB2.0 CardReader SD0 (scsi)
Disk /dev/sdc: 3942MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 4      131kB  3942MB  3941MB  primary  fat32        boot


```
```
sudo blkid

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="54C4AB32C4AB14F0" TYPE="ntfs" 
/dev/sdb1: UUID="5E54ECC854ECA3CD" TYPE="ntfs" 
/dev/sdc4: LABEL="Ubuntu 14.0" UUID="B4FE-5315" TYPE="vfat" 


```
```
df

Filesystem     1K-blocks   Used Available Use% Mounted on
/cow              508728  66924    441804  14% /
udev              498432      8    498424   1% /dev
tmpfs             101748   1072    100676   2% /run
/dev/sdc4        3841280 992324   2848956  26% /cdrom
/dev/loop0        957696 957696         0 100% /rofs
none                   4      0         4   0% /sys/fs/cgroup
tmpfs             508728     12    508716   1% /tmp
none                5120      4      5116   1% /run/lock
none              508728     76    508652   1% /run/shm
none              102400     76    102324   1% /run/user


```

ADD: I must say, so far I like the feel of regular ubuntu. (used it to give the above). Seen a few pictures of lubuntu and it visually resembles windows a bit much for my liking!? Wanted to get away from that if possible.
 
1. You must change the file systems of **/dev/sda1** and  **/dev/sdb1** to ***ext4***. Do that with ***gparted***. Then I think it will work better to install. Use 'Something else' at the partitioning window of the installer.

2. How much RAM is there? 1f 1 GB or less I would recommend Lubuntu (ultra light-weight) or Xubuntu (medium light-weight), but if you really want, it is possible to install Ubuntu, but I think you should have 2 GB RAM for it to run smoothly.

3. Also, Xubuntu and standard Ubuntu need more flash space for the bigger application programs (compared to Lubuntu).

*. There is also the alternative to install the whole system to the 8 GB drive (and not have a separate /home partition. If you are good at moving data files (documents, pictures, music files etc) to other drives (the 4 GB internal drive and plugged in USB pendrives), it might be a good alternative with Ubuntu.

---

### Post by spark001uk on 2014-05-11
Just out of interest how does the standard "replace windows with ubuntu" option deal with changing the partition to ext4? Is gparted only required when partitioning two drives?
RAM is 512MB by the way.

---

### Post by deadflowr on 2014-05-11
> **spark001uk said:**
> Just out of interest how does the standard "replace windows with ubuntu" option deal with changing the partition to ext4? Is gparted only required when partitioning two drives?
RAM is 512MB by the way.

First it wipes the existing partition table, then it create a new one.
But with the disk sizes you have, follow the advice by Sudodus and use the "something else" option.
Your drives are so small, I wouldn't be surprised if something came up about it if you tried to use the replace option.

---

### Post by sudodus on 2014-05-11
> **deadflowr said:**
> First it wipes the existing partition table, then it create a new one.
But with the disk sizes you have, follow the advice by Sudodus and use the "something else" option.
Your drives are so small, I wouldn't be surprised if something came up about it if you tried to use the replace option.
+1

And with only 512 MB RAM, I recommend ***Lubuntu***. Both Xubuntu and standard Ubuntu need more RAM to work well.

If you have problems with 13.10 and 14.04 LTS (for example some hardware driver), you have the alternative to try a light-weight respin of Ubuntu 12.04 LTS,

***Bento, Bodhi*** or ***LXLE***.

---

### Post by spark001uk on 2014-05-11
Trying lubuntu 14.04, selected try without installing, and it appears to have hung, with a bunch of text on the screen. At the top of which it says something about kernel panic - not syncing vfs, unable to mount root fs on unknown block 0,0
?

ADD: Does same thing when I try to install it.

---

### Post by sudodus on 2014-05-11
Did you download the 32-bit or 64-bit system? I think 32-bits is better in this case.

Did you check that the download was good with md5sum? See this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Which tool did you use to create the USB boot drive? Maybe you should try another tool. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There might be problems with a hardware driver. In that case it would be better with an older version, Lubuntu 13.10 or try a light-weight respin of Ubuntu 12.04 LTS, ***Bento, Bodhi*** or ***LXLE***.

See also this link with more tips

[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by spark001uk on 2014-05-11
I used ultraiso. Ive just tried it with unetbootin and thats even worse, nothing happens at all, just black screen with a cursor.

---

### Post by sudodus on 2014-05-11
If you create a new FAT32 partition and then use Unetbootin, I think it should work. Are you trying to create the USB pendrive in linux or Windows?

---

### Post by sudodus on 2014-05-11
If you create the USB pendrive in Lubuntu or Ubuntu, you can also use ***Startup Disk Creator***. If still no go, try ***mkusb***. See

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

Try with various [boot options]("https://help.ubuntu.com/community/BootOptions"), for example those suggested at F6 in the installer:

acpi=off
noapic
nolapic
edd=on
nodmraid
nomodeset

These can also be used with Unetbootin.

---

### Post by spark001uk on 2014-05-11
Ok getting there slowly. I reformatted fat32 once again, with a slow format, and stuck lubuntu back on it using unetbootin and still didnt work, but ultraiso did.
Next hurdle - ran it live without install to check everything working, and theres no wifi - no setting, no icon, nothing. However wifi worked flawlessly out of the box on ubuntu and xubuntu! Am I missing something?

---

### Post by sudodus on 2014-05-12
Yes, there is a bug, so that ***nm-applet*** is not started (and not shown on the panel).

Start nm-applet 'right now'

```
nm-applet &
```

Make Lubuntu start nm-applet after reboot (when installed or in a persistent live system)

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

---

### Post by spark001uk on 2014-05-12
> **sudodus said:**
> Yes, there is a bug, so that ***nm-applet*** is not started (and not shown on the panel).

Start nm-applet 'right now'

```
nm-applet &
```

Make Lubuntu start nm-applet after reboot (when installed or in a persistent live system)

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

On a live session, typed the above in terminal and I get:

```

nm-applet: error while loading shared libraries: /usr/lib/i386-linux-gnu/libmm-glib.so.0: cannot read file data: Input/output error

```

---

### Post by spark001uk on 2014-05-12
Also on a brighter note - lifted the trap door just now to check the ssd etc out, and noticed I've actually got 1gb of ram, twice as much as I thought I had!

---

### Post by sudodus on 2014-05-12
Are you talking about running ```
nm-applet &
``` in a terminal window during a live session?

It works for me, I just tested it in a live session with 'Lubuntu 14.04 LTS desktop 32-bits'. Does your computer need a proprietary driver for the wifi (for example broadcom)? In that case see this link

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

Or is it an installed system with some package missing?

---

### Post by sudodus on 2014-05-12
> **spark001uk said:**
> Also on a brighter note - lifted the trap door just now to check the ssd etc out, and noticed I've actually got 1gb of ram, twice as much as I thought I had!

This is good :-)

Check that is is really being recognized and used with the following command

```
free -m
```

With 1 GB RAM, you should be able to run ***Xubuntu*** too, which might work better for you.

---

### Post by spark001uk on 2014-05-12
Definitely 14.04 desktop 32 bit yes. What I might do then in light of discovering the gig of ram is see how xubuntu runs (I already know the wifi works on that), and see if I can shoe horn it onto the 4gb via a minimal, knock a few apps off or something? Then if that doesn't play nice I'll go back down the lubuntu road.

---

### Post by sudodus on 2014-05-12
I think shoehorning Xubuntu into 4 GB might be a short-term solution. I think it fits better in the 8 GB drive.

Reinstalling is rather fast anyway, if you want to go back to Lubuntu.

---

### Post by trag on 2014-05-12
You might try a distro built for eepc's ,check this one out [http://www.leeenux-linux.com/](http://www.leeenux-linux.com/)
good luck
trag

---

### Post by spark001uk on 2014-05-12
I've got the minimal xubuntu burnt to my boot device (a 1gb sd card in this case), and I''m ready to try installing. I have found two howto's on fitting it onto the 4gb ssd, which one do you think I would be best off following, and are there any issues I need to watch out for? The reason I'm reluctant to try it on the 8gb ssd by the way is I've heard it's considerably slower than the (motherboard fitted?) 4gb one apparently?

[http://askubuntu.com/questions/165798/installing-xubuntu-on-a-4-gb-storage-device-eee-pc-701](http://askubuntu.com/questions/165798/installing-xubuntu-on-a-4-gb-storage-device-eee-pc-701)

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Or: as I'm not too au-fait with manual install, would I be better off doing a full install as you suggested before, something about having /home install to the other ssd?

---

### Post by sudodus on 2014-05-12
I think both descriptions are helpful, and both are dated 2012. Read both links.

If you intend to install from Ubuntu 12.04 LTS mini.iso, you should know that it wants to be installed from CD/DVD. I don't think it works from a USB pendrive. I hope and think it works from a USB CD/DVD drive, but I have no own experience of it.

The newer versions 13.10 and 14.04 LTS work also from USB pendrives. I have done it, so I know.

-o-

You may manage to install Xubuntu into 4 GB, but if you want to install some new program packages, you will hit the ceiling pretty soon. Why do you want to install to the 4 GB drive instead of the 8 GB drive? Is the 4 GB drive faster or better in some other way?

---

### Post by spark001uk on 2014-05-12
> **sudodus said:**
> 
You may manage to install Xubuntu into 4 GB, but if you want to install some new program packages, you will hit the ceiling pretty soon. Why do you want to install to the 4 GB drive instead of the 8 GB drive? Is the 4 GB drive faster or better in some other way?

I should say so yes.
See here:

[http://www.jkkmobile.com/2008/07/asus-eee-pc-ssd-read-and-write-tests.html](http://www.jkkmobile.com/2008/07/asus-eee-pc-ssd-read-and-write-tests.html)

---

### Post by sudodus on 2014-05-12
I see. You know what you are doing :-)

If you get problems because of the limited size of the root partition, I suggest that you should look for smaller operating systems, Lubuntu or some other ultra light-weight distro.

Or you can make a persistent live system instead of a regular install. Then 4 GB is plenty also for Xubuntu, because a lot of program packages are stored in a compressed archive, and are extracted to RAM. It will work like your USB install drive, but faster (due to the faster connection and faster flash memory).

Another alternative is Knoppix, which is made for running live or persistent live "poor man's install" in Knoppix terminology.

---

### Post by spark001uk on 2014-05-12
Ok. Is there some way I could use both ssd's? For example putting /home (and possibly /tmp) onto the 2nd slower ssd? Would that work?
Again, just going by what I've read here and there.

---

### Post by sudodus on 2014-05-12
Yes, see post #2 in this thread.

You can certainly have /tmp and swap there too. (Of course swapping will be slower, but I suggest that you should avoid swapping anyway.)

Remember that both the root and home partitions need an ext file system (not NTFS) according to post #8.

---

### Post by spark001uk on 2014-05-12
> **sudodus said:**
> Yes, see post #2 in this thread.

You can certainly have /tmp and swap there too. (Of course swapping will be slower, but I suggest that you should avoid swapping anyway.)

Remember that both the root and home partitions need an ext file system (not NTFS) according to post #8.

Ok many thanks for the pointers. I'm guessing from the error I encountered before, that I need to boot into a live session and partition/format the two ssd's first? Could you advise me on how to do this if you wouldn't mind?

---

### Post by sudodus on 2014-05-12
Use ***gparted***. It comes with the Ubuntu family installers, and is rather intuitive and easy to use, easier than to do the same thing with the installer.

After that, when you run the installer, select 'Something else' at the partitioning page and set the installer to use the partitions that you made with gparted.

I will leave now. It is bed time for the children ...

---

### Post by spark001uk on 2014-05-12
Ok yes I think I saw that on the ubuntu live (its not on xubuntu live). What type of partitions do I need and how many/ what size?

---

### Post by slooksterpsv on 2014-05-12
You can do it with just 1 partition, or you can make 3. 
/ - for where your files will be stored for the OS
/home - where your personal files and settings will be stored
swap - think of it like RAM thats on the disk.

Put /home on the bigger disk. Put / on the disk you're going to use for your OS, and put swap as like a 1024MB partition on the largest drive you have. I'd suggest trying to get bigger storage for your computer or, as much as I hate to say it, a lighter distro.

---

### Post by Impavidus on 2014-05-12
If you can't squeeze the full install (except /home and swap) on the 4GB drive, you can also move part of what is normally on the root partition to a separate partition on the larger drive. For example, on my install the root partition has 7.7GB, with 4.8GB of that in the /usr/share directory. In principle this directory could be moved to a separate partition on the bigger drive, although it's some guess work to decide which directory can be moved best. I didn't move that one, but I did move /usr/local to a separate partition. By default it's empty, but I store a lot of program data there.

---

### Post by spark001uk on 2014-05-12
Ok, well I'm about to go to bed now, so far I've done the following in gparted, and left it at that until tomorrow. I saw it as a good point to stop, and also to allow time for anyone to see if I'd done it right or not! ;)
(ignore the card reader, that's my live disk)

```

ubuntu@ubuntu:~$ sudo parted -l

Model: ATA ASUS-PHISON OB S (scsi)
Disk /dev/sda: 4035MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4034MB  4033MB  primary  ext4


Model: ATA ASUS-PHISON SSD (scsi)
Disk /dev/sdb: 8070MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8069MB  8068MB  primary  ext4


Model: USB2.0 CardReader SD0 (scsi)
Disk /dev/sdc: 3942MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 4      131kB  3942MB  3941MB  primary  fat32        boot

```

---

### Post by sudodus on 2014-05-13
Disk /dev/sda: 4035MB is OK for the root partition '/'

Disk /dev/sdb: 8070MB has only one partition.

It needs
- one partition for '/home' with ext4 file system and
- one swap partition (1.1 GB if you want to hibernate, otherwise 512 MB should be enough)

Use gparted to make a swap partition. Maybe it is easier to remove the ext4 partition and start from the beginning, but you can also shrink the ext4 partition to create space for the swap.

---

### Post by spark001uk on 2014-05-13
Ah ok will do. So, partition of 1024mb for the swap, and the other partition to fill the rest of space then. Do I put the small partition at the beginning or the end of the space? And both ext4 primary?

(I think I was going by the Ubuntu help pages for ssd installs, advising not to create a swap partition due to heavy writing)

---

### Post by sudodus on 2014-05-13
Yes, I know. But the system might break easily due to lack of RAM, if you have no swap. I suggest that you have swap, but run the computer, so that it will be needed only in rare cases. When you notice swapping, close tabs, windows, applications, that are not necessary. It is a good idea to monitor the swapping with a monitoring tool (unless you notice it directly because the computer gets slow).

Hibernation will also wear the SSD flash memory of the swap space. So avoid hibernation, and have only a small swap partition, maybe 512 MB.

Use the mount options ***noatime*** and ***discard*** in the file **[FONT=courier new]/etc/fstab[/FONT]** for the root and home partitions. It will increase the expected life of the SSD flash memory.

---

### Post by spark001uk on 2014-05-13
OK, will deal with the mount options when I get to that stage. Right now I have gparted open, on the 8gb ssd, and have removed partition. So, this little 512mb partition I'm making, do I put it on the left hand side and storage space to the right? Or vice versa?

---

### Post by sudodus on 2014-05-13
It might make a difference in a HDD, but it does not matter at all in an SSD. Put it where you want it :-)

A friend of order might want to have the partititions in order (lower partition numbers to the left, but it is not important).

---

### Post by spark001uk on 2014-05-13
OK thanks.and these are all primary, and ext4 is that right?

---

### Post by sudodus on 2014-05-13
You can have max four primary partitions. If you need more partitions, have max three primary partitions and one extended partition. And the rest of the partitions can be created as logical partitions inside the extended partition. In this case it is OK with two primary partitions. The ***home*** partition should have an ***ext4*** file system. The swap partition should be created as ***linux-swap***, and should have no file system.

---

### Post by spark001uk on 2014-05-13
OK, done. I notice there's a yellow bit at the beginning of both drives now, I assume that's reserved for the filing system?

---

### Post by sudodus on 2014-05-13
Is it 1 MB unallocated before the partitions start? It is space that can be used by grub.

---

### Post by spark001uk on 2014-05-13
The 1mb each end was there before partitioning yes. And now I've partitioned both drives there is a yellow bit inside each partition, I think it said in the listing something like 130mb used on the 4gb and 260ish on the 8gb. Assume that's something to do with ext4?

---

### Post by sudodus on 2014-05-13
Now I see what you mean :-) That yellow part shows how much is used or otherwise not available. There is journaling and other overhead, which occupies some space even before there are files in the file system.

---

### Post by spark001uk on 2014-05-13
Ok, I am now writing this on a successful full install of xubuntu 14.04! :)
Was all fairly painless, quite nippy, can't say I notice it being slow. Certainly running a lot better than xp did on it!

---

### Post by spark001uk on 2014-05-13
Getting a strange bunch of messages come up though. Still boots ok, just comes up with this lot during boot. Obviously I couldn't copy it, so I'll type it from a pic I took. 

9.926499) sd 2:0:0:0: (sdc) No caching mode page found
9.927015) sd 2:0:0:0: (sdc) Assuming drive cache: write through
9.977138) sd 2:0:0:0: (sdc) No caching mode page found
9.977653) sd 2:0:0:0: (sdc) Assuming drive cache: write through
9.986576) sd 2:0:0:0: (sdc) No caching mode page found
9.927015) sd 2:0:0:0: (sdc) Assuming drive cache: write through
10.106994) (drm:i915_stolen_to_physical) *ERROR* conflict detected with stolen region: (0x3f800000 - 0x40000000)

ADD: OK the (sdc) entries don't show up now I've taken the live-install sd out obviously, but the stolen to physical error still occurs.

---

### Post by Ripp_Steakface on 2014-05-13
> **spark001uk said:**
> Ok, I am now writing this on a successful full install of xubuntu 14.04! :)
Was all fairly painless, quite nippy, can't say I notice it being slow. Certainly running a lot better than xp did on it!

I'm pretty new here myself and I too just got Xubuntu 14.04 running on my Asus EeePC 900HA (1.6GHz, 140GB HDD, 1GB RAM). Pretty simple little netbook, but Xubuntu runs better than XP EVER did. I even have Conky (system resource viewer/monitor) running on the side of my screen, fits well into the 1024x600 resolution. The only real issue I've had with it is getting the computer to recover from sleep/hibernate. The screen goes black after typing the password, and I'm sure it has something to do with the video drivers, but until I get more familiar with the system, I just disabled it. I'm super happy with how things are going otherwise.

---

### Post by spark001uk on 2014-05-13
Yep same here, this is only a celeron 900mhz with 4gb & 8gb ssd. Xubuntu is way nippier, very impressed so far. Win xp on this ran like a dog!

---

### Post by Ripp_Steakface on 2014-05-13
> **spark001uk said:**
> Yep same here, this is only a celeron 900mhz with 4gb & 8gb ssd. Xubuntu is way nippier, very impressed so far. Win xp on this ran like a dog!

Have you tried using Conky yet?

Another thing I've noticed is the system is under far, FAR less strain that with XP running on it. The system stays cool while doing general things like surfing the web and screwing around on the desktop. I'm considering trying to run Xubuntu on my old PowerBook G4 if the PowerPC CPU won't be an issue because it's a 17" laptop and this netbook is less than 10"!

---

### Post by sudodus on 2014-05-14
[ 						 					]("http://ubuntuforums.org/member.php?u=820492") 				 				 					 						 	*[COLOR=#000000]@Ripp_Steakface[/COLOR]*



You might have better luck with Lubuntu, which has an iso file for Power PC. But it may need some tweaking. I suggest that you start an own thread in order to get help to install and tweak Lubuntu for your Power PC.

---

### Post by sudodus on 2014-05-14
> **spark001uk said:**
> Getting a strange bunch of messages come up though. Still boots ok, just comes up with this lot during boot. Obviously I couldn't copy it, so I'll type it from a pic I took. 

9.926499) sd 2:0:0:0: (sdc) No caching mode page found
9.927015) sd 2:0:0:0: (sdc) Assuming drive cache: write through
9.977138) sd 2:0:0:0: (sdc) No caching mode page found
9.977653) sd 2:0:0:0: (sdc) Assuming drive cache: write through
9.986576) sd 2:0:0:0: (sdc) No caching mode page found
9.927015) sd 2:0:0:0: (sdc) Assuming drive cache: write through
10.106994) (drm:i915_stolen_to_physical) *ERROR* conflict detected with stolen region: (0x3f800000 - 0x40000000)

ADD: OK the (sdc) entries don't show up now I've taken the live-install sd out obviously, but the stolen to physical error still occurs.

I don't know about this error. Let us hope someone who knows will read your thread and help you.

---

### Post by spark001uk on 2014-05-14
> **sudodus said:**
> I don't know about this error. Let us hope someone who knows will read your thread and help you.

That's ok, from what I can gather it's not serious, and in any case I booted up just now and no errors appeared this time.
Anyway I'd like to thank you for the assistance you've given me to get me this far, it's much appreciated, you've been very helpful.

:)

---

### Post by sudodus on 2014-05-14
You are welcome and good luck running Xubuntu in your eeePC :-)

---

### Post by spark001uk on 2014-05-14
Oh I forgot, you said something about I need a couple of commands in the system to limit the ssd writes? How do I go about that and what do I need to enter?

---

### Post by sudodus on 2014-05-15
It can look something like this: [COLOR=#0000ff]discard,noatime[/COLOR] highlighted in the line for the root partition in the file **/etc/fstab**

```
# /dev/sdx1 root file system
UUID=bdc8b3a7-46af-43bd-91fc-130c23ef9887 /               ext4    defaults,[COLOR=#0000ff]discard,noatime,[/COLOR]errors=remount-ro 0       1
```

and something corresponding for the home partition. You must use ***your*** UUIDs, mine is only an example.

---

### Post by spark001uk on 2014-05-15
OK, I have 3 entries on mine, where should I make the changes? Sorry to be dumb but don't want to mess it up! :)

```
# / was on /dev/sda1 during installation
UUID=f073847f-1158-4d81-a36b-8d51965d259e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=f2d4c261-4dc5-4e93289dd-79c634c65723 /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=6c3e2acc-01cc-4edc-a92a-002c7236cf46 none            swap    sw              0       0
```

---

### Post by sudodus on 2014-05-15
> **spark001uk said:**
> OK, I have 3 entries on mine, where should I make the changes? Sorry to be dumb but don't want to mess it up! :)

```
# / was on /dev/sda1 during installation
UUID=f073847f-1158-4d81-a36b-8d51965d259e /               ext4    defaults,[COLOR=#0000ff]discard,noatime,[/COLOR]errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=f2d4c261-4dc5-4e93289dd-79c634c65723 /home           ext4    defaults[COLOR=#0000ff],[/COLOR][COLOR=#0000ff]discard,noatime[/COLOR]        0       2
# swap was on /dev/sdb2 during installation
UUID=6c3e2acc-01cc-4edc-a92a-002c7236cf46 none            swap    sw              0       0
```


These options are most important for the root partition, but also important for the home partition.

They are not relevant for the swap partition, and as I mentioned earlier, avoid swapping to a flash or SSD device. It should be only for rare cases.

---

### Post by spark001uk on 2014-05-15
> **sudodus said:**
> These options are most important for the root partition, but also important for the home partition.

They are not relevant for the swap partition, and as I mentioned earlier, avoid swapping to a flash or SSD device. It should be only for rare cases.

I see you've added the word "defaults" to the first entry, do I need to add that also? It's not currently there on the / entry, but it is there on the /home entry

---

### Post by sudodus on 2014-05-16
I have it, probably it is not necessary. But if you have it, have the other options afterwards (like I showed in post #61).

---

