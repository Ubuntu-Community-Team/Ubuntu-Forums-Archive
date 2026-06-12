---
title: "&quot;Backup&quot; app says 160gigs is &gt; 500 gigs?"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2014-04-04
The Ubuntu default program, (badly named) Backup reports that it cannot find enough space. The folders being backed up are /home and nothing else. A few folders in /home are being excluded, for example: /dvd.

The size of /home is approx. 180 gig. The size of the storage for a backup is 400 gig.

Some background about this may be in order.

A week ago, using clonezilla (hereafter cz), I cloned my /dev/sda from a 400 gig to a 1T drive. The clonezilla must have burped. I do have a cloned, functional hard disk drive, but cz created a mess. I have an /dev/sda that is approx. 500 gig, an 8 gig swap file following that partition and then approx. 500 gig unallocated. I tried, using a LiveUSB session to make GParted move the swap, delete the swap, etc. I tried to expand both the /sda and move/resize unallocated

NOTHING worked.

Next, the 400 gig (SATA) drive which had been the boot hard disk drive was removed and installed in an external box. On starting up this device, the /home partition could be removed, but not the / (boot). At least not by GParted. It reported the / as "Busy", even though it is in an external drive cradle, and powered up after starting the computer.

Next, I took the 400g and connected it to a microsoft machine and was able to delete the boot partition. Then, back at Ubuntu, under GParted, the drive was formatted ext4 and there is but only one partition for the entire 400g as it's use is for backup up my /home. (the external box is both eSATA and USB)

As always, GParted sets devices (Partitions) as root:root and Ubuntu's default backup applet: Backup cannot use that. So I started searching for the keywords: external, fstab, usb, and after several trials, I have converted the root:root to mark:mark. That was last night. When powered up today, the splash screen said that the device with:

UUID=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

was not mounted, did I want to Wait, Mount or Skip. Before I could choose, the OS decided to boot without it. 

So my question is: Why is Backup reporting insufficient space?

Some particulars:

mark@Lexington:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00084ceb

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39063551    19530752   83  Linux
/dev/sda2       765798398   781422591     7812097    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3        39063552   765796351   363366400   83  Linux
/dev/sda4       781422592  1953523711   586050560   83  Linux
/dev/sda5       765800448   781422591     7811072   82  Linux swap / Solaris
```

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

```
Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   781422767   390711383+  ee  GPT
```


mark@Lexington:~$ sudo blkid
/dev/sda1: UUID="536a864f-d91c-4e3d-b6f6-108a783d5e46" TYPE="ext4" 
/dev/sda3: UUID="1455a163-528e-42ec-8b29-ca7076fc00c7" TYPE="ext4" 
/dev/sda4: UUID="bb3741fb-dd99-4ffc-99c5-56d36ed3d292" TYPE="ext4" 
/dev/sda5: UUID="8fba474d-db51-4e6a-9146-030e45900dbd" TYPE="swap" 
/dev/sdb1: UUID="80cb5313-35a0-432b-9250-4cc62d79a3c8" TYPE="ext4"

Lastly:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=536a864f-d91c-4e3d-b6f6-108a783d5e46  /            ext4  errors=remount-ro    0  1  
# /home was on /dev/sda3 during installation
UUID=1455a163-528e-42ec-8b29-ca7076fc00c7  /home        ext4  defaults             0  2  
# swap was on /dev/sda5 during installation
UUID=a37873a0-d70f-495f-92ea-fffb41041cf4  none         swap  sw                   0  0  
## below by mp 3-apr-14
UUID=4035f386-aae1-49b5-a0b2-f077dc662003  /media/backup  ext4  noauto

/dev/sdb1                                  /media/sdb1  ext4  users,noauto,user    0  0  (the OS added this automatically)
```

Yes, I made a directory in /media named: backup. Screenshots of the partitions on /dev/sda and /dev/sdb attached.[ATTACH=CONFIG]251709[/ATTACH][ATTACH=CONFIG]251709[/ATTACH][ATTACH=CONFIG]251710[/ATTACH]

---

### Post by The Cog on 2014-04-04
sda is a bit of a bag o' nails, but should be usable. 

sdb has lots of free space, but your screenshot shows it not to be mounted. If it wasn't mounted when you tried to do the backup then there would not have been enough space because you would have been backing up to a directory on sda. So that's one possibility I can think of.

In your screenshot of sda in gparted, the unallocated is not unallocated, it is a primary partition sda4. I would have expected cz to make a perfect replica of the smaller disk, which it would be if it weren't for the existence of partition sda4. Are you sure you didn't create that partition yourself after making the clone?

If you want to rearrange sda, my first move would be to delete sda4 (assuming you have nothing important stored on it. Then you could expand the extended partition sda2 to encompass the unallocated 559G. This leaves you free to make, move resize logical partitions inside the extended one. Except for the swap partition which the live CD has probably found and used. The command
```
swapon -s
``` will show if it's in use. If it is, ```
sudo swapoff /dev/sda5
``` will release it.

---

### Post by Mark_in_Hollywood on 2014-04-04
Thanks for the quick post.

Answering your question: [COLOR="#FF0000"]"Are you sure you didn't create that partition yourself after making the clone?"[/COLOR] Answer: "No"

The source drive, 400gig, had but 3 partitions, it having been manually created a while ago, after I destroyed the boot by accident. Those named partitions are: / and /home and swap, respectively /dev/sda1, /dev/sda5 and /dev/sda3. I have no idea as to the numerical order.

About unallocated, versus allocated. You are correct. Yesterday, looking at the GParted map, the space was unallocated. Trying to move the swap to the end (far right) today, I formatted the unallocated and what you see in the screenshot, is the result of that formatting. I could not move, change, resize any of these partitions, using GParted, in LiveUSB mode.

[COLOR="#FF0000"]"I would have expected cz to make a perfect replica of the smaller disk, which it would be if it weren't for the existence of partition sda4."[/COLOR] - There was NO, I repeat NO /sda4 on the day cz was used. The 400g drive was cloned to the bare-metal 1T drive. Clonezilla, without my asking, or informing me, divided the 1T drive on it's own volition. You can read about that at my post: [Partition Size, using dd and options afterwords]("http://ubuntuforums.org/showthread.php?t=2212528") 

When cz ran, I was asked if I wanted to clone the boot sector - I said YES
When cz ran, I was asked if I wanted the default clone - I said YES

---

### Post by Mark_in_Hollywood on 2014-04-04
The Cog:

I'm in LiveUSB mode, and have managed to delete the "swap" via your instructions.

Please see the screenshot, below:

[ATTACH=CONFIG]251717[/ATTACH]

I have attempted to move/resize both sda3 as well as the (now, again) unallocated space and I cannot figure out what I'm doing. Neither /sda3 nor the unallocated allow me to expand, move or resize. For example: If I select /sda3 and try to enlarge it, there is nothing for it to enlarge into. I have managed to make a new "swap"

 [ATTACH=CONFIG]251718[/ATTACH]

But I cannot enlarge /sda3 into the unallocated without your help.

---

### Post by The Cog on 2014-04-04
So you want to enlarge sda3. You can't at the moment, because the extended partition (a container for logical partitions) is in the way. sda2 no longer contains any logical partitions (you have deleted those), but the container partition sda2 still exists. I think you need to delete sda2 adn then you will be able to expand sda3.

Don't worry about the numbers being out of order.

---

### Post by Mark_in_Hollywood on 2014-04-04
```
mark@Lexington:~$ df -a
Filesystem       1K-blocks      Used Available Use% Mounted on
/dev/sda1         19091584   7014644  11100408  39% /
proc                     0         0         0    - /proc
sysfs                    0         0         0    - /sys
none                     0         0         0    - /sys/fs/fuse/connections
none                     0         0         0    - /sys/kernel/debug
none                     0         0         0    - /sys/kernel/security
udev               1981952        12   1981940   1% /dev
devpts                   0         0         0    - /dev/pts
tmpfs               404900       900    404000   1% /run
none                  5120         0      5120   0% /run/lock
none               2024492      2252   2022240   1% /run/shm
/dev/sda3        934015104 179092496 707470704  21% /home
binfmt_misc              0         0         0    - /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon         0         0         0    - /home/mark/.gvfs

```

Is the report about 1K-blocks correct? I thought this is large/modern enough hdd for 4K?

---

### Post by The Cog on 2014-04-04
My brain's going. I meant df -h for human sizes. 

fdisk reported:
Sector size (logical/physical): 512 bytes / 4096 bytes
whick looks normal to me. I don't really know why fdisk defaults to measuring units if 1k. History, I guess.
I much prefer parted to fdisk. It defaults to readable numbers, and it can understand gpt partitions.

---

### Post by Mark_in_Hollywood on 2014-04-04
Too many variables (512, 1K, 4K) have confused me in into wasting your invaluable time. Please accept my apology. Many thanks for your support.

---

### Post by The Cog on 2014-04-04
Hey, don't think you need to apologise. Everybody learns by asking questions (and reading these forums). And anyway, I get a warm feeling if I think I've helped someone.

---

