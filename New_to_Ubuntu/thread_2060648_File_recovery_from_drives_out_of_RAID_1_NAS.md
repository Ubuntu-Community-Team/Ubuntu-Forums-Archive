---
title: "File recovery from drives out of RAID 1 NAS"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by arborite on 2012-09-20
I'm a total new to uBuntu... and could use some help...
   
  My iOmega Storcentre NAS crashed because of what appears to have been a Raid controller failure.  I've been told that it runs Linux, and the drives are formatted in Ext3.  I can no longer access the drives and I do not know the condition of the data on the two 1TB drives (RAID 1), as it may have been corrupted by the controller.  
   
  I pulled them out and installed them as secondary drives in a desktop I had laying around (a P4 using a Asus P4P800 motherboard).   I downloaded and installed uBuntu in dual boot with Windows XP pro with the objective of retrieving my data.
   
  In uBuntu, I can easily access the Window's drive and it's files... but not the other two drives.  In the disk utility, I can see all three drives (each NAS drive has two partitions each labelled "Raid Component"). How do I get to the data?  I see no "mount" button available and it won't go to Array. 
   
  Thanks in advance...
  ROb

---

### Post by steeldriver on 2012-09-20
Welcome to the forum

If this is Linux 'soft raid' then I think you have a good chance for recovery - I'm not sure if the regular desktop CD contains all the software RAID tools though so the first thing to do is

```
sudo apt-get update
sudo apt-get install mdadm
```You can then try to read the RAID meta data

```
sudo mdadm --examine /dev/sdXn
```where sdXn is each of the RAID partitions in turn (/dev/sdb2 or whatever - got from the Disk Utility or via fdisk / parted / gparted)

If those check out OK you can try to assemble the array - I'm sure one of the RAID experts will chime in so let's leave it at that for now

---

### Post by arborite on 2012-09-20
Thanks SteelD...  
   
  I'm hoping that because it's RAID 1 (data is written identically to two drives, thereby producing a "mirrored set") that I could be able to access one single drive without the need for the Raid. (one drive is failing)
   
  I did find a post online from several years ago from someone with a similar issue with an iOmega unit (older version I think)... he posted: 
   [INDENT]*How it works:*
*- install the drive in the computer*
*- boot Ubuntu and go to the disk manager and find out which device your data partition is (the first one is the IOmega's mini Linux version, the second one is the swap space and the third one which is also the biggest is the data)*
*- mount the partition as EXT3 - do not change anything in the disk manager, even though Ubuntu detects it as RAID Linux partition:*
*mount -o ro -t EXT3 /dev/sdc3 /mnt/recovery*
*ro is "just in case" and sdc3 was the device in my case*
*I created /mnt/recovery directory before I mounted the partition*
[/INDENT]  Granted, my drives have only two partitions each...  can someone explain the components of:  ***mount -o ro -t EXT3 /dev/sdc3 /mnt/recovery*** ?...  I assuming:
   
  mount  [the command]
  -o ro  [?]
  -t EXT3 [the file type key]
  /dev/sdc3 [the source directory, in his case the 3rd partition on sdc]
  /mnt/recovery [the destination directory]
   
  Do i need to use the "sudo" in front of that command?  Do I use the Disk Utility if I want to create a similar directory "recover1"... ?  Then it would be just a question of dragging and dropping the files to a backup location?
  Thanks again...
  ROb

---

### Post by mips on 2012-09-20
> **arborite said:**
>  
  mount  [the command]
  -o ro  [?]
  -t EXT3 [the file type key]
  /dev/sdc3 [the source directory, in his case the 3rd partition on sdc]
  /mnt/recovery [the destination directory]


[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)
  mount  [the command]
  -o [optionss]
  ro  [read only]
  -t EXT3 [the file system type key]
  /dev/sdc3 [the source partition]]
  /mnt/recovery [mount point for /dev/sdc3, suppose you could call it the destination directory]

---

### Post by arborite on 2012-09-21
Thanks mips...  



I gave it a try last night... here is quick summary:  



I've got two original drives (I'll call drive 1 and drive 2), and one replacement that the NAS tried (perhaps unsuccessfully) at rebuilding the RAID on it (drive 3).  I tested each one individually in the computer (hence they all appeared as "sdb")
   
  **_Drive 1:_** In DiskUtility, I see the SMART Status as "Disk Failure is Imminent"... but I did try mounting this one with the following command:
   [INDENT]*sudo mount &#8211;o ro &#8211;t ext3 /dev/sdb2 /media/disk1*
[/INDENT]  and I got the following error mounting: 

          *mount: wrong fs type, bad option, bad superblock on  /dev/sdb2, missing codepage or helper program, or other error In some  cases useful info is found in syslog -try dmesg | tail or so*
   
  **_Drive 2:_** In DiskUtility, I see the SMART Status as "Disk has a few bad sectors"... but everything else seems fine.  I did try mounting this one with the following command:
   [INDENT]*sudo mount &#8211;o ro &#8211;t ext3 /dev/sdb2 /media/disk2*
[/INDENT]  and I got the following message mounting: 
   [INDENT]*mount: unknown filesystem type 'linux_raid_member'*
[/INDENT]  **_Drive 3:_** In DiskUtility, I see the SMART Status as "Healthy"... but under Volumes, it mentions the "Warning: the partition is misaligned by 512 bytes.  This may result in very poor performance.  Repartitioning is suggested." 
   
  I did try mounting this one with the following command:
   [INDENT]*sudo mount &#8211;o ro &#8211;t ext3 /dev/sdb2 /media/disk3*
[/INDENT]  and I got the following error mounting: 
   [INDENT]*mount: wrong fs type, bad option, bad superblock on /dev/sdb2, missing codepage or helper program, or other error In some cases useful info is found in syslog -try dmesg | tail or so*


[/INDENT]What am i doing wrong?...  Or do i need some application to get at them?
Thanks again... ROb

---

### Post by PEM59 on 2012-11-09
I just had a similar problem.  I have a Buffalo Link station  Model LS-WX1.0TL/R1 that died after only a year.  It seems to be a connection problem.   Since the drives in the device are RAID 1, I think the data is safe, but reading it is the problem.   I am working off of a laptop.  I tried using a USB caddy, and Ubuntu cannot see the drive.  Windows 7 could see it,  but saw it as a bunch of empty drives that needed formatting.  is there some way to recover the data using a USB caddy.

---

### Post by jlirot on 2013-03-09
I am in EXACTLY the same situation.  I don't see this as being resolved.  Any further info?  

I can see the drives but for the life of me I can not mount them.  I've been all over and most of the suggestions are along the same theme as below.  But, I can't get it to work. 

Can anyone help me? 

I have 2 disks and they both seem healthy.  I think it was the Linksys NAS200 that died.  I just can't mount the damn things to get the data off. 

Tried to get mdadm but doesn't seem to install.  Will it install if I'm booting from disk?  

Cheers, 




> **arborite said:**
> Thanks mips...  



I gave it a try last night... here is quick summary:  



I've got two original drives (I'll call drive 1 and drive 2), and one replacement that the NAS tried (perhaps unsuccessfully) at rebuilding the RAID on it (drive 3).  I tested each one individually in the computer (hence they all appeared as "sdb")
   
  **_Drive 1:_** In DiskUtility, I see the SMART Status as "Disk Failure is Imminent"... but I did try mounting this one with the following command:[INDENT]*sudo mount –o ro –t ext3 /dev/sdb2 /media/disk1*
[/INDENT]
and I got the following error mounting: 

          *mount: wrong fs type, bad option, bad superblock on  /dev/sdb2, missing codepage or helper program, or other error In some  cases useful info is found in syslog -try dmesg | tail or so*
   
  **_Drive 2:_** In DiskUtility, I see the SMART Status as "Disk has a few bad sectors"... but everything else seems fine.  I did try mounting this one with the following command:[INDENT]*sudo mount –o ro –t ext3 /dev/sdb2 /media/disk2*
[/INDENT]
and I got the following message mounting: [INDENT]*mount: unknown filesystem type 'linux_raid_member'*
[/INDENT]
**_Drive 3:_** In DiskUtility, I see the SMART Status as "Healthy"... but under Volumes, it mentions the "Warning: the partition is misaligned by 512 bytes.  This may result in very poor performance.  Repartitioning is suggested." 
   
  I did try mounting this one with the following command:[INDENT]*sudo mount –o ro –t ext3 /dev/sdb2 /media/disk3*
[/INDENT]
and I got the following error mounting: [INDENT]*mount: wrong fs type, bad option, bad superblock on /dev/sdb2, missing codepage or helper program, or other error In some cases useful info is found in syslog -try dmesg | tail or so*


[/INDENT]
What am i doing wrong?...  Or do i need some application to get at them?
Thanks again... ROb

---

### Post by tgalati4 on 2013-03-09
RAID1 is not a backup strategy.  As you can see from the posts of this thread, that when a hardware NAS, with presumably hardware RAID goes bad, it is difficult to recover the data, without buying another, identical NAS chassis to put the drives in.  Even then, if there are encrypted headers or UUID's embedded in the disk tables, then even the new chassis might refuse to read the drives.

I would like to hear from the OP if he had any success recovering the data.

---

### Post by jlirot on 2013-03-09
Funny u mentioned putting into same system.  i actually went out and bought the exact same system to do just that.  problem is i don't have a pc computer to set up the linksys nas200.  also, i don't know if i can set it up without reformatting the drives.  so, instead of focusing on that can o worms, i've been focusing on trying to get the data mounted.  it seems everyone but me and the OP has been successful.  since my problems are the same as the OP (to the letter) i'm really interested in knowing how he solved his problems.

---

