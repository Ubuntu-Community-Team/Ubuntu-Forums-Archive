---
title: "How To: Correctly Shrink, Enlarge, and Merge ext3 Partitions"
date: 2009-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by BslBryan on 2009-05-29
Hello, everyone. :-)  I have seen thousands of posts that look like this:[QUOTE=Example User]I tried out Windows 7, but I didn't care for it, so I deleted the partition it was on to devote my HD to Ubuntu.  Now, it leaves me with 200GB for Ubuntu, and 50GB as unallocated disk space.  GParted doesn't let me merge the two together.  What do I do? [/QUOTE]

And that post is usually unanswered.  Nobody really knows how to do that.  **Until today!**
[B]
This tutorial will show you how to shrink, enlarge, and merge existing ext3 partitions.  You should not have any corrupted data.[/B] 

**[COLOR="Red"]THIS TUTORIAL IS NOT VERY BEGINNER-FRIENDLY.  I do not guarantee that this tutorial will work for you as it has for me.  Before going any further, backup your system, and read over my tutorial, making sure that you are comfortable with all of these commands.  Messing with partitions is dangerous work, and even if done correctly can leave you with a GRUB error or two.[/COLOR]**
 
I know I will get bashed for this, but the commands in this tutorial should be run as root.  **[COLOR="Red"]I DO NOT RECOMMEND BECOMING ROOT FOR MORE THAN ONE COMMAND UNLESS IN VERY SPECIFIC CASES.[/COLOR]**  Become root by opening up your favorite shell and typing:

```
sudo su
```
[B]
Also, this is just an example.  You might need to change words in a command, etc. so it will work for you.  Do not go messing around with /dev/sda3 if /dev/sda3 does not exist![/B]

This is an Ubuntu desktop that has every file in one large partition (10 GB, device /dev/sda1). The partitioning looks like this:

```
df -h

```

[I]```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.5G  4.1G  4.9G  46% /
varrun                 94M  132K   94M   1% /var/run
varlock                94M     0   94M   0% /var/lock
udev                   10M   52K   10M   1% /dev
devshm                 94M     0   94M   0% /dev/shm
lrm                    94M   18M   77M  19% /lib/modules/2.6.17-10-generic/volatile

```[/I]

**The partition to be resized must be unmounted when we do the resizing**; obviously _this is impossible if this is the partition that holds all important system files_ like in this example.  **We can do it, though, but we need to have an Ubuntu LiveCD to boot from. **

*If the partition that you want to resize doesn't hold any system files, like  /home partitions, backup partitions, etc., you don't need a Live-CD, because all of the steps can be run from the original system.*

**[COLOR="Red"]If you want to resize partitions on production systems, _please_ back up your data before, because it is possible you lose all your data if you don't calculate the size of your new partition correctly!!![/COLOR]** 

In this tutorial, we will resize /dev/sda1. [I]If your partition is named differently, please replace /dev/sda1 with your own device.
[/I]
 
So, let's begin.  **First, let's learn about shrinking partitions.**  In this example, I will shrink /dev/sda1.

The first thing you need to do is get some information on your system.  Run

```
df
```
And you should see an output similar to

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              9859036   4234908   5123304  46% /
varrun                   95480       132     95348   1% /var/run
varlock                  95480         0     95480   0% /var/lock
udev                     10240        52     10188   1% /dev
devshm                   95480         0     95480   0% /dev/shm
lrm                      95480     17580     77900  19% /lib/modules/2.6.17-10-generic/volatile
```
Then run
```

df -B 4k
```
Again, you should see something like

```
Filesystem           4K-blocks      Used Available Use% Mounted on
/dev/sda1              2464759   1058727   1280826  46% /
varrun                   23870        33     23837   1% /var/run
varlock                  23870         0     23870   0% /var/lock
udev                      2560        13      2547   1% /dev
devshm                   23870         0     23870   0% /dev/shm
lrm                      23870      4395     19475  19% /lib/modules/2.6.17-10-generic/volatile
```

Then, run
```

df -h
```
You will see something like

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.5G  4.1G  4.9G  46% /
varrun                 94M  132K   94M   1% /var/run
varlock                94M     0   94M   0% /var/lock
udev                   10M   52K   10M   1% /dev
devshm                 94M     0   94M   0% /dev/shm
lrm                    94M   18M   77M  19% /lib/modules/2.6.17-10-generic/volatile

```
Then, run a 
```
fdisk -l
```

```

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1247    10016496   83  Linux
/dev/sda2            1248        1305      465885    5  Extended
/dev/sda5            1248        1305      465853+  82  Linux swap / Solaris

```
Then, 
```
fdisk -s /dev/sda1
```
You will see something like
```
10016496
```

Then we shut down the system and boot into the LiveCD.  **If the partition you want to resize doesn't hold any system files, you can do everything from the original system; the steps are the same, just omit booting into the LiveCD.**
```

reboot now
```

After Ubuntu has booted, open a terminal and become root.

```
sudo su
```

/dev/sda1 should be unmounted by default, but you can run

```
umount /dev/sda1
```

to be safe. Then, run

```
fsck -n /dev/sda1
```

The output looks like this:

```
fsck 1.38 (20-Apr-2009)
e2fsck 1.38 (20-Apr-2009)
/dev/sda1: clean, 159037/1254176 files, 1095299/2504124 blocks
```


Now, run

```
e2fsck -f /dev/sda1
```

```
e2fsck 1.38 (20-Apr-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 164178/1254176 files (0.6% non-contiguous), 1051617/2504124 blocks
```

Now we resize our filesystem with resize2fs. 

Currently, 4.1GB are used on /dev/sda1 (see the df -h output above), So it's safe to shrink it from 10GB to about 6GB.  **[COLOR="Red"]If you make it smaller than 4.1GB, you will lose data.[/COLOR]** 

Now, we run
```
resize2fs /dev/sda1 6000M
```

The output is:

```
resize2fs 1.38 (20-Apr-2009)
Resizing the filesystem on /dev/sda1 to 1536000 (4k) blocks.
The filesystem on /dev/sda1 is now 1536000 blocks long.
```

**_[COLOR="Red"]Write down the amount of blocks (1536000) and their size (4k). We need that soon.[/COLOR]_**

Now we delete the /dev/sda1 partition (no data will be lost) and create a new, smaller one.  **Make certain it is still big enough, though!**  We can do this with fdisk:

```
fdisk /dev/sda
```

**Now, it's /dev/sda, not /dev/sda1.**

```
The number of cylinders for this disk is set to 1305.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
```

To get a list of all commands, type
```
m
```
You will see:

```
Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)
```

Now, let's delete partition no. 1 (/dev/sda1):

```
Command (m for help): d
Partition number (1-5): 1
```

Next we create a new /dev/sda1 partition. It was a primary partition before, so we choose p again, and again it is our partition no. 1:

```
Command (m for help): n
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
p
Partition number (1-4): 1
```

Now comes the most important part.  We are asked about the size of the new partition. The first cylinder is no problem, it is the one from the fdisk -l output at the beginning of the tutorial.
```

First cylinder (1-1305, default 1): 1
```

**But we don't have a value for the last cylinder of our new partition.** Fortunately, we can specify the size in kilobytes (K), so we calculate the size like this:

We multiply the amount of blocks from the resize2fs output (1536000) by the size of a block (4k), and to make certain the partition is big enough, we add 3 to 5% to it.  3 should be enough, but if you want to be *really* safe, go with 5%.
```
1536000 * 4k * 1.03 = 6328320k

```
So we prepend that value with a + sign and replace the small k with a capital one (K) and enter it:

```
Last cylinder or +size or +sizeM or +sizeK (1-1247, default 1247): +6328320K
```

Our original /dev/sda1 had the bootable flag (see the fdisk -l output from the beginning of this chapter), so we must add it to our new /dev/sda1 again:

```
Command (m for help): a
Partition number (1-5): 1
```

Now let's write our new partition table and exit fdisk:

```
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

Now we reboot the system, and again we boot into our LiveCD (unless your resized partition doesn't contain system files.  In this case, just reboot.)

```
reboot now
```

Become root again. 
```
sudo su
```

and then run this:

```
fsck -n /dev/sda1
```

The output should look like this:

```
fsck 1.38 (20-Apr-2009)
e2fsck 1.38 (20-Apr-2009)
/dev/sda1: clean, 159036/765536 files, 1047239/1536000 blocks
```

Then we create the journal on our new /dev/sda1, thus turning it into an ext3 partition again:

```
tune2fs -j /dev/sda1
```

```
tune2fs 1.38 (20-Apr-2009)
Creating journal inode: done
This filesystem will be automatically checked every 30 mounts or
0 days, whichever comes first. Use tune2fs -c or -i to override.
```

Now we are done. :-) Shut down the system and boot into the original system:
```
sudo reboot now
```

If everything went well, the original system will boot up, and no data has been lost. Now we can gather some details about our new partitioning and compare them with the information we collected at the beginning of the tutorial:

```
df
```

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              6047868   4224140   1639408  73% /
varrun                   95480       132     95348   1% /var/run
varlock                  95480         0     95480   0% /var/lock
udev                     10240        52     10188   1% /dev
devshm                   95480         0     95480   0% /dev/shm
lrm                      95480     17580     77900  19% /lib/modules/2.6.17-10-generic/volatile
```

```
df -B 4k
```
```

Filesystem           4K-blocks      Used Available Use% Mounted on
/dev/sda1              1511967   1056035    409852  73% /
varrun                   23870        33     23837   1% /var/run
varlock                  23870         0     23870   0% /var/lock
udev                      2560        13      2547   1% /dev
devshm                   23870         0     23870   0% /dev/shm
lrm                      23870      4395     19475  19% /lib/modules/2.6.17-10-generic/volatile
```
```

df -h
```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.8G  4.1G  1.6G  73% /
varrun                 94M  132K   94M   1% /var/run
varlock                94M     0   94M   0% /var/lock
udev                   10M   52K   10M   1% /dev
devshm                 94M     0   94M   0% /dev/shm
lrm                    94M   18M   77M  19% /lib/modules/2.6.17-10-generic/volatile
```

```
fdisk -l
```

```

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         789     6337611   83  Linux
/dev/sda2            1248        1305      465885    5  Extended
/dev/sda5            1248        1305      465853+  82  Linux swap / Solaris
```

```
fdisk -s /dev/sda1
```
```
6337611
```

All right!  We did it. \\:D/ We shrunk a partition, without corruption or loss of data.  Now, let's take a crack at **enlarging An ext3 Partition.**

In this example we have a /dev/sda1 partition with about 6GB, and right behind that partition we have 4GB of unallocated space. We want to add those 4GB of unused spave to our /dev/sda1 partition. **This doesn't work if these 4GB don't come right behind our /dev/sda1 partition.**

First, we collect some details again about our current partitioning:
```

df
```

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              6047868   4224140   1639408  73% /
varrun                   95480       132     95348   1% /var/run
varlock                  95480         0     95480   0% /var/lock
udev                     10240        52     10188   1% /dev
devshm                   95480         0     95480   0% /dev/shm
lrm                      95480     17580     77900  19% /lib/modules/2.6.17-10-generic/volatile
```

```
df -B 4k
```

```
Filesystem           4K-blocks      Used Available Use% Mounted on
/dev/sda1              1511967   1056035    409852  73% /
varrun                   23870        33     23837   1% /var/run
varlock                  23870         0     23870   0% /var/lock
udev                      2560        13      2547   1% /dev
devshm                   23870         0     23870   0% /dev/shm
lrm                      23870      4395     19475  19% /lib/modules/2.6.17-10-generic/volatile
```
```

df -h
```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.8G  4.1G  1.6G  73% /
varrun                 94M  132K   94M   1% /var/run
varlock                94M     0   94M   0% /var/lock
udev                   10M   52K   10M   1% /dev
devshm                 94M     0   94M   0% /dev/shm
lrm                    94M   18M   77M  19% /lib/modules/2.6.17-10-generic/volatile
```
```

fdisk -l
```


```
Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         789     6337611   83  Linux
/dev/sda2            1248        1305      465885    5  Extended
/dev/sda5            1248        1305      465853+  82  Linux swap / Solaris

```
```
fdisk -s /dev/sda1
```

```
6337611
```

Then we shut down the system and boot into our LiveCD.  **If the partition you want to resize doesn't hold any system files, you can do everything from the original system.  The steps are the same, just omit booting into the LiveCD.**

```
sudo reboot now
```

After Ubuntu has booted, open a terminal and become root.
sudo su[/CODE]

/dev/sda1 should be unmounted by default, but you can run
```

umount /dev/sda1
```

to be safe.

Then run

```
fsck -n /dev/sda1
```

```
fsck 1.38 (20-Apr-2009)
e2fsck 1.38 (20-Apr-2009)
/dev/sda1: clean, 159036/765536 files, 1080014/1536000 blocks
```


Now we use fdisk to delete our current /dev/sda1 partition and create a bigger one. No data will be lost.
```

fdisk /dev/sda
```
**Now, it is not /dev/sda1, but /dev/sda.**

```
The number of cylinders for this disk is set to 1305.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
```

To get a list of all commands, type
```
m
```

```
Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)
```

Let's print out the partition table:

```
Command (m for help): p

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         789     6337611   83  Linux
/dev/sda2            1248        1305      465885    5  Extended
/dev/sda5            1248        1305      465853+  82  Linux swap / Solaris
```

Now we delete partition no. 1 (/dev/sda1):

```
Command (m for help): d
Partition number (1-5): 1
```

Next we create a new /dev/sda1 partition. It was a primary partition before, so we choose p again, and again it is our partition no. 1:

```
Command (m for help): n
Command action
   l   logical (5 or over)
   p   primary partition (1-4)
p
Partition number (1-4): 1
```

Now we must specify the first and the last cylinder of our new /dev/sda1 partition. We know the first cylinder, can can take it from the fdisk -l output before:

```
First cylinder (1-1305, default 1): 1

```
Now fdisk tells us the highest possible cylinder of our new partition (1247 in this example), so we simply enter this number:

```
Last cylinder or +size or +sizeM or +sizeK (1-1247, default 1247): 1247
```

Let's print out our new partition table:

```
Command (m for help): p

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1247    10016496   83  Linux
/dev/sda2            1248        1305      465885    5  Extended
/dev/sda5            1248        1305      465853+  82  Linux swap / Solaris
```

Our original /dev/sda1 had the bootable flag (see the fdisk -l output from the beginning of the tutorial), so we must add it to our new /dev/sda1 again:

```
Command (m for help): a
Partition number (1-5): 1
```

Now let's write our new partition table and exit fdisk:

```
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

Now we reboot the system, and again we boot into our LiveCD.  If you are using your original system, because the resized partition doesn't hold system files, simply reboot. 

```
reboot now
```

Open a terminal, and become root.

```
sudo su
```

Then run

```
e2fsck -f /dev/sda1
```

Now we must resize the filesystem in our /dev/sda1 partition. If we don't specify a size for the resize2fs command, it will assume the biggest possible size so we don't have to calculate. So we run

```
resize2fs /dev/sda1
```

The output looks like this:

```
resize2fs 1.38 (20-Apr-2009)
Resizing the filesystem on /dev/sda1 to 2504124 (4k) blocks.
The filesystem on /dev/sda1 is now 2504124 blocks long.
```

Next we run

```
fsck -n /dev/sda1
```

```
fsck 1.38 (20-Apr-2009)
e2fsck 1.38 (20-Apr-2009)
/dev/sda1: clean, 159036/1254176 files, 1062544/2504124 blocks
```

and create the journal on /dev/sda1, turning it into an ext3 partition again:

```
tune2fs -j /dev/sda1

```
```
tune2fs 1.38 (20-Apr-2009)
Creating journal inode: done
This filesystem will be automatically checked every 30 mounts or
0 days, whichever comes first. Use tune2fs -c or -i to override.
```

Now we're finished. :-)  Shut down the computer, and eject the LiveCD, booting into your original system.

```
sudo reboot now
```

If everything went well, the original system will boot up, and no data has been lost. Now we can gather some details about our new partitioning and compare them with the information we collected at the beginning of this tutorial:
```

df
```

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              9859036   4224032   5234348  45% /
varrun                   95480       132     95348   1% /var/run
varlock                  95480         0     95480   0% /var/lock
udev                     10240        52     10188   1% /dev
devshm                   95480         0     95480   0% /dev/shm
lrm                      95480     17580     77900  19% /lib/modules/2.6.17-10-generic/volatile
```

```
df -B 4k
```

```
Filesystem           4K-blocks      Used Available Use% Mounted on
/dev/sda1              2464759   1056008   1308587  45% /
varrun                   23870        33     23837   1% /var/run
varlock                  23870         0     23870   0% /var/lock
udev                      2560        13      2547   1% /dev
devshm                   23870         0     23870   0% /dev/shm
lrm                      23870      4395     19475  19% /lib/modules/2.6.17-10-generic/volatile
```

```
df -h
```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.5G  4.1G  5.0G  45% /
varrun                 94M  132K   94M   1% /var/run
varlock                94M     0   94M   0% /var/lock
udev                   10M   52K   10M   1% /dev
devshm                 94M     0   94M   0% /dev/shm
lrm                    94M   18M   77M  19% /lib/modules/2.6.17-10-generic/volatile
```

```
fdisk -l
```


```
Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1247    10016496   83  Linux
/dev/sda2            1248        1305      465885    5  Extended
/dev/sda5            1248        1305      465853+  82  Linux swap / Solaris
```

```
fdisk -s /dev/sda1
```
```
10016496
```

**Finally, let's talk about merging partitions! **

In this example, the 6GB /dev/sda1 partition is followed directly by the 4GB /dev/sda3 partition on the hard disk. /dev/sda3 is mounted to the /data directory and doesn't hold files needed by the Linux system, just user data. The current partitioning looks like this:

```
df -h
```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.8G  4.1G  1.6G  73% /
varrun                 94M  132K   94M   1% /var/run
varlock                94M     0   94M   0% /var/lock
udev                   10M   56K   10M   1% /dev
devshm                 94M     0   94M   0% /dev/shm
lrm                    94M   18M   77M  19% /lib/modules/2.6.17-10-generic/volatile
/dev/sda3             3.5G   72M  3.3G   3% /data
```

**[COLOR="Red"]To merge /dev/sda1 and /dev/sda3, we have to delete /dev/sda3 and then enlarge /dev/sda1 as described in the previous section of this tutorial. This means that all data on /dev/sda3 will be lost, so if you need it later on please back it up somewhere else and then restore it to the new and bigger /dev/sda1 afterwards![/COLOR]**

So, we open /etc/fstab and remove the line for /dev/sda3 there if it exists:

```
vi /etc/fstab
```

The new file without /dev/sda3 could look like this:

```
# /etc/fstab: static file system information.
#
#                
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=566fd9e9-098f-4aae-9908-51efe171d8ba /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=82102b65-35db-469a-9532-03d619d8cffb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

Then we unmount /dev/sda3 and run fdisk to delete it. This can still be done on the original system as /dev/sda3 doesn't contain system files:

```
umount /dev/sda3
```

```
fdisk /dev/sda
```
[B]
Now, it's /dev/sda, not /dev/sda1.[/B]

```
The number of cylinders for this disk is set to 1305.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
```

To get a list of all commands, type
```
m
```
```
Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)
```

Now, let's delete /dev/sda3:

```
Command (m for help): d
Partition number (1-5): 3
```

Afterwards, we write the new partition table to the disk:

```
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

Now we reboot the system:

```
sudo reboot now
```

and boot into our LiveCD.  [B]From here onward, the steps are identical to those in the "Enlarging partitions" section, beginning with
[/B]
```
sudo su
```

```
umount /dev/sda1
```

So, simply scroll, up, and you'll have two merged partitions in no time at all. :-)  

I sincerely hope I've helped you all.  This tutorial has definitely helped me out, as I was tired of having a 35.4 GB empty partition!

Best to everybody, and good luck.

---

### Post by wieman01 on 2009-05-29
Good one! Hope you'll continue to support this thread. :-)

---

### Post by BslBryan on 2009-05-29
Thanks a lot.  I'm eager to hear how it works for others. :-)

---

### Post by -kg- on 2009-05-30
> THIS TUTORIAL IS NOT VERY BEGINNER-FRIENDLY.

You got that right!

You know how computers are...one little mis-typed letter or number can totally FUBAR everything, and the more steps you have in a process the more opportunity you have to do so.

Wouldn't it be a lot easier to boot on to the Live CD and run GPartEd from the "System/Administration/Partition Editor" selection?  GPartEd automates most of the many steps you have in your post and eliminates the many file system checks, as well, as it is all taken care of in the program.  And if you want to have a dedicated GPartEd distribution, you can download the GPartEd Live CD from Sourceforge.

I have (re-)written a nice tutorial in the Community Wiki that covers the use of GPartEd (and really, many other GUI-based partition editors, since they basically operate the same) and partitioning operations that you may want or need to perform.  The link is in my signature block.

As far as merging partitions, you aren't actually merging them.  You're just copying the data off the data partition, deleting it, enlarging the main partition, then copying the data back on to the main partition, assumably into a /data directory, which you of course will need to mount to access that data in the same way.

And the original question:

>  Originally Posted by Example User
I tried out Windows 7, but I didn't care for it, so I deleted the partition it was on to devote my HD to Ubuntu. Now, it leaves me with 200GB for Ubuntu, and 50GB as unallocated disk space. GParted doesn't let me merge the two together. What do I do?

The way I read this question, he has 200GB for Ubuntu and 50 GB of free space.  You can't merge a partition with free space...you expand into it (as long as the free space is not encompassed by an Extended partition, of course) by resizing the 200 GB partition.  Most all this information is contained in my WIKI page.

I don't know...just a suggestion.  I try to catch as many of these partitioning problems as I can, but I'm not retired yet and can't spend as much time as I'd like to.

---

### Post by BslBryan on 2009-05-30
That's precisely why I wrote this tutorial, -kg-. :-)

You see, I did this because I had a 35 GB partition that I couldn't merge with the other partition on my machine.  So, since it was unallocated, I wanted to delete it, and make the first one larger.  The thing is, GParted wouldn't let me delete it, because it was unallocated space.  So, I made it swap space or something, and then deleted it, so I could resize the first.  Well, guess what?  The partition was again called "unallocated space" and I couldn't do anything with it.

Also, search the forums for the same problem as the example quote.  What you'll see is a lot of people trying to help, but as soon as the person gets into GParted, or follows one instruction, they find that they can't complete the others.  They haven't done anything wrong, but the program wouldn't let them do what they had to do.

I have used the LiveCD to run GParted to fix my problem from Hardy to Jaunty, and none of them worked.

This did. :-)
EDIT: Also,
> **-kg- said:**
> 
The way I read this question, he has 200GB for Ubuntu and 50 GB of free space.  You can't merge a partition with free space...you expand into it (as long as the free space is not encompassed by an Extended partition, of course) by resizing the 200 GB partition.  Most all this information is contained in my WIKI page.
Read my tutorial, and go to the section where it talks about merging partitions.  This didn't get accepted because I don't know what I'm talking about. ;-)

Regards!

---

### Post by dcstar on 2009-05-31
> **BslBryan said:**
> That's precisely why I wrote this tutorial, -kg-. :-)

You see, I did this because I had a 35 GB partition that I couldn't merge with the other partition on my machine.  So, since it was unallocated, I wanted to delete it, and make the first one larger.  The thing is, GParted wouldn't let me delete it, because it was unallocated space.  So, I made it swap space or something, and then deleted it, so I could resize the first.  Well, guess what?  The partition was again called "unallocated space" and I couldn't do anything with it.
.........

I have successfully used gparted for all partition shrinking/expansion/deleting/whatever since Ubuntu 4.10.

You cannot delete "unallocated space" because there is nothing to delete - it is "unallocated" and available to be used for a new partition (if there is space for one) or to expand an existing partition into.

The only problems I seem to see (in these forums) from people using gparted is due to their lack of understanding on how to use it.

---

### Post by wieman01 on 2009-05-31
I own a server and cannot use GParted for the very reason that I don't have a DE. So I'll probably use this guide next time I have to resize my partitions.

---

### Post by -kg- on 2009-05-31
> **wieman01 said:**
> I own a server and cannot use GParted for the very reason that I don't have a DE. So I'll probably use this guide next time I have to resize my partitions.

Ah, but you *can* download the [GPartEd Live CD]("http://gparted.sourceforge.net/") and boot to that to do your partitioning.  That, or if you have a regular desktop Ubuntu Live CD, you can boot to that.

> I have successfully used gparted for all partition shrinking/expansion/deleting/whatever since Ubuntu 4.10.


And while I haven't used GPartEd that long, I *have* used other partition editors (specifically Partition Magic, but others as well) for the last 15 years or so.  I know what you mean.

> You cannot delete "unallocated space" because there is nothing to delete - it is "unallocated" and available to be used for a new partition (if there is space for one) or to expand an existing partition into.


Exactly, and this is all explained in my Wiki page and what I try to explain to people when I come across their posts (among other things! :p )

> The only problems I seem to see (in these forums) from people using gparted is due to their lack of understanding on how to use it.

Which is exactly (upon coming upon the old "How To Partition" page) why I re-wrote the page with a little more (actually, a *lot* more) detail and explanation.  I think I did a good job, but every once in a while I come upon a situation that stumps even me.  Of course, it's very difficult to diagnose a problem at a distance and through description.  I generally know what I'm looking at; other people don't.

> EDIT: Also,
Quote:

[QUOTE]The way I read this question, he has 200GB for Ubuntu and 50 GB of free space. You can't merge a partition with free space...you expand into it (as long as the free space is not encompassed by an Extended partition, of course) by resizing the 200 GB partition. Most all this information is contained in my WIKI page.

Read my tutorial, and go to the section where it talks about merging partitions. This didn't get accepted because I don't know what I'm talking about. [/QUOTE]

Oh, I definitely wouldn't say that.  You obviously know what you're doing, and I never did (nor would) say that you didn't.  It's just that your method is long, drawn out, complicated, and mistake prone for someone that *doesn't,* not to mention that there's an easier way to do it (once you learn the basic concepts and how to use the software).

---

### Post by BslBryan on 2009-06-01
-kg-, I see that you're trying to advocate your way of doing things.  And that's fine.  Please, though, stop preaching your wiki page.  Let's say, for all intents and purposes, that this tutorial is solely for the people who hate GParted and would prefer to do everything in a shell.

Linux is about choice.  Even if your way is better, let's let exist more than one option. ;)

---

### Post by wieman01 on 2009-06-01
> **BslBryan said:**
> -kg-, I see that you're trying to advocate your way of doing things.  And that's fine.  Please, though, stop preaching your wiki page.  Let's say, for all intents and purposes, that this tutorial is solely for the people who hate GParted and would prefer to do everything in a shell.
Yes, I am in favor of it as well. Let's move on from here and see how this tutorial goes. This discussion doesn't bring anymore benefit.

---

### Post by wieman01 on 2009-06-01
> **-kg- said:**
> Ah, but you *can* download the [GPartEd Live CD]("http://gparted.sourceforge.net/") and boot to that to do your partitioning.  That, or if you have a regular desktop Ubuntu Live CD, you can boot to that.
Like I said, it's a server and it doesn't even have a display. You can only SSH into it. Tough luck.

---

### Post by unutbu on 2009-06-01
Hi BslBryan, thank you for taking the time to write this tutorial! 

Just out of curiosity, what is your reason for believing that resize2fs can not handle ext3 partitions? I'm not saying you are wrong, just wondering if I have been doing (and recommending) something dangerous without knowing.

According to the resize2fs man page:
```

       The  resize2fs program will resize ext2 or ext3 file systems. 

```

---

### Post by BslBryan on 2009-06-01
Oh, thanks!  I've been using it for a long time, so I never knew that newer versions could handle ext3.

I'll update the tutorial.  Thanks a lot!

EDIT: Updated.  If there are any problems with this in practice, I can always write that part back in, I suppose, as I have never tested keeping it as ext3.  IMO, it seems marginally safer to just keep ext3, and making it ext2 would just be a waste of time.  Let's just hope it works. ;-)

---

