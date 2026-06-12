---
title: "cannot mount external USB drive after ddrescue"
date: 2015-04-23
forum: New to Ubuntu
---

### Post by hpsauce on 2015-04-23
Hello,

I am new to Ubuntu, I installed Ubuntu Gnome recently as part of a dual boot OS, specifically to use the ddrescue command to try and clone an existing external USB drive that started failing under windows.

I ran ddrescue -n, from the failing HDD to my new 2TB external HDD, with a logfile, then I ran ddrescue -r3, to try and recover as much as possible.

Once it was complete, I tried mounting the new 2TB HDD, but that didn't give me any results. I was reading that trying sudo fsck -v -f /dev/sdb would help to check the disk. I tried that, and I think I might have end up changing the partitions filesystems from ntfs to sun...ooops

Now when I run sudo fdisk -l, I get the following:

Disk /dev/sdd: 1.8 TiB, 2000365289472 bytes, 3906963456 sectors
Geometry: 255 heads, 63 sectors/track, 46589 cylinders
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: sun

Device          Start        End    Sectors  Size Id Type         Flags
/dev/sdd1           0 3906863414 3906863415  1.8T 83 Linux native      
/dev/sdd2  3906863415 3906959804      96390 47.1M 82 Linux swap      u 
/dev/sdd3           0 3906959804 3906959805  1.8T  5 Whole disk        

Partition table entries are not in disk order.

If I run sudi blkid, I get the following:

/dev/sda1: LABEL="2T backup" UUID="1C6E011C6E00EFF6" TYPE="ntfs" PARTUUID="000245eb-01" 
/dev/sdb1: LABEL="320gig Data" UUID="3CD6F902D6F8BCE8" TYPE="ntfs" PARTUUID="00000001-01" 
/dev/sdc1: UUID="AE8E23B58E23754D" TYPE="ntfs" PARTUUID="1b3d229e-01" 
/dev/sdc5: UUID="a7161264-7ea2-405a-b8dc-c12650759551" TYPE="swap" PARTUUID="1b3d229e-05" 
/dev/sdc6: UUID="3952278c-00b9-43d9-976e-4925d6df960b" TYPE="ext4" PARTUUID="1b3d229e-06" 
/dev/sdd1: PTTYPE="sun" 
/dev/sdd3: PTTYPE="sun" 

/dev/sdd is the HDD I am interested in, it contains the recovered data; however I have no clue how to access it.
I have plugged the drive in under windows, but file manager does not recognise it and disk manager asks me to initialise disk before it can be used, which I am reluctant to do as I will most likely lose my data.

Can anybody provide me with some help or advise please?

Cheers,
hp.

---

### Post by yancek on 2015-04-23
Did you create a filesystem on the external before copying anything to it, ntfs for windows?
Running a Linux filesystem check as you did isn't going to work on a windows filesystem and you would need some windows tool to do that.  I don't know where you got your advice to use fsck from Linux but mark that as a bad source.  I'm not familiar with Solaris so I'm not sure if windows not recognizing it is a problem.  You do know that a windows system doesn't recognize any Linux filesystem and you would likely see the same with a working Linux from windows.  You said you had a dual-boot so boot Ubuntu and take a look at the disk from there and see if you can see anything.

---

### Post by hpsauce on 2015-04-23
My new drive was formatted ntsf before I started the process...I am in Ubuntu but I just cannot seem to access any info on my new drive. I can see the drive when I run sudo fdisk -l, but cannot mount any of the 3 partitions that are present on the drive.
One of the things that fdisk tells me is: the Partition table entries are not in disk order...is there anything I can do to fix this, and then I might be able to access the data that is on the drive?
Otherwise I might just re-format my new drive, re-plug my old hdd in and start the whole ddrescue exercise again hoping that I can still rescue some data off my old drive...

---

### Post by matt_symes on 2015-04-23
Hi

Please post the exact ddrescue command that you ran.

Kind regards

---

### Post by hpsauce on 2015-04-24
Hi Matt,

I did:
sudo ddrescue -n -f /dev/sdc /dev/sdb extrescue.log,
Once that what completed I did:
sudo ddrescue -d -r3 /dev/sdc /dev/sdb extrescue.log

then I tried mounting the disk,
sudo mount -t ext2 -o ro /dev/sdb /mnt
 and that gave me an error (I can&#8217;t remember what it was...)

Then I tried 
sudo fsck -v -f /dev/sdb
(because  I was reading on a forum that after a ddrescue this would check the  disk, recover the data and save it  ([http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html](http://www.cyberciti.biz/tips/how-do-i-save-recover-data-from-crashed-disks-with-dd-and-ddrescue-command.html)))

Then somehow I think I end up changing the partitions to SUN partitions...now I am stuck and not too sure what to do...

Thanks,
hp

---

### Post by matt_symes on 2015-04-24
Hi

The ddrescue commands look alright although i would need to double check the order to be 100% sure.

```
sudo mount -t [COLOR=#ff0000]**ext2**[/COLOR] -o ro /dev/sdb /mnt
```

You are not specifying a partition to mount in the above command. 

Are you sure the partition is formatted to ext2 and not the default of ext4 ?

```
sudo mount -t [COLOR=#ff0000]**ext2**[/COLOR] -o ro /dev/**sdb1** /mnt
```

```
sudo fsck -v -f /dev/sdb
```

Once again the above command needs a partition to run on.

```
sudo fsck -v -f /dev/**sdb1**
```

> Then somehow I think I end up changing the partitions to SUN partitions...now I am stuck and not too sure what to do...

I'm not quite sure what you did here. fdisk ? parted ?

EDIT:

Just re-read the thread. Is the drive formatted to ntfs ?

Kind regards

---

### Post by jones quest on 2015-04-24
Hi,

The information you provided is a bit hard to follow. The device names are inconsistent.

In the first post you said you did a file system consistency check for device sdb ("fsck -v -f /dev/sdb"). According to the blkid output sdb is:
/dev/sdb1: LABEL="320gig Data" UUID="3CD6F902D6F8BCE8" TYPE="ntfs" PARTUUID="00000001-01"
So this device is a nfts formatted 

Yet you seem convinced that the drive where the recovered information is located is sdd (the one with the odd partition data table type (PTTYPE="sun"). 
According to the fdisk -l
/dev/sdd1 0 3906863414 3906863415 1.8T 83 Linux native
/dev/sdd2 3906863415 3906959804 96390 47.1M 82 Linux swap u
/dev/sdd3 0 3906959804 3906959805 1.8T 5 Whole disk 
This device contains three partitions of which two are linux specific.

Reading between the lines I got the impression that you were trying to recover an ntfs formatted drive. In which case the sdd does not contain what you wanted. Am I wrong???
Is it possible that you in fact copied the device with your dual boot windows + ubuntu gnome onto sdd and not the external usb device you wanted to recover.

In dd rescue command you specify the input device, followed by the output device. 
sudo ddrescue -n -f [/dev/sdc <-- this is input]  [/dev/sdb <-- this is output] extrescue.log

Also the mount command you used is not specific enough and I would suspect the mount type is wrong. Correct me if I'm wrong again :)
"sudo mount -t ext2 -o ro /dev/sdb /mnt"
The device you are trying to mount [/dev/sdb] needs to be specified to the level of partition.
For example: sudo mount -t ext2 -o ro /dev/sdb**1** /mnt
and the mount type [-t ext2] <--  needs to match what is on that partition 
for example sudo mount -t **ntfs-3g** -o ro /dev/sdb1 /mnt
If you in fact did intend to mount an ext2 file system I apologize for my mistake.

Ps. When it comes to recovering data with ddrescue. You should not format the output hard drive before hand as the recovery will simply overwrite the device at the block level, replicating whatever partition tables existed on the input drive.

---

### Post by hpsauce on 2015-04-24
Hello,

Sorry about the confusion, I should have explained all my steps in a little more detail...
When I first started with ddrescue, I only had 3 drive attached to my PC: my dual boot drive which was sda, then my new external USB drive, sdb, then my failing external USB drive, sdc...hence the commands:
sudo ddrescue -n -f /dev/sdc /dev/sdb extrescue.log,
and
sudo ddrescue -d -r3 /dev/sdc /dev/sdb extrescue.log

I was trying to rescue the whole drive sdc onto the whole drive sdb...

Once that was complete I got over excited, and tried to mount sdb, not knowing that I had to mount a specific partition (sdb1)...when that didn't work, I think I did fdisk, which is where I believe I changed the filesystem format by mistake...

After that, I had my PC off for a few days, when I turned my PC on I had connected all of my original drives, hence in the above posts you can see that the drive descriptors do not match the original drive descriptors I had when I ran ddrescue. (I have 2 additional internal hdd's which I had originally disconnected...)

Nevertheless, the current status is that I have /dev/sdd connected, which is my new external USB hdd with the rescued data on it; however now it has 3 partitions, sdd1, 2, 3 as such:

Disk /dev/sdd: 1.8 TiB, 2000365289472 bytes, 3906963456 sectors
Geometry: 255 heads, 63 sectors/track, 46589 cylinders
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: sun

Device          Start        End    Sectors  Size Id Type         Flags
/dev/sdd1           0 3906863414 3906863415  1.8T 83 Linux native      
/dev/sdd2  3906863415 3906959804      96390 47.1M 82 Linux swap      u 
/dev/sdd3           0 3906959804 3906959805  1.8T  5 Whole disk        

Partition table entries are not in disk order.

Is there anything I can do to fix the partition table entries not bein in disk order?
I tried mounting sdd3 only, as this seems to be the whole disk, but I am not sure that I am using the correct command...

Cheers,
hp

---

### Post by jones quest on 2015-04-24
Hi,

Did the failing exteral USB hard drive have 3 partitions on it? (Two of them linux partitions.)
If yes the you have presumably copied over the correct drive.
All you would basically need to do is exactly what you attempted before, but additionally specifying the correct partition.
sudo mount -t [file format] /dev/sdd**3** /mnt

However it's possible that the partition data table type got corrupted by running the fsck command on the whole drive, without specifying the partition.
You can run testdisk to analyze the condition of the drive. You can also use it to recover the partition data table type, etc.
Check their website for step by step instructions.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by matt_symes on 2015-04-24
Hi
```

Device          Start        End    Sectors  Size Id Type         Flags
/dev/sdd1           0 3906863414 3906863415  1.8T 83 Linux native      
/dev/sdd2  3906863415 3906959804      96390 47.1M 82 Linux swap      u 
/dev/sdd3           0 3906959804 3906959805  1.8T  5 Whole disk
```

^^^ That doesn't look right. sdd1 and sdd3 look to be overlapping.

Can you mount /dev/sdd1 ?

```
sudo umount /mnt; sudo mount /dev/sdd1 /mnt
```

Can you then list the files in the /mnt directory ?

```
ls /mnt
```

EDIT:

I believe partition type 5 is an extended partition.

Kind regards

---

### Post by hpsauce on 2015-04-24
Hello,

I tried sudo mount /dev/sdd1 /mnt, and I get the following:

mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

when I do ls /mnt, I get the following:
BootInfo  boot-sav

dmesg | tail gives me the following info:
[37291.459938] audit: type=1400 audit(1429825513.259:35): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3587 comm="apparmor_parser"
[37291.468068] audit: type=1400 audit(1429825513.271:36): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="third_party" pid=3587 comm="apparmor_parser"
[85580.562536] r8169 0000:04:00.0 eth0: link down
[85605.031827] r8169 0000:04:00.0 eth0: link up
[85618.862905] r8169 0000:04:00.0 eth0: link down
[85620.676788] r8169 0000:04:00.0 eth0: link up
[85649.957195] r8169 0000:04:00.0 eth0: link down
[85653.009176] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[85653.476380] r8169 0000:04:00.0 eth0: link up
[85653.476390] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

I have also tried mounting sdd3, and I get the same error...
I am a bit lost...
Thanks,
hp

---

### Post by hpsauce on 2015-04-24
Thanks Jones, I might give that a go...

---

### Post by matt_symes on 2015-04-24
Hi

You could try to use a backup superblock on sdd1 if they are readable. 

No guarantees but does this return anything ?

```
sudo  dumpe2fs /dev/sdd1 | grep -i superblock
```

If so then you may be able to use a backup superblock when running fsck.

Post back the results of the above command and we'll see if it can be used.

BTW: syslog != dmesg.

Kind regards

---

### Post by hpsauce on 2015-04-24
Hi Matt,

here is what I get when I run the above command you mentioned:

dumpe2fs 1.42.10 (18-May-2014)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sdd1
Couldn't find valid filesystem superblock.

Cheers,
hp

---

### Post by hpsauce on 2015-04-25
I have run through testdisk, but that wasn't successful, it originally found the 3 partitions, but then after search and deeper search I couldn't select a partition to access files and copy them.

So now I am running photorec, and that seems to be finding (all?) my files and recovering them! 21hrs to go, so I will let you know how it pans out, but it seems like I will be able to recover my files after all!

Thanks for your help thus far peeps!
hp

---

### Post by matt_symes on 2015-04-25
Hi
> 
I have run through testdisk, but that wasn't successful, it originally  found the 3 partitions, but then after search and deeper search I  couldn't select a partition to access files and copy them.

So now I am running photorec, and that seems to be finding (all?) my  files and recovering them! 21hrs to go, so I will let you know how it  pans out, but it seems like I will be able to recover my files after  all!

Thanks for your help thus far peeps!
hp

At this point i would use ddrescue again on the original disc and copy onto the new disk using the commands and information in all the previous posts.

The reason i would do this is because i cannot be sure what you did before you posted for help. 

> Then somehow I think I end up changing the partitions to SUN partitions...now I am stuck and not too sure what to do...

You see, i'm still not sure what you did here and what other things you may have applied.

Do you have a good backup of that disc ?

Kind regards

---

### Post by hpsauce on 2015-04-25
Hi Matt,

That was my thought as well...I am waiting for photorec to finish doing its thing, once I believe I have copied as near as all the files as possible from my new hdd using photorec, I will format it to ntfs, then go through the ddrescue process again from my old hdd to my new.
I am hoping that in the end I will end up with duplicate of my data that was on my failing hdd, it will take me time to sort through it, but I am happy to have been able to salvage it!

Thanks for your help!
hp

---

