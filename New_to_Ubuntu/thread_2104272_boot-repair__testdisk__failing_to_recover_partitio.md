---
title: "boot-repair / testdisk / failing to recover partition"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by cocos1d on 2013-01-12
Hello All,

I know I have done everything wrong to this point first of all by not making a backup, but currently kind of stuck with partition recovery.
* I have two ~750Gb SATA disks in RAID0 (named Alle) so it sums up to ~1.5Gb RAID.
* Installed Ubuntu 12.04 on 1Tb partition (/dev/mapper/...Alle1), left 500Gb for Windows. It was some time ago.
* Now installed Windows on an additional ~400Gb partition (/dev/mapper/...Alle2).
* Decided to restore GRUB2 after Win installation using boot-repair (from ubuntu-secure USB flash drive / 1Gb Memorex)
  ** Switched to advanced options,  "Restore GRUB" was selected, restore MBR **un**selected. Applied.
  ** boot-repair performed some actions and kind of hanged at the end. After several minutes I closed it.
  ** Tried to restart to check if it helped, no luck
  ** Booted ubuntu-secure again, executed boot-repair's "Recommended repair"
  ** Rebooted, but Windows was loaded
* Rebooted to ubuntu-secure, tried testdisk:
  ** sudo testdisk /dev/mapper/...Alle1
  ** It found *Linux (primary bootable) started at 2, wrote changes to the partition table
* Tried to restore GRUB using 12.04 alternate CD:
  ** Detected disks, configured partition as ext4, mount to '/', no formatting
  ** Attempted to install GRUB, no luck

So it looks like I have broken partition /dev/mapper/...Alle1p1 start position. Is it possible to restore it to some default value? What would it be, 0?
After all I made boot-info, not sure if it is usefull: [http://paste.ubuntu.com/1524436/](http://paste.ubuntu.com/1524436/)

I would appreciate any advice how to resolve the problem.

---

### Post by oldfred on 2013-01-12
I do not know RAID, but it looks like you have some corruption in your partition, so Boot-Repair cannot see the install to suggest to then install grub to the root of your RAID.

Do you run e2fsck on RAID like you do a "normal" ext4 partition?

Except I assume it is your /mapper/..... not sdb1 as mount point? And from liveCD you may have to install lvm2 driver.
       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by cocos1d on 2013-01-12
Fred, thank you for your reply.

> **oldfred said:**
> Do you run e2fsck on RAID like you do a "normal" ext4 partition? I am actually afraid of running e2fsck against this partition since because the partition is not properly aligned (I guess) the data are invalid anyway so e2fsck might attempt to fix something and the partition will be totally unrecoverable.

> **oldfred said:**
> 
Except I assume it is your /mapper/..... not sdb1 as mount point? And from liveCD you may have to install lvm2 driver.
       
I can access the RAID from [ubuntu-secure]("https://help.ubuntu.com/community/UbuntuSecureRemix").

I think the issue is with partition boundaries changed by testdisk, so I can't figure out how to shift them, say to 0 or what would it be if ubuntu was installed on the first partition?

---

### Post by oldfred on 2013-01-12
Your partitions do not look aligned. Normal start used to be sector 63, but for the last couple of years it has been sector 2048 for better alignment with SSD and new 4K drives. Is your 2TB drive a 4K drive?

Normal install of Ubuntu to drives somewhere over 1TB is also gpt partitions not MBR(msdos). Was drive gpt before and testdisk converted it to MBR? 
MBR has a max of 2TB so it still would work on your drive.

But RAID may do its own thing and I have never installed RAID.

---

### Post by cocos1d on 2013-01-13
So the main question that remain to me is how adjust partition start/end positions without affecting data on these partitions?
As far as I understand by now sdisk or parted should be used, but I am basically afraid of experimenting further. Could you please give me an exact command to type in  order to set START and END positions for a partition?

> **oldfred said:**
> 
Normal install of Ubuntu to drives somewhere over 1TB is also gpt  partitions not MBR(msdos). Was drive gpt before and testdisk converted  it to MBR? 

It is currently MBR, since gdisk reports that it found invalid GPT and found valid MBR. What was before I started my silly experiments, not sure. What I can say that it was GRUB, then updated to GRUB2, but GRUB could be installed on both: MBR and GPT I guess, so unfortunately I have no idea.

> **oldfred said:**
> Your partitions do not look aligned. Normal start used to be sector 63, but for the last couple of years it has been sector 2048 for better alignment with SSD and new 4K drives. Is your 2TB drive a 4K drive?

Yes, I think I broke partition start/end positions. This is what **gparted** thinks about my disk:

[IMG]http://savepic.ru/3861321.jpg[/IMG]

This last partition (Alle3) is a temp Ubuntu installation I made to avoid configuring Live every time.
Could you please also have a look at **sudo sfdisk -l** output:

```

Disk /dev/mapper/isw_dcfegcdggj_Alle: 182402 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
[COLOR=Sienna]/dev/mapper/isw_dcfegcdggj_Alle1          0+ 122791- 122792- 986326669+   5  Extended[/COLOR]
/dev/mapper/isw_dcfegcdggj_Alle2   * 122792  169652   46861  376410982+   7  HPFS/NTFS/exFAT
/dev/mapper/isw_dcfegcdggj_Alle3     169653+ 182402-  12750- 102406656   83  Linux
/dev/mapper/isw_dcfegcdggj_Alle4          0       -       0          0    0  Empty
[COLOR=Red]/dev/mapper/isw_dcfegcdggj_Alle5   *      0+ 121567- 121568- 976494896   83  Linux
        start: (c,h,s) expected (0,2,1) found (2,0,1)
        end: (c,h,s) expected (1023,254,63) found (1023,0,1)[/COLOR]
/dev/mapper/isw_dcfegcdggj_Alle6     121568+ 122791-   1224-   9831740   82  Linux swap / Solaris
        start: (c,h,s) expected (1023,254,63) found (1023,0,1)
        end: (c,h,s) expected (1023,254,63) found (1023,0,1)


```

---

### Post by cocos1d on 2013-01-13
Provided that current positions are: START: 2, END: 1952989793, my guess is that it should be **parted**'s:
```
move /dev/mapper/...Alle5 0 1952989795
``` (move start 2 bytes back and end 2 bytes forward) in case I want to align to 0 or
```
move /dev/mapper/...Alle5 63 1952989795
```  in order to align to 63. Or should it be  ```
move /dev/mapper/...Alle5 64 1952989795
``` ?
Could you please confirm?

---

### Post by oldfred on 2013-01-13
I really do not know with RAID. I only have this in my notes, but it may not be current:

Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)

---

### Post by cocos1d on 2013-01-14
Finally it turned out to be a superblock problem. Your suggestion to e2fsck worked.

* testdisk was able to read files from a recovered partition, copied files to a backup dev
* used a superblock location provided by testdisk to e2fsck-y -n <superblock> /dev/mapper/...Alle5
* Rebooted, reinstalled GRUB

---

