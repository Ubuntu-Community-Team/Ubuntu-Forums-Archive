---
title: "Can't rename file names in nautilus."
date: 2011-10-21
forum: New to Ubuntu
---

### Post by zzal_cn on 2011-10-21
Hi, I've updated to ubuntu 11.10 recently, all works fine but some weired malfunction in nautilus. The file manager can not rename any file in NTFS partitions(the Linux partition is fine), it's not a permission problem because I'm in the group with all the needed privileges.
Can somebody tell me how to solve this problem! Thanks.

PS:the ntfs partition auto mount function is realized by using 'NTFS configuration tool'.

---

### Post by bhaveshnande on 2011-10-21
I think its not a nautilis malfunction. You cannot rename a partition until you format it.

---

### Post by zzal_cn on 2011-10-21
Is there an method can work around this problem with reformat the partition. My windows partitions are very big and it's a lot of work backing up all the data and reformat.

---

### Post by gsmanners on 2011-10-21
Actually, ntfslabel can bestow a "name" on your NTFS drives (no need for formatting). I just get the feeling that your drive was mounted read-only somehow.

---

### Post by coffeecat on 2011-10-21
@zzal_cn, can you confirm that you are trying to rename files in the NTFS partition, and not relabel the partition? This is how I read your post. If you are simply trying to rename files, you do not need to reformat the partition.

Anyway, assuming I've read you correctly, I think this may be the basis of the problem:

> **zzal_cn said:**
> 
PS:the ntfs partition auto mount function is realized by using 'NTFS configuration tool'.

Is that ntfs-config? That application is out-of-date, unmaintained and does strange things at times. Open a terminal, and post the output of these three commands:

```
sudo fdisk -lu
sudo blkid
cat /etc/fstab

```

You can highlight the output with the mouse, right-click and "copy" and then paste into your post.

---

### Post by zzal_cn on 2011-10-21
> **coffeecat said:**
> @zzal_cn, can you confirm that you are trying to rename files in the NTFS partition, and not relabel the partition? This is how I read your post. If you are simply trying to rename files, you do not need to reformat the partition.

Anyway, assuming I've read you correctly, I think this may be the basis of the problem:



Is that ntfs-config? That application is out-of-date, unmaintained and does strange things at times. Open a terminal, and post the output of these three commands:

```
sudo fdisk -lu
sudo blkid
cat /etc/fstab

```You can highlight the output with the mouse, right-click and "copy" and then paste into your post.

Sorry for ambiguity in the question. What i am trying to do is rename the files in ntfs partitions within nautilus file manager, and ntfs-config is the tool i used to modify the /etc/fstab.
Here is the output of the commands
cmd:sudo fdisk -lu
output
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x063a987e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   165763071    82778112    7  HPFS/NTFS/exFAT
/dev/sda3       165763072   411523071   122880000    7  HPFS/NTFS/exFAT
/dev/sda4       411525118   976771071   282622977    f  W95 Ext'd (LBA)
/dev/sda5       580347904   769091583    94371840    7  HPFS/NTFS/exFAT
/dev/sda6       769093632   976771071   103838720    7  HPFS/NTFS/exFAT
/dev/sda7       411525120   413523967      999424   82  Linux swap / Solaris
/dev/sda8       413526016   580333567    83403776   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4007 MB, 4007657472 bytes
5 heads, 32 sectors/track, 48921 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8064     7827455     3909696    b  W95 FAT32

cmd:sudo blkid
output
/dev/sda1: LABEL="M-gM-3M-;M-gM-;M-^_M-dM-?M-^]M-gM-^UM-^Y" UUID="62A040CAA040A5FF" TYPE="ntfs" 
/dev/sda2: LABEL="UB_VOL2" UUID="9A90BDB190BD946B" TYPE="ntfs" 
/dev/sda3: LABEL="UB_W7" UUID="D6388B49388B2817" TYPE="ntfs" 
/dev/sda5: LABEL="UB_VOL3" UUID="B5B328D232F92388" TYPE="ntfs" 
/dev/sda6: LABEL="UB_VOL4" UUID="0FD55659C9652066" TYPE="ntfs" 
/dev/sda7: UUID="b56186f2-305f-472a-a4f6-f781b8971d20" TYPE="swap" 
/dev/sda8: UUID="e73fe6ae-a36a-4dfc-a7e7-e062dcc456c2" TYPE="ext4" 
/dev/sdb1: LABEL="KINGSTON" UUID="80B5-2DC5" TYPE="vfat" 

cmd:cat /etc/fstab
output
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda8 :
UUID=e73fe6ae-a36a-4dfc-a7e7-e062dcc456c2    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda2 :
UUID=9A90BDB190BD946B    /media/UB_VOL2    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda5 :
UUID=B5B328D232F92388    /media/UB_VOL3    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda6 :
UUID=0FD55659C9652066    /media/UB_VOL4    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda3 :
UUID=D6388B49388B2817    /media/UB_W7    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda7 :
UUID=b56186f2-305f-472a-a4f6-f781b8971d20    none    swap    sw    0    0

PS: The sdb1 device is my use finger drive, and file renaming is fine in it.

---

### Post by coffeecat on 2011-10-21
@zzal_cn, I have to admit that I'm slightly mystified at the moment as to why you can't rename any files in your NTFS partitions. The /etc/fstab entries created by ntfs-config while not optimal should give you write access, which includes renaming files.

Questions:

Does this happen with all four mounted partitions, or just one?
Do you get an error message when you try to rename a file? If so, what?
Can you write to the NTFS partition(s) - that is, can you save files there?

A filesystem inconsistency in the NTFS filesystem would cause Ubuntu to mount it read-only, but this seems unlikely if this affects all four partitions. If you answer the above questions we can take it from there.

---

### Post by gsmanners on 2011-10-21
> **zzal_cn said:**
> 
cmd:sudo blkid
output
/dev/sda1: LABEL="M-gM-3M-;M-gM-;M-^_M-dM-?M-^]M-gM-^UM-^Y" UUID="62A040CAA040A5FF" TYPE="ntfs" 
...

I'm just tossing this out there, but that is a mighty strange label for a drive.

---

### Post by coffeecat on 2011-10-21
> **gsmanners said:**
> I'm just tossing this out there, but that is a mighty strange label for a drive.

Agreed! :) It's about 105MB in size which would do for a Windows 7 boot partition, but that normally has the label "SYSTEM".

@zzal_cn, what version of Windows are you running?

---

### Post by zzal_cn on 2011-10-21
> **coffeecat said:**
> Agreed! :) It's about 105MB in size which would do for a Windows 7 boot partition, but that normally has the label "SYSTEM".

@zzal_cn, what version of Windows are you running?

That is the reserved disk space when i installed window 7 ultimate edition os, i don't know it's use.

And here are the answers for your three questions,
This problem happens in all my four mounted ntfs partition but the auto-mounted use finger drive.
I've tried to rename files in nautilus by using F2 key or right click menu way and nautilus accepted my input but filenames returned back to original version when renaming finished. Even weirder, i can change file names in command line with normal user account.
The write function in those is good, i can copy and delete files there within nautilus.

I just found out that this problem not only in my laptop (running oneiric ocelot) but also my desk-sit workstation (running oneiric ocelot) too, both devices' os are automatically upgraded from natty narwhal.

---

### Post by gsmanners on 2011-10-21
> **zzal_cn said:**
> ... both devices' os are automatically upgraded from natty narwhal.

"Upgraded"? Why am I not surprised? I'm really starting to hate that Update Manager (and I never even use it).

---

### Post by coffeecat on 2011-10-22
@zzal_cn, please give us some examples of the new names you are trying to apply. The filesystem is NTFS and there are some characters which are permitted in Linux filesystems but not in NTFS. I wonder if that might be the problem.

---

### Post by audeojude on 2011-10-22
I think my problem is related to what you have been seeing.

It seems to be a problem in ntfsprogs and the kernel. I have tried a couple kernels and no luck. Then I installed ntfs-3g which automatically un-installed and replaced ntfsprogs and my read write ability on my usb drives and even my ntfs sata drives came back.

so the solution was to go 

sudo apt-get install ntfs-3g 

allow it to uninstall ntfsprogs

it takes a while to un-install and install as it has to recompile a bunch of kernel drivers. I had upgraded to the latest stock 3.0.13 kernel in updates just before trying this.


what a pita though. in changing permissions and playing with settings I killed my ability to log into my user directory. I had to delete that and create a totally fresh user directory and then copy back into the new one all my data and application configurations. 

Mostly Ubuntu just works which is what I like. Years ago I loved digging under the hood and customising and tweaking. Nowadays I just want my applications and Internet to work.

---

### Post by coffeecat on 2011-10-22
> **audeojude said:**
> It seems to be a problem in ntfsprogs and the kernel. I have tried a couple kernels and no luck. Then I installed ntfs-3g which automatically un-installed and replaced ntfsprogs and my read write ability on my usb drives and even my ntfs sata drives came back.

FYI. The package ntfs-3g - which includes the ntfs userspace read-write driver - comes as default in Oneiric. You shouldn't have to install it, unless it has been previously uninstalled. In earlier versions of Ubuntu, you needed the package ntfsprogs for such utilities as ntfsfix, ntfslabel and so on. This is not needed in Oneiric as the package ntfs-3g now includes these utilities. Indeed, if you try to install ntfsprogs in Oneiric, it removes ntfs-3g, because the two now conflict. I believe some of the issues surrounding the absence of ntfs-3g in Oneiric are due to ntfsprogs being installed and the user not noticing that ntfs-3g is being removed.

Whatever, @audeojude, thanks for bringing this up - an interesting point. It's possible that the removal of ntfs-3g is causing the system to fall back to the old read-only ntfs kernel module. Just a theory.

@zzal_cn, check to see if you have the package ntfs-3g installed.

---

### Post by gsmanners on 2011-10-22
> **zzal_cn said:**
> This problem happens in all my four mounted ntfs partition but the auto-mounted use finger drive.
I've tried to rename files in nautilus by using F2 key or right click menu way and nautilus accepted my input but filenames returned back to original version when renaming finished. Even weirder, i can change file names in command line with normal user account.
The write function in those is good, i can copy and delete files there within nautilus.

I'm guessing Nautilus didn't quite "upgrade" right.

---

### Post by audeojude on 2011-10-22
My theory is that an upgrade put ntfsprogs back in and removed ntfs-3g.

serious pain caused by it. I can only imagine the number of people affected that haven't said anything on the forums or don't know how to troubleshoot it. I have seen at least 10 new threads started in the last week related to this though. To me that says a lot of people are dealing with it.

---

### Post by BillyBoa on 2011-10-24
I have the same problem with the following variation:
I cannot rename files on my NTFS drive BUT only in one directory. I tried to move the directory files to a newly created directory and I was able to rename the files. BUT after a few attempts the problem started again. The most complicated thing is that I have the same problem in my Ubuntu home/Download directory and only in this directory. All the permissions are correct in NTFS drive and in Download directory. Smells like bug to me.

---

