---
title: "trying to access /dev/sda1"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by ProfessorPlum888 on 2012-11-23
so I am trying to go against all odds here and salvage some files from my laptop before reformatting.  A laptop running Windows XP Pro, with a small C: drive partition and a larger D: partition.  My laptop hard drive crashed the other day, such that it could not find the operating system anymore.  Booting from a USB drive with Windows on the bootable USB drive did no good either, as it saw the partitions but also thought that the partitions were unformatted.
 
I then went to my Hail Mary option, by installing Ubuntu (11.10) on a bootable USB drive and seeing what I can do there. I can see the partitions:
 
/dev/sda1 HPFS/NTFS/exFAT
/dev/sda2 HPFS/NTFS/exFAT
 
but I can't seem to mount the drives. This laptop is around 3 years old (HP EliteBook) running Windows XP Pro, so my guess is that it is FAT32 formatted but not sure. I'm not sure how to install the NTFS-3g utility onto the USB drive. When I try and mount the drive using this command:
 
mount -t vfat -o defaults, user,exec,uid=1000,gid-100,umask-100 /dev/sda1 /media/wdisk
 
I get an "wrong fs type, bad option, bad superblock on /dev/sda1......" error.
 
I hope I can recover the files. Can someone give me some step-by-step help here?
 
Thanks!

---

### Post by Sealbhach on 2012-11-23
That doesn't look good.

Well, it seems vfat is the wrong fs type, so try

mount -t ntfs

Also run fdisk -l and blkid,  and parted -l to see what it shows.

You can install ntfs-3g in the live USB session, should work OK.

.

---

### Post by ProfessorPlum888 on 2012-11-23
running parted -l shows that the partition of interest is ntfs, but when running blkid it shows:
 
/dev/loop0: TYPE="squashfs"
/dev/sdb1:  UUID="8828-ECAC" TYPE="vfat"
 
2nd question - can you give me a step-by-step on how to install the ntfs-3g onto my bootable usb stick?

---

### Post by ProfessorPlum888 on 2012-11-23
also, what does the "mount -t ntfs" do for me?

---

### Post by PinkFloyd102489 on 2012-11-23
Try:

```
sudo mount -t vfat /dev/sdb1 /media/windows
```

According to your parted command, it's a FAT volume on sdb1. The above command should mount the volume to the /media/windows directory. Then, just navigate there and anything that was in Windows should be there.

---

### Post by Sealbhach on 2012-11-23
Just install ntfs-3g like normal, it will work for the current live session, but I'm not sure if the change will persist on the next boot.

```
sudo apt-get install ntfs-3g
```

But anyway, see if PinkFloyd's suggestion works. 

.

---

### Post by Wim Sturkenboom on 2012-11-23
I doubt very much that the partitions are FAT; also, I've never had to install ntfs related stuff to be able to access windows partitions on my dual boot systems.

I would start with a simple mount omitting the type. Something like (possibly with sudo, not sure)
```

mount /dev/sdaX /mnt

```
Your C drive will be sda1, your D drive will be sda2.

---

### Post by ProfessorPlum888 on 2012-11-24
well, just using    **mount /dev/sda1 /mnt  **
gives me an error of:   *you must specify the filesystem type*

and

**mount -t vfat /dev/sda1  /media/wdisk**

gives me the "*wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage,....*"
going into **dmesg **gives me these errors:

[I]bogus number of reserved sectors
Can't find a valid FAT filesystem[/I]

---

### Post by Wim Sturkenboom on 2012-11-24
XP defaults to NTFS for the filesystem. So I doubt very much that it is any type of FAT; and you would now as you did setup the partitions.
Is your data on C: or on D: ? Useless trying sda1 if you want to recover from sda2.

If everything else fails, it's time to install recovery tools (like testdisk, which is in the repositories) while booted from the USB stick.

---

### Post by Mark Phelps on 2012-11-24
IF the hard drive was in bad enough shape for the Windows filesystems to get corrupted, no amount of hacking in Linux is going to mount those partitions in any way that will make the files recoverable.

While they MIGHT have been FAT filesystems, unless you were running XP from  the original install and never installed any Service Pack updates, they were NTFS partitions.

If you're interested in recovering data from those partitions, and testdisk doesn't work well for you, then read on below ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by The Cog on 2012-11-24
> **ProfessorPlum888 said:**
> well, just using    **mount /dev/sda1 /mnt  **
gives me an error of:   *you must specify the filesystem type*

and

**mount -t vfat /dev/sda1  /media/wdisk**

gives me the "*wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage,....*"
going into **dmesg **gives me these errors:

[I]bogus number of reserved sectors
Can't find a valid FAT filesystem[/I]
Yabbut your first post said the partition was ntfs, not vfat. So try:
```
mount -t ntfs /dev/sda1  /media/wdisk
```
I assume you have created the folder /media/wdisk for it to be mounted into (sudo mkdir /media/wdisk). However, the fact that blkid didn't list your sda drive is not a good indicator - maybe the drive is too corrupt for blkid to identify it properly.


If you can't get the disk mounted, the software Mark Phelps might help. Or there is a free CD called systemrescue that you can download and burn which has a program called testdisk on it. That program can scan the disk looking for files and save them to an external USB drive. It ignores the filesystem and looks just at disk sectors, so it will find lots even when the filesystem is scrambled. It will find many thousands of files, and save them with numbers for names, and it is then down to you to look for whatever you wanted to retrieve - it may or may not be there.

---

### Post by ProfessorPlum888 on 2012-11-27
thanks for all the replies. I used MarkPhelps' suggestion but the software found nothing after 2 days of searching.
 
I had used the Ubuntu method because I had had another Windows OS (Windows 7) hard drive crash on another laptop about 6 months ago, and was successfully able to mount the crashed partition and see the files. Not sure why this particular one would have "died" so suddenly without a trace of recoverability.

---

