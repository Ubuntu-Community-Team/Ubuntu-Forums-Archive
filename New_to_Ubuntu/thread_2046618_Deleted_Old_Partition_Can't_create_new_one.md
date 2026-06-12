---
title: "Deleted Old Partition Can't create new one"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by KGibbons83 on 2012-08-23
I've been searching for two days and trying to get an old windows partition mounted, but nothing I try seems to work.  I've created mount points, and when it seems like it is working, I reboot and get the message that either it can't be mounted or it isn't ready.  I could definitely use some help, I'd like to be able to use this 350ish gigs of extra space.

Thanks!):P

---

### Post by Lisiano on 2012-08-23
I don't understand. You delete a partition and can't create a new one or you can't mount a partition on boot? Depending on what you want, you need to do different things.

---

### Post by KGibbons83 on 2012-08-23
I deleted the old windows partition, using gparted.  Now, unallocated.  I *did* make it an ext3, then tried to mount it...not using gparted, using terminal because gparted doesn't give me the option to mount it.  It seems to work until I restart my system.

---

### Post by steeldriver on 2012-08-23
To automount the new partition on boot you need to make an entry for it in your /etc/fstab file

---

### Post by KGibbons83 on 2012-08-23
I did that using the code 

sudo gedit /etc/fstab 

/dev/sda /katsmedia ext3 defaults 0 0

was the line that I put into the /etc/fstab but it istill isn't working.

Thanks -

---

### Post by steeldriver on 2012-08-23
sda would be the whole device, not the partition I would think? can you post the output of these commands:

```
sudo fdisk -l

sudo blkid
```

---

### Post by Lisiano on 2012-08-23
I see. So you wish to mount it at boot, correct?
Open a terminal (Ctrl+Alt+T) and type in the following
```
sudo blkid -c /dev/null
```
Try to locate the partition you created (Either by /dev/sdx or by the label)
Copy the UUID line you want. We know from fdisk it's /dev/sda5 because of the size.
```
lisiano@Lisiano-Ubuntu:~$ sudo blkid -c /dev/null
/dev/sda1: LABEL="Recovery" UUID="7430A7A730A76F34" TYPE="ntfs" 
/dev/sda2: LABEL="System Reserved" UUID="E856DBE256DBAF94" TYPE="ntfs" 
/dev/sda3: UUID="698563b0-38fb-406b-8d0a-b97e256116a9" TYPE="ext3" 
/dev/sda5: UUID="**a91aacf4-0393-4835-9b32-5c66c81503b4**" TYPE="ext4" 
/dev/sda6: UUID="4979958d-75c2-4f0e-8f05-68fc42b693d5" TYPE="swap" 
```
Now type in the following in the terminal
```
gksudo gedit /etc/fstab
```
Be careful not to touch anything beside what I tell you.
You will get something like this
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=698563b0-38fb-406b-8d0a-b97e256116a9 /               ext4    errors=remount-ro 0       1
UUID=4979958d-75c2-4f0e-8f05-68fc42b693d5 none            swap    sw              0       0
```
You will need to add a line that will look like this to the end of the file
```
UUID=a91aacf4-0393-4835-9b32-5c66c81503b4 /katsmedia  ext4 defaults 0 2
```

Now you will need to just save it, now when you reboot, it will be mounted and ready for you.

P.S. Wow I took a while to write it all.

EDIT: Substituted entries with KGibbons83's entries.

---

### Post by KGibbons83 on 2012-08-23
sudo fdisk -l 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa1bd4ed9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    22310911    11154432   27  Hidden NTFS WinRE
/dev/sda2   *    22310912    22515711      102400    7  HPFS/NTFS/exFAT
/dev/sda3        22515712   730294271   353889280   83  Linux
/dev/sda4       730296318  1250263039   259983361    5  Extended
/dev/sda5       730296320  1242566655   256135168   83  Linux
/dev/sda6      1242568704  1250263039     3847168   82  Linux swap / Solaris


sudo blkid

/dev/sda1: LABEL="Recovery" UUID="7430A7A730A76F34" TYPE="ntfs" 
/dev/sda2: LABEL="System Reserved" UUID="E856DBE256DBAF94" TYPE="ntfs" 
/dev/sda3: UUID="698563b0-38fb-406b-8d0a-b97e256116a9" TYPE="ext3" 
/dev/sda5: UUID="a91aacf4-0393-4835-9b32-5c66c81503b4" TYPE="ext4" 
/dev/sda6: UUID="4979958d-75c2-4f0e-8f05-68fc42b693d5" TYPE="swap"

---

### Post by steeldriver on 2012-08-23
great - so now you can follow Lisiano's excellent instructions

---

### Post by Lisiano on 2012-08-23
Updated whatever I typed so there is no guesswork.

---

### Post by KGibbons83 on 2012-08-23
I followed all direction, gparted says it is mounted where I would like it mounted.  Unfortunately, when I go to properties, it is saying the size is the original size of the /home drive and not the new one.  -.-

---

### Post by Lisiano on 2012-08-23
What size is it reporting exactly?
My calculations report that the size of the partition should be near 256GB

---

### Post by Finnicella on 2012-08-23
Sorry for the intrusion, but I think the partition he want to mount is /dev/sda3: UUID="698563b0-38fb-406b-8d0a-b97e256116a9" TYPE="ext3"
>  I *did* make it an ext3
I'd like to be able to use this 350ish gigs of extra space
Bye and sorry for my english. :D

---

### Post by oldfred on 2012-08-23
Then the ex3 & ext4 partitions are mixed up and the / partition is wrong. UUID 69xxx is mounted as ext4 and as root.

> UUID=[COLOR=Red]698563b0-38fb-406b-8d0a-b97e256116a9[/COLOR] /               [COLOR=Red]ext4  [/COLOR]  errors=remount-ro 0       1

> /dev/sda3: UUID="[COLOR=Red]698563b0-38fb-406b-8d0a-b97e256116a9[/COLOR]" TYPE="[COLOR=Red]ext3[/COLOR]" 
/dev/sda5: UUID="a91aacf4-0393-4835-9b32-5c66c81503b4" TYPE="ext4" 


Because fstab is not showing the normal comments it looks like fstab was manually edited. Either UUID or ext4 is then wrong in fstab for / (root) and the UUIDs are mixed up.  It probably is sda5 that is / and ext4 is correct in fstab but hten UUID should be the sda5 UUID not the sda3 UUID.

So which partition is really root and which is data.

---

### Post by Lisiano on 2012-08-24
@oldfred
He didn't provide his fstab, I just made one up from the information I saw.

@oldfred and @Finnicella
I kind of assumed his new partition was in an Extended partition. You might be right though that it is the reverse.

@KGibbons83
Can you also provide the outputs from the following 2 commands?
```
mount
```
```
df
```

---

