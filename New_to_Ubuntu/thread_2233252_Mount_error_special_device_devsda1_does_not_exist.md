---
title: "Mount error special device /dev/sda1 does not exist"
date: 2014-07-07
forum: New to Ubuntu
---

### Post by Suparno on 2014-07-07
Hi everyone,

        I am trying to recover some data from a ext4 file system. Just to give a bit of a background i was using Ubuntu 12.04 since last 6 months. Recently i had done a R update and after the next restart i am not being able to boot the machine at all.
For more details please refer to my original thread [http://askubuntu.com/questions/492095/kernel-panic-not-syncing-vfs-unable-to-mount-root-ubuntu-12-04lts?lq=1](http://askubuntu.com/questions/492095/kernel-panic-not-syncing-vfs-unable-to-mount-root-ubuntu-12-04lts?lq=1).

Right now i am trying to recover my data using a live usb of 13.04. I have got some of my data back but i still can't access the /dev/sda1 which had most of my data. The partition is  showing in gparted as well as sudo fdisk -l.  
Sudo fdisk -l output:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00052866

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   909690879   454844416   83  Linux
/dev/sda2       909692926   976766975    33537025    5  Extended
/dev/sda5       909692928   976766975    33537024   82  Linux swap / Solaris


But when i try to mount it using  "sudo mount /dev/sda1 /mnt/" it throws me an error 

mount: special device /dev/sda1 does not exist

and when i try this "sudo mount /dev/sda /mnt/" it throws me another error 

mount: unknown filesystem type 'isw_raid_member'

This is a ext4 file system and i dont see anyreason why the hard disk would have been corrupted. Anyone has anyclue on how to solve this. 

Thanks,

Suparno

---

### Post by yancek on 2014-07-07
> mount: unknown filesystem type 'isw_raid_member'

That indicates you have RAID, so the mount command will be different.  You can verify the partition types with the command below.  I've never used RAID so can't help. 

```
sudo parted /dev/sda print all
```

---

### Post by Suparno on 2014-07-08
I seriously have no clue what to make the output:

```
Model: ATA WDC WD5003ABYX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  466GB  466GB   primary   ext4
 2      466GB   500GB  34.3GB  extended
 5      466GB   500GB  34.3GB  logical   linux-swap(v1)


Model: ATA WDC WD5003ABYX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  466GB  466GB   primary   ext4
 2      466GB   500GB  34.3GB  extended
 5      466GB   500GB  34.3GB  logical   linux-swap(v1)


Model: ATA INTEL SSDSA2M080 (scsi)
Disk /dev/sdc: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  80.0GB  80.0GB  primary  ntfs


Model: General USB Flash Disk (scsi)
Disk /dev/sdd: 4009MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  4009MB  4009MB  primary  fat32        boot


Model: LSILOGIC Logical Volume (scsi)
Disk /dev/sde: 2250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   2250GB  2250GB  ntfs         Basic data partition


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_becbdadhci_Volume1p5: 34.3GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  34.3GB  34.3GB  linux-swap(v1)


Error: Can't have a partition outside the disk!                           

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_becbdadhci_Volume1p1: 466GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  466GB  466GB  ext4


Model: Linux device-mapper (mirror) (dm)
Disk /dev/mapper/isw_becbdadhci_Volume1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  466GB  466GB   primary   ext4
 2      466GB   500GB  34.3GB  extended
 5      466GB   500GB  34.3GB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
```

---

### Post by Suparno on 2014-07-08
But the interesting thing is there is no UUID for /dev/sda ( i guess thats expected as it's a part of RAID)

 sudo blkid:

```
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="b90a06d7-4c25-6648-8661-84973bbabd82" TYPE="ext2" 
/dev/sr0: LABEL="ISSDA CER" TYPE="udf" 
/dev/sda: TYPE="isw_raid_member" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc1: LABEL="SSD" UUID="B844627A44623B70" TYPE="ntfs" 
/dev/mapper/isw_becbdadhci_Volume1p1: UUID="f602aca3-cfe6-4460-8374-ba3f77eb6d47" TYPE="ext4" 
/dev/sdd1: LABEL="MYLINUXLIVE" UUID="5642-BD55" TYPE="vfat" 
/dev/sde2: LABEL="RAID5" UUID="9CCC6D2FCC6D04BC" TYPE="ntfs" 
/dev/mapper/isw_becbdadhci_Volume1p5: UUID="2b61748a-f9c5-4f34-be1c-c6d24f1647a7" TYPE="swap"
```

---

### Post by yancek on 2014-07-08
In your initial post, you indicate you did an "R update" which to me means you upgraded to 14.04 (release update).  I'm not sure if that is correct, what you intended or what you did but if it is, that would be a reason for your problems.  Obviously, anytime you are doing an upgrade, you need a backup of all important data.


I believe the UUID is for partitions only, there are other commands to get device ids, see the link below:

 [http://serverfault.com/questions/5031/how-can-i-find-out-what-hard-disks-are-attached-to-a-linux-box](http://serverfault.com/questions/5031/how-can-i-find-out-what-hard-disks-are-attached-to-a-linux-box)

I think you need to use a modification of the lines you posted above from the blkid output, the one beginning with /dev/mapper showing ext4 filesystem but, having never used RAID, have no idea what that would be.

---

### Post by steeldriver on 2014-07-08
Let's take a few steps back here

/dev/sda and /dev/sdb appear to be Intel (ISW) BIOS RAID - is that what you expect? You said "the /dev/sda1 which had most of my data" - but remember that the /dev/sdX designations can change at boot time. Was your data on the RAID volume?

@yancek I believe the "R update" in this case refers to a package update of the r-cran statistical package(s) rather than a release update

---

### Post by Suparno on 2014-07-08
@yancek , steeldriver is right. "R" basically refers to statistical programming language. I didn't update my OS. But in anycase it was extremely stupid of me to not backup my thesiswork :(

@steeldriver yes i do expect them to be on the RAID drive. The thing is i didn't setup this machine but and i was not too aware of the RAID configurations up until now because it never really bothered me. But from the disk utility image i can see that the hard drive which contained my data is indeed a part of the RAID. 

[IMG]http://i58.tinypic.com/nlzbeo.png[/IMG]

---

### Post by Suparno on 2014-07-08
The output for sudo lshw -class disk:

```
*-disk:0 UNCLAIMED      
       description: ATA Disk
       product: ST31500341AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       version: HP23
       serial: 9VS3H5HQ
       capacity: 1397GiB (1500GB)
       capabilities: 15000rpm
       configuration: ansiversion=5
  *-disk:1 UNCLAIMED
       description: ATA Disk
       product: ST31500341AS
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@7:0.1.0
       version: HP23
       serial: 9VS3H5EL
       capacity: 1397GiB (1500GB)
       capabilities: 15000rpm
       configuration: ansiversion=5
  *-disk:2 UNCLAIMED
       description: ATA Disk
       product: ST31500341AS
       vendor: Seagate
       physical id: 0.2.0
       bus info: scsi@7:0.2.0
       version: HP23
       serial: 9VS3H5V3
       capacity: 1397GiB (1500GB)
       capabilities: 15000rpm
       configuration: ansiversion=5
  *-disk:3 UNCLAIMED
       description: ATA Disk
       product: ST31500341AS
       vendor: Seagate
       physical id: 0.3.0
       bus info: scsi@7:0.3.0
       version: HP23
       serial: 9VS3H2PM
       capacity: 1397GiB (1500GB)
       capabilities: 15000rpm
       configuration: ansiversion=5
  *-disk:4
       description: SCSI Disk
       product: Logical Volume
       vendor: LSILOGIC
       physical id: 1.1.0
       bus info: scsi@7:1.1.0
       logical name: /dev/sde
       version: 3000
       size: 2095GiB (2249GB)
       capabilities: 15000rpm gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=2 guid=fe6246e3-703d-4f73-a7a8-97cd55ac6373
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-H653R
       vendor: hp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       logical name: /media/ISSDA CER
       version: 0E00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=999,gid=999,umask=77,dmode=500,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/ISSDA CER
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=999,gid=999,umask=77,dmode=500,iocharset=utf8 state=mounted
  *-disk
       description: ATA Disk
       product: WDC WD5003ABYX-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WMAYP4167580
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00052866
  *-disk
       description: ATA Disk
       product: WDC WD5003ABYX-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WMAYP4081550
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00052866
  *-disk
       description: ATA Disk
       product: INTEL SSDSA2M080
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdc
       version: 2CV1
       serial: CVPO00400053080BGN
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=ce7722b3
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdd
       size: 3823MiB (4008MB)
       capabilities: partitioned partitioned:dos
```

---

### Post by steeldriver on 2014-07-08
OK so in that case your data is not directly "on" /dev/sda1 - it's on the assembled array /dev/mapper/isw_becbdadhci_Volume1p1 so that's what you should be trying to mount, I think

If you're trying to do that from a live CD, you may need to install the dmraid package first

---

### Post by Suparno on 2014-07-08
okay that worked .But that drive didnt have the data. I guess i will try the other /dev/mapper/X.

---

### Post by Suparno on 2014-07-08
I tried mounting /dev/mapper/isw_becbdadhci_Volume1 as well but this didnt work. said it was already mounted or mount point busy.If /dev/sda was indeed  /dev/mapper/isw_becbdadhci_Volume1p1 Seems all my data has just vanished in thin air :(

---

### Post by Bashing-om on 2014-07-08
Suparno; Hey;

As I redirect myself from that original thread of yours -

You are in the best of hands here with steeldriver's guidance, There is nothing I can add to what steeldriver will advise.

I will make this comment to try and comfort you in this time of trial. No data is lost, perhaps the "pointers" to that data, but those bits on the hard drive remain until overwritten. So the thing is until the raid array can be reassembled, do not write anything to those disks !

It will take someone who is intimate with raid to fix this situation,

[INDENT][INDENT][INDENT][INDENT]and it ain't me, no no !
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steeldriver on 2014-07-08
> **Bashing-om said:**
> 
[INDENT][INDENT][INDENT][INDENT]and it ain't me, no no !
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


... and it ain't me neither unfortunately - especially not for dmraid. It's *possible* that the raid set just needs to be activated, however my first thought is it wouldn't have mounted at all if that were the case. Was there anything at all (such as a lost+found directory) on the /dev/mapper/isw_becbdadhci_Volume1p1 volume when you did manage to mount it?

---

### Post by Suparno on 2014-07-08
[COLOR=#000000]@ [/COLOR]**Bashing****-om **Thanks for your comforting words and all the help you have provided till now :). I also believe that data should be there somewhere and the drives can't really be harmed by something as simple as a programming language version upgrade. I am definitely not giving up yet.

@Steeldriver As far as i remember there was. I guess it said that the contents of the folder couldn't be displayed when i tried to access it. As far as the RAID configuration is concerned i will have a chat with the guy who had setup the RAID and ubuntu tomorrow. I hope he can throw some light how this whole thing works.

---

### Post by steeldriver on 2014-07-08
best case, that sounds like it might be nothing more serious than a permissions problem - let us know how it works out tomorrow

---

### Post by Suparno on 2014-07-10
Hi, Sorry for the late reply. I still didnt manage to recover my data but seems finally i have managed to see where it might be. This is a screeshot of the properties of /dev/mapper/isw_becbdadhci_Volume1p1

[http://i61.tinypic.com/2h3ufqp.png](http://i61.tinypic.com/2h3ufqp.png)

As you can see the contents are 2.2 gb, whereas it says 25 GB used !!. I think this is where all my data is. The screenshot is taken while accessing the drive by "sudo nautilus". So donT think its a permission problem. Anyclue how to get the rest of the data?

---

### Post by Suparno on 2014-07-10
Okaz now it got crazier. I tried to image the disk using ddrescue it failed read even a single byte in last 1.5 hours. Though i can't see why it couldnt get at least the 2.2 gb of data that was showing up in nautilus(maybe cause its still mounted and i used the mountpoint istead of the drive?)
Anyways heres the output

```
sudo ddrescue -r 3 /media/f602aca3-cfe6-4460-8374-ba3f77eb6d47 /media/RAID5/recovery /media/RAID5/logfile

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:         0 B,  errsize:   9223 PB,  current rate:        0 B/s
   ipos:    11957 GB,   errors:       1,    average rate:        0 B/s
   opos:    11957 GB,     time from last successful read:     1.6 h
Splitting failed blocks... 
Interrupted by user

```

---

### Post by steeldriver on 2014-07-10
I'm thinking you should probably unmount the array and fsck it - **however you should wait for someone more knowledgeable to confirm that**

---

### Post by oldfred on 2014-07-10
I do not use RAID and there are many types. But you seem to show something about LSIlogic which is a hardware RAID?

Is the partition labeled RAID5 really NTFS? 
If so you need to mount it and use Windows repair tools to run chkdsk not Linux tools as they cannot fix NTFS formatted errors. Not sure how to mount a proprietary RAID with a Windows repair CD or Flash drive.

---

