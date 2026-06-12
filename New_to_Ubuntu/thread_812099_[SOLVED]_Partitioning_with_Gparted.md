---
title: "[SOLVED] Partitioning with Gparted"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by ben32b on 2008-05-29
I have a 500GB hard drive (no files on it yet), and I want to make a few partitions using the Gparted program that is on my Ubuntu 8.04 LiveCD:
[LIST=1]
[*]Ubuntu - What filesystem should this be (I don't know which is best for Linux) and how large should I make it?
[*]80GB partition for random files - Should the filesystem be NTFS?
[*]Truecrypt encrypted partition. It will take up the remainder of the hdd space - Should this also be NTFS?
[/LIST]
Partition #1 will be used only in Ubuntu, and not in Windows.
Partition #2 and Partition #3 will be used in both Ubuntu and Windows XP.

After these 3 partitions have been made, I will want to install Ubuntu on my Ubuntu partition. Can I tell the Ubuntu installer to install just to my Ubuntu partition?
Next I will encrypt the Truecrypt partition with Truecrypt, and leave the 80GB partition as-is.

It would be very helpful if these questions can be answered.

---

### Post by logos34 on 2008-05-29
> **ben32b said:**
> 
[LIST=1]
[*]Ubuntu - What filesystem should this be (I don't know which is best for Linux) and how large should I make it?

ext3 (the default)
> 
[*]80GB partition for random files - Should the filesystem be NTFS?

you can also make it ext3.  Get fs-driver so windows can read/write to it. Or ntfs if that makes you happy.  Hardy comes with ntfs-3g driver so you can write to ntfs from linux
> 
[*]Truecrypt password protected partition. It will take up the remainder of the hdd space - Should this also be NTFS?
[/LIST]

Someone else will know the answer

> Partition #1 will be used only in Ubuntu, and not in Windows.
Partition #2 and Partition #3 will be used in both Ubuntu and Windows XP.

After these 3 partitions have been made, I will want to install Ubuntu on my Ubuntu partition. Can I tell the Ubuntu installer to install just to my Ubuntu partition?

yep, specify '/' mountpoint for root (ext3), '/swap' (linux-swap) and maybe a separate /home.

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by ben32b on 2008-05-29
logos34: You suggested that I format the 80GB partition to ext3. Can Windows read & write ext3 drives?

---

### Post by Shazaam on 2008-05-29
Some help.....
1. ext3 is usually recommended.
2. Depends on if it will be shared with Windows.
3. I haven't used TrueCrypt, can't help here.
Keep (or install) Windows first. If you are going to resize Windows make sure you defrag it first. Then add the linux partitions after Windows. To keep from bumping into the 4 primary partition limit make an extended partition after Windows then add your linux distro's as logical partitions inside of the extended partition.
For future reference, if you re-install Windows at a later date you will wipe out whatever boot loader (grub, gag, lilo, etc) is installed and you will have a problem booting to linux. This CAN be fixed but it's a pain IMHO. I keep a SuperGrubDisk around just for this eventuality.

---

### Post by kk0sse54 on 2008-05-29
> Can Windows read ext3 drives? 

yes windows can read ext3 only if you install the fs-driver like logos34 said otherwise by default windows can't read, write or recognize a ext3 extension. For data partitions that involve both windows and linux I like to just stick with NTFS because by default ubuntu includes the driver needed to read and write to NTFS partitions so nothing extra needed

---

### Post by ben32b on 2008-05-29
Thanks for the help. :)

---

### Post by paapereira on 2008-05-29
> **ben32b said:**
> logos34: You suggested that I format the 80GB partition to ext3. Can Windows read & write ext3 drives?

Check the [driver]("http://www.fs-driver.org/download.html") logos34 mentioned.

It says ext2 but it will work with ext3 also. :popcorn:

---

### Post by ben32b on 2008-05-29
What size do you suggest I make my Ubuntu partition?

---

### Post by paapereira on 2008-05-29
> **ben32b said:**
> What size do you suggest I make my Ubuntu partition?

Here's a [good place]("http://ubuntuforums.org/showthread.php?t=282018") to start reading. It helped me to decide.

I currently have:
```
/dev/sdc2    ext3    /         15360 MB (20 GB)
/dev/sdc5    ext3    /home     15360 MB (15 GB)
/dev/sdc6    swap               2048 MB (2 GB)
```

---

### Post by kk0sse54 on 2008-05-29
> What size do you suggest I make my Ubuntu partition? 

If you plan to make a seperate home partition and plan on storing all your data on another partition then you at most need 20 GB. Although probably 10-15 GB is more ideal if you are installing a lot of software especially of the heavy type otherwise you can do anything from 4-10 GB if you are looking to use a light weight window manager and less and lighter programs. Your swap partition totally depends on how much RAM you have and as for your /home if you are using it store data then obviously you will want it bigger but otherwise it doesn't have to be too big.

---

### Post by ben32b on 2008-05-29
I finished making the partitions:
[INDENT]500Gbit HDD with a 15GB ext3 primary and a 450GB extended. On the extended I have a 80GB NTFS logical and a 370GB logical.[/INDENT]
I then tried installing Ubuntu onto the 15GB ext3 primary partition.

During the installation at the menu where it says "Prepare Disk Space" (step 4 of 7), I selected "Manual".
Then I selected my 15GB ext3 primary partition (/dev/sdb1/), then pressed forward but I get this error:
```
No root file system is defined.

Please correct this from the partitioning menu.
```


I'm not sure how to get around this error, so could someone explain what I should do?

---

### Post by ben32b on 2008-05-29
bump

---

### Post by logos34 on 2008-05-29
change the mount point to '**/**'

---

### Post by ben32b on 2008-05-30
> **logos34 said:**
> change the mount point to '**/**'
That fixed my problem :)
But now the installer tells me to make a partition for "swap space". Should I make this partition ext3? What size do you suggest I make the partition for swap space?

---

### Post by kwacka on 2008-05-30
Double the size of your RAM, e.g. I GB RAM, 2 GB /swap.

Place it anywhere you want - it doesn't matter. It will be formatted as 'swap' NOT ext2, ext3, reiserfs, etc.

It won't ask you for a /home partition. If you want it on a separate partition create another partition labeled /home. Otherwise /home will be on the same partition as /.

---

