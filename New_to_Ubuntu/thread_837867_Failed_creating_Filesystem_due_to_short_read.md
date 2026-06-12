---
title: "Failed creating Filesystem due to short read"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by AegisTalons on 2008-06-22
Hey everyone,
So I have a 300 gig hard drive from an old external hard drive I put together. I just turned one of my old computers into an Ubuntu server. Anyways, it was initially formatted as a NTFS. I want to reformat it as ext3.

So I ran the following in command prompt: ```
sudo mkfs.ext3 /dev/sdb1
```

and the following was outputted from terminal:
```
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
18317312 inodes, 73258400 blocks
3662920 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
2236 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616

Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir
```

It fails to create the filesystem. Has anyone experienced this before. Also I ran badblocks on the whole drive and it didn't return any errors or bad blocks.

Any help would greatly be appreciated.

---

### Post by cariboo on 2008-06-22
Have removed the ntfs partiton and created an ext3 partition. You have to do this before you format the drive.

You can use either fdisk if you are comfortable in a terminal or gparted if you like to use a gui. Gparted is in the repositories and you can use synaptic to install it.

Jim

---

### Post by AegisTalons on 2008-06-23
Well I tried fdisk and it gives the same answer. It has something to do with the "Attempt to read block from filesystem resulted in short read while creating root dir". And I'm pretty sure that gparted is going to give the same thing. Also this is on a server and its all command line.

Does anyone know if I overwrite absolutely everything on the hard drive with zeros, if that might work. I'm thinking absolutely everything including MBR, everything. I want a blank hard drive.

---

### Post by zingalala on 2008-12-15
I am getting exact same error when I try to format ext3 partition on a 1TB WD Internal SATA drive. gpated simply give error without any specific reasons so I tried to create ext3 file system with command mkfs.ext3 /dev/sdx

parted can create partition table and partition successfully but mkfs can not create file system. THis seems like a file system bug.

I tried creating ntfs file system and that works. But I don't like ntfs because when it goes out of sync I need windows PC to get back to normal state. I have no windows PC in my house!

I need ext3. I may settle for raiserfs.

---

### Post by mikechant on 2008-12-15
I did a bit of research on this error message
> ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir 

There were a lot of cases where no conclusion was reached about the cause. But the following are possiblities (most likely first)
[LIST=1]
[*]The drive has a hardware fault. It may appear generally usable and formatable with other file systems like NTFS, but this error indicates it is dodgy and about to fail.
[*]There are sometimes problems with having all the disk space in one partition. Try creating a small partition first (just 1G say) followed by a large partition using the rest of the space.
[*]There are sometimes problems with partition sizes greater than 256Gb. Try creating two 150Gb partitions.
[/LIST]

2 and 3 above are fairly easy to try out. If it looks like a hardware fault you could look into the 'smartctl' command for listing disc error data (SMART data), but a clean report doesn't mean the disc is definitely OK.

---

### Post by wlan-11g on 2009-04-21
Had the same problem..

my fix was to load up gparted, start from the end of the volume, created a 730gb partition. last 20 or so gb's couldn't write the file system.

Oh well i'm not too fussed, lost about 20gb's

---

### Post by pete_m on 2010-06-25
As a post script to this thread in case other netbook users may encounter similar problems

- using an EEE PC i've had problems with the second SolidState Drive.  .

after first problems with the drive i re-formatted sucessfully. Having read that the early par tof the disk might be problematic.I left 16 Mb of empty space at the head of the disk . .
a couple of months later and the disk has failed again.. this time i've left a bigger space before getting rid of "short read" errors.
starting from  the back of the disk sounds a good idea . .

my problem driive is  now partitioned as 
4Gb( just less) ext3,
 27Gb ext3
1Gb swap

my first HDisk is currently not bootable - upgrade troubles .. .and i'm writing this on an EB4 stick pending resolution .

---

