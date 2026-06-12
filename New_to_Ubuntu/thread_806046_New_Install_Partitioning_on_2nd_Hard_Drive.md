---
title: "New Install Partitioning on 2nd Hard Drive"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by jukingeo on 2008-05-24
Hello all,

I am new to Ubuntu and I am a bit confused as to going about partitioning my new hard drive to accept a new permanent install of Ubuntu.  I have the latest version (8.04). And I have a 2 Hard Drive System.

Here are the details:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32c632c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78124063+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
ubuntu@ubuntu:~$

Ok the first drive which is "sda" (80gig) is my main Windows Drive.  I am not going to touch this drive at all.  That is going to be my dedicated Windows Drive.

The next drive is the one in question.  I am going to put the Ubuntu installation on the "sdb" drive.

As you can see from the information above, this hard drive is a brand new 500gig SATA drive of which I just installed yesterday.  The BIOS recognized the drive and I can pull it up here through "sudo fdisk -l".

So at this point I am ready for my Ubuntu installation.   I do understand that Ubuntu can partition the drive for my need and I already have been getting advice at how to do this.  However, some things I am not clear on and I decided to make a dedicated thread on this topic.

During my readings I do understand that I should set the partitioner to "Manual" and nothing else when asked to do so.

Supposedly there is a recommended way to set up the partitions and this is what I gather they supposed to be:

1) About 15gig or so for the main Ubuntu installation (in the partitioning program is this the "Primary partition?)
2) Another partition should be set from 1 to 2gig for a Swap Partition (what is this really for and should it be placed at the beginning of the hard drive or at the end?).
3) The next partition should be a point set for the \home information to retain all personal settings for Ubuntu for when the OS is upgraded.  
4) Finally a shared partition should be created to handle both Windows and Ubuntu Files.  However, if this partition is set to the recommended EXT3 file system, a program has to be installed in Windows in order for it to see the files.

Originally I was going to make the shared partition FAT32, because both Ubuntu and Windows can access that file format without any additional programs.  However, I was told that it is a very wasteful format and that using the EXT-3 file format is best, but i would have to use a special program in Windows in order to read and write to the files on that partition.  Ok, so I get that and it is no biggie.

There seems to be quite a bit of confusion on to where should I put the boot loader (Grub) program.  Since I have an existing Windows installation and my desire is to dual boot, I was told to make sure that Grub is installed on the Ubuntu drive as to not interfere with Windows.  Yet, I was also told that on installation to leave the Grub program setting on it's default.  The default setting points to the Windows Drive. So leaving it at that setting is contradictory to what I been reading.  So what should I do here?  Does Grub go on the Windows drive or on the drive I am going to put Ubuntu on?

Overall, this is what I would like to do.  I would like to follow the procedure as recommended, but I think I am going to go with more partitions due to the fact that the hard drive is so large.  So this is what I came up with.

1) 15 gig "Primary" partition for the main Ubuntu Program (Ext 3)
2) 2gig Swap File to be placed at the end of disk (EXT 3)
3) 100gig /home file for main settings and Ubuntu Programs (Ext 3)
4) 50gig FAT32 Partition for extra Windows data storage
5) 100gig universal data storage A (Ext 3)
6) (whatever is left) universal data storage B (mainly for audio/video files) EXT 3).

So overall I am looking to split the drive up into 6 partitions.

I am looking for recommendations particularly with the 50gig FAT32 partition.  Should I even bother?

Also I do need some clarification on what I should do with Grub.  I was told to leave it at it's default setting, but that is my Windows Drive.  Considering the horror stories I heard about Grub and installing it on the Windows Drive, I think I should err on the side of safety and install Grub on the "B" or second hard drive.  Again I need advice here.

The last thing I would like to do is put myself in a position where I wipe out my Windows Drive.  So the goal is NOT to touch the Windows (80gig sda) drive at all.

So any advice, clarifications and opinions are welcome.

Thank You,

Geo

---

### Post by Steve413z on 2008-05-24
Here is my recommendation for you:

Most hard drives only allow a maximum of 4 partitions (unless you use "logical" partitions)

My recommendation to you is:
1. 100 GB Partition for Ubuntu (including /home)
2. swap partition
3. The remaining volume as FAT32 (because both windows and ubuntu can access it)


or if you want a Separate home directory partition: 
1. 15 GB Partition for Ubuntu
2. 100 GB for /home
3. swap partition
4. The remaining volume as FAT32 (because both windows and ubuntu can access it)

---

### Post by jukingeo on 2008-05-24
> **Steve413z said:**
> Here is my recommendation for you:

Most hard drives only allow a maximum of 4 partitions (unless you use "logical" partitions)


Ok, that throws another curve ball in the mix.  I thought you could only have TWO partitions, a Primary and an extended and if you want more you have to create logical partitions withing the extended partition.

But the answer would be "Yes" I would use logical partitions, probably to divide down the "storage" space pretty much as outlined above.


> My recommendation to you is:
1. 100 GB Partition for Ubuntu (including /home)
2. swap partition
3. The remaining volume as FAT32 (because both windows and ubuntu can access it)


or if you want a Separate home directory partition: 
1. 15 GB Partition for Ubuntu
2. 100 GB for /home
3. swap partition
4. The remaining volume as FAT32 (because both windows and ubuntu can access it)

I would be opt to go with the latter set up because it separates the main Ubuntu installation from your settings.  From what I gather it is better to obliterate the old version of Ubuntu entirely before doing an upgrade.  Thus if you delete the "home" folder along with that, you will loose all your settings and have to redo them every time.  Whereas a large /home partition could also be used to store Ubuntu programs.

Now it does seem that you favor the FAT32 format.  I was told that when you start getting to large volumes, that it is very wasteful and either NTSC would be better or the best way would be to go with the EXT-3 format.  Granted this format isn't read/writable in Windows natively, but I hear there is a program out that fixes that.

Yet I did think about creating a small portion of that disk (50gig) to FAT32 and for the most part that would be a place to store Windows files (that I also want to access in Ubuntu).  However with EXT-3 AND the Windows program fix in place, I am thinking that it may not be necessary.

However, there is one question you didn't address and that was what should I do about Grub?  I read that it isn't wise to put Grub on the Windows Hard Drive and that I should only put it on the primary Ubuntu partition.  Yet, in another guideline someone said to leave the the Grub setting at "default".  But the default setting points to the Windows drive.  So now I am not really sure what to do here.

Please advise.

Thank You,

Geo

---

### Post by Steve413z on 2008-05-24
> **jukingeo said:**
> Ok, that throws another curve ball in the mix.  I thought you could only have TWO partitions, a Primary and an extended and if you want more you have to create logical partitions withing the extended partition.

But the answer would be "Yes" I would use logical partitions, probably to divide down the "storage" space pretty much as outlined above.




I would be opt to go with the latter set up because it separates the main Ubuntu installation from your settings.  From what I gather it is better to obliterate the old version of Ubuntu entirely before doing an upgrade.  Thus if you delete the "home" folder along with that, you will loose all your settings and have to redo them every time.  Whereas a large /home partition could also be used to store Ubuntu programs.

Now it does seem that you favor the FAT32 format.  I was told that when you start getting to large volumes, that it is very wasteful and either NTSC would be better or the best way would be to go with the EXT-3 format.  Granted this format isn't read/writable in Windows natively, but I hear there is a program out that fixes that.

Yet I did think about creating a small portion of that disk (50gig) to FAT32 and for the most part that would be a place to store Windows files (that I also want to access in Ubuntu).  However with EXT-3 AND the Windows program fix in place, I am thinking that it may not be necessary.

However, there is one question you didn't address and that was what should I do about Grub?  I read that it isn't wise to put Grub on the Windows Hard Drive and that I should only put it on the primary Ubuntu partition.  Yet, in another guideline someone said to leave the the Grub setting at "default".  But the default setting points to the Windows drive.  So now I am not really sure what to do here.

Please advise.

Thank You,

Geo


there is a windows program to read and write EXT3, however i've never tried it, and there is NTFS support for linux, but it doesn't work that well.  FAT32 is somewhat wasteful and starting to become out of date, but it works well in both linux and windows without problem, most of my external hard drives I use for backup and file storage are FAT32.  I am not sure what exactly you have in mind, so I would leave it up to you on what to do.

---

### Post by jukingeo on 2008-05-25
> **Steve413z said:**
> there is a windows program to read and write EXT3, however i've never tried it, and there is NTFS support for linux, but it doesn't work that well.  FAT32 is somewhat wasteful and starting to become out of date, but it works well in both linux and windows without problem, most of my external hard drives I use for backup and file storage are FAT32.  I am not sure what exactly you have in mind, so I would leave it up to you on what to do.

Hello all,

Just a recap I did the install yesterday and I did have some problems with the Grub boot loader and I couldn't boot into Windows nor Ubuntu.  I was able to get my computer going only via the Live CD and I made a separate posting of that problem yesterday.  I received some really good help and now that problem is fixed.

For the record this is what I ended up with for a final drive set up:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32c632c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78124063+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf364

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1837    14755671   83  Linux
/dev/sdb3            1838       13995    97659135   83  Linux
/dev/sdb4           13996       60800   375961162+   5  Extended
/dev/sdb5           54722       60800    48829567+   b  W95 FAT32
/dev/sdb6           13996       32231   146480607   83  Linux
/dev/sdb7           32232       54465   178594573+  83  Linux
/dev/sdb8           54466       54721     2056288+  82  Linux swap / Solaris

Partition table entries are not in disk order
geo@geo-desktop:~$ 

Drawing your attention to the second drive (the first 80gig drive is my Windows drive and that went untouched).  That drive is my new Seagate 500gb SATA drive.

Going down the list as follows:
sdb1 is the boot partition

sdb3 is where the main Ubuntu program is and is the bootable part of the drive.  This is set at about 15gig

sdb4 is the /home partition where my settings are stored and also Ubuntu programs will be installed. This is about 100g

sdb5 is a FAT32 partition and it is only 50gig of the whole drive.  This is going to be where most of my Windows files will be stored.  I was going to go with NTSC for obviously more efficient use of space, but in the event I DO also end up using this for storing Ubuntu files, I can.

sdb6 is a 150gb EXT-3 Partition that is where I will be storing most of my Ubuntu files and documents. 

sdb7 is the largest partition which is over 150gig and this will be storage of mostly MP3, Audio and Video files.

sdb8 is a 2 gig swap file.

So that is what I ended up with.

Geo

---

