---
title: "Partitions possibly not mounting???"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2012-06-19
Just installed Ubuntu 12.04 with an encrypted home partition. On boot, prior to the log-in screen, I get a warning along the lines of a disk drive is not ready or present (with an UUID number), and it then tells me to either wait or press some key combo to sort the problem out manually.

Generally, I do nothing and it moves on to the log-in screen within seconds.

Curious, I did a quick check to see whether everything's working as it should.

> ls -A /home
.ecryptfs  melchizedek

Which seems to confirm the home folder is encrypted. I then did a...
> 
sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1b751b74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31021514    15510726    7  HPFS/NTFS/exFAT
/dev/sda2        31021576   488392064   228685244+   5  Extended
/dev/sda5        31021578    72163979    20571201   83  Linux
/dev/sda6        72164043   256477724    92156841   83  Linux
/dev/sda7       256477788   262614554     3068383+  83  Linux
/dev/sda8       262614618   488392064   112888723+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   308656844   154328391    7  HPFS/NTFS/exFAT
/dev/sdb2       308656845   452968739    72155947+   7  HPFS/NTFS/exFAT
/dev/sdb3       452968740   976768064   261899662+   5  Extended
/dev/sdb5       452968803   596493449    71762323+   7  HPFS/NTFS/exFAT
/dev/sdb6       596493513   700691039    52098763+   7  HPFS/NTFS/exFAT
/dev/sdb7       700691103   803394584    51351741    7  HPFS/NTFS/exFAT
/dev/sdb8       803394648   976768064    86686708+   7  HPFS/NTFS/exFAT

Disk /dev/mapper/cryptswap1: 3142 MB, 3142024704 bytes
255 heads, 63 sectors/track, 381 cylinders, total 6136767 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x33412deb

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

My question is... how can I find out whether I have a working swap partition or not?

---

### Post by Kakers on 2012-06-19
Hi SpongeBob,

I get the same thing with my encrypted home partition, it just takes a little while for the encrypted partition to mount, you'll notice it disappears once it does. If you're able to log in Ok then I wouldn't worry.

If you wish to see how much swap you have available you can use the 'free -m' command.

Everything sounds like it's probably fine ;)

---

### Post by SpongeBob SquarePants on 2012-06-19
Hi Kakers,

> free -m
             total       used       free     shared    buffers     cached
Mem:          2012        972       1039          0         20        437
-/+ buffers/cache:        515       1497
Swap:            0          0          0


Does the above suggest I have no swap?

---

### Post by Kakers on 2012-06-19
I would say yes lol, what do you have in your fstab? (/etc/fstab)
Did you allocate swap space during the installation?

Looking at your fdisk list it looks like you may have not added swap space.

Here is mine:

```

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f531

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     3905535     1951744   82  Linux swap / Solaris
/dev/sdb2   *     3905536   312580095   154337280   83  Linux

Disk /dev/mapper/cryptswap1: 1998 MB, 1998585856 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff0c5bdf

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

---

### Post by SpongeBob SquarePants on 2012-06-19
Yes, I did alloacte a swap partition. 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=68502c21-07ec-48bf-bcf9-0222f1929dd9	/	reiserfs	notail	0	1
#Entry for /dev/sda6 :
UUID=b2ffeb3d-72af-4498-a983-ed24c7383c81	/home	reiserfs	defaults	0	2
#Entry for /dev/sdb2 :
UUID=7C4E91931FB789D8	/media/Archives	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb1 :
UUID=1FE78CC5354CF414	/media/Audio	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb8 :
UUID=74C0A9D0654C02BB	/media/Video	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/mapper/cryptswap1 :
UUID=34bde6d6-dfe3-417c-a295-b9a7db5ac66b	none	swap	sw	0	0

#UUID=c9fd96b1-4110-4276-9b2e-ec01a7839d7d	none	swap	sw	0	0



---

### Post by Kakers on 2012-06-19
Odd, don't see it there.

sda5 - / (reiserfs)
sda6 - /home (reiserfs)

sdb1
sdb2 - Media
sdb8

Are you able to see it on the disk using gparted? (when not using a live cd it comes up as unknown for me)

---

### Post by SpongeBob SquarePants on 2012-06-19
Same in mine...

---

### Post by Kakers on 2012-06-19
Humm not too sure, you could try 'mountall -v' it will fail but if you run it without sudo, you'll at least be able to see any error messages without actually doing anything to your system

---

### Post by critin on 2012-06-19
Did you click on the red exclamation points on sda/7 & 8 to see what the error is?

---

### Post by SpongeBob SquarePants on 2012-06-19
> File System: unknown
Size: 2,94 GiB

Path: /dev/sda7
Status: Not mounted
Label:
UUIOD:

Warning: unable to detech file system. Possible reason are:

-- The File System is damaged
-- The file system is unknown to gParted
-- There is no file system available
-- The device entry /dev/sda7 is missing.

I think I'm going to try formatting the partition and then rebooting. I'll report back when I'm done.

---

### Post by SpongeBob SquarePants on 2012-06-19
Okay, it wouldn't format from within Ubuntu, so I ran the live distro and sorting it from there. No warning at bootup... so obviously, that's good news. I'm still not sure I have a working swap, however.

> free -m
             total       used       free     shared    buffers     cached
Mem:          2012        753       1259          0         10        376
-/+ buffers/cache:        365       1646
Swap:            0          0          0

And...

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=68502c21-07ec-48bf-bcf9-0222f1929dd9	/	reiserfs	notail	0	1
#Entry for /dev/sda6 :
UUID=b2ffeb3d-72af-4498-a983-ed24c7383c81	/home	reiserfs	defaults	0	2
#Entry for /dev/sdb2 :
UUID=7C4E91931FB789D8	/media/Archives	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb1 :
UUID=1FE78CC5354CF414	/media/Audio	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/sdb8 :
UUID=74C0A9D0654C02BB	/media/Video	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0
#Entry for /dev/mapper/cryptswap1 :
UUID=34bde6d6-dfe3-417c-a295-b9a7db5ac66b	none	swap	sw	0	0

#UUID=c9fd96b1-4110-4276-9b2e-ec01a7839d7d	none	swap	sw	0	0

Any ideas?

---

### Post by SpongeBob SquarePants on 2012-06-19
Okay, this is weird... although I formatted using the live distro, and it showed up as a valid linux swap, and said everything was fine, in my hard drive installation (despite there being no warning message on boot) it still has an exclamation mark next to it. Currently, I can think of doing two things:

1. Deleting the partition altogether, recreating it, and then formatting it.

2. Creating a second swap in the unallocated space at the end of the disk. Would it then be possible to instruct ubuntu to use that?

---

### Post by SpongeBob SquarePants on 2012-06-19
Sorted. Unfortunately, I had to do a full reinstall... including a partition wipe and rebuild. There was an issue with one of my partitions, and the only way I could fix it was to start again from scratch. 

Thanks for the help though, guys. Without you, I wouldn't have even known what the problem was :-)

---

