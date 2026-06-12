---
title: "retrieving data from  non booting lvm partition"
date: 2018-08-09
forum: New to Ubuntu
---

### Post by simongatti on 2018-08-09
I have 16.04 on my computer which now won't boot.

from a 18.04 pen drive

lvdisplay gives me /dev/ubuntu-vg/root and a swap partition

I activated the volumes with vgchange -a y ubuntu-vg and made /tmp/disk with mkdir
mounted it and changed the directory to /tmp/disk
ls gives the usual suspects including 'home'
navigating to /home/simon reveals my all my directories 

so far so good!

I attach my samsung portable hard drive seen as /dev/sdc1 on media/ubuntu/SAMSUNG type fuseblk

Then I get stuck.  I can't copy or move any of the files or directories rsync gives me Error: cannot stat destination "/dev/sdc1/SAMSUNG": not a directory
I've tried making directories in terminal and directly on the Samsung but it keeps telling that whatever I type is not directory.

Where am I going wrong?

---

### Post by TheFu on 2018-08-09
The issue seems to be with the Samsung thingy.

Check a few things.
mount - will show the exact options used.  If it is read-only, you can't copy anything there. Best not to use a GUI to mount storage.  Try using **mkdir /mnt/sam ; mount /dev/sdc1   /mnt/sam **
Any errors?

Check the permissions on the mountpoint and inside - 
**ls -al   /mnt/sam**

Depending on the file system, you might have to control the permissions at mount time. That is usually required for non-Linux file systems like NTFS or FAT-whatever.

---

### Post by Dennis N on 2018-08-09
May be as simple as this:

rsync can't use /dev/sdc1/ as part of the destination path since it's not a directory:

look:
```
[dmn@Sydney ~]$ file /dev/sda1
/dev/sda1: block special (8/1)
[dmn@Sydney ~]$ file /mnt/tmp
/mnt/tmp: directory

```

You need to use the mount point in designating the destination path for rsync, like /media/ubuntu/SAMSUNG/...

---

### Post by simongatti on 2018-08-10
> **TheFu said:**
> The issue seems to be with the Samsung thingy.

Check a few things.
mount - will show the exact options used.  If it is read-only, you can't copy anything there. Best not to use a GUI to mount storage.  Try using **mkdir /mnt/sam ; mount /dev/sdc1 **
Any errors?

Check the permissions on the mountpoint and inside - 
**ls -al   /mnt/sam**

Depending on the file system, you might have to control the permissions at mount time. That is usually required for non-Linux file systems like NTFS or FAT-whatever.

Thanks so much for looking at this
mkdir gives me this
```
ubuntu@ubuntu:/tmp/disk/home/simon$ sudo mkdir /mnt/sam ; mount /dev/sdc1
mount: /dev/sdc1: can't find in /etc/fstab.
```



```
[B]ls -al   /mnt/sam 
[/B]total 0
drwxr-xr-x 2 root root 40 Aug 10 16:37 .
drwxr-xr-x 1 root root 60 Aug 10 16:37 ..
```

for your information

```
**lsblk** 
NAME                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                   7:0    0   1.8G  1 loop /rofs
loop1                   7:1    0  86.9M  1 loop /snap/core/4917
loop2                   7:2    0  34.7M  1 loop /snap/gtk-common-themes/319
loop3                   7:3    0 140.9M  1 loop /snap/gnome-3-26-1604/70
loop4                   7:4    0   2.3M  1 loop /snap/gnome-calculator/180
loop5                   7:5    0    13M  1 loop /snap/gnome-characters/103
loop6                   7:6    0  14.5M  1 loop /snap/gnome-logs/37
loop7                   7:7    0   3.7M  1 loop /snap/gnome-system-monitor/51
sda                     8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1                  8:1    0   512M  0 part 
&#9492;&#9472;sda2                  8:2    0 232.4G  0 part 
  &#9500;&#9472;ubuntu--vg-root   253:0    0 224.5G  0 lvm  
  &#9492;&#9472;ubuntu--vg-swap_1 253:1    0   7.9G  0 lvm  
sdb                     8:16   1   7.2G  0 disk /cdrom
&#9500;&#9472;sdb1                  8:17   1   1.8G  0 part 
&#9492;&#9472;sdb2                  8:18   1   2.3M  0 part 
sdc                     8:32   0 931.5G  0 disk 
&#9492;&#9472;sdc1                  8:33   0 931.5G  0 part /media/ubuntu/SAMSUNG
sr0                    11:0    1  1024M  0 rom
```

---

### Post by simongatti on 2018-08-10
When I do as you suggest I get the following

```
ubuntu@ubuntu:/tmp/disk/home/simon$ file /dev/sda1
/dev/sda1: block special (8/1)
ubuntu@ubuntu:/tmp/disk/home/simon$ file /mnt/tmp
/mnt/tmp: cannot open `/mnt/tmp' (No such file or directory)
```

---

### Post by TheFu on 2018-08-10
I made a mistake - actually thought I'd fixed it, but I was multitasking and missed it.
Here's the correction:
```
sudo mkdir /mnt/sam ; sudo mount /dev/sdc1  /mnt/sam
```
All the other commands after my mistake don't work. Sorry.  I fixed the original.  Please do them again, and if anything fails, stop.

Using "code tags"  would really help.  Adv Editing/Reply has a button (#) for it. Please edit your prior posts, so the code will line up. Too hard for me to read otherwise.

Please ensure sdc1 is still the right device. Drives move around sometimes, so it could have changed the device.

---

### Post by Dennis N on 2018-08-10
> **simongatti said:**
> When I do as you suggest I get the following

```
ubuntu@ubuntu:/tmp/disk/home/simon$ file /dev/sda1
/dev/sda1: block special (8/1)
ubuntu@ubuntu:/tmp/disk/home/simon$ file /mnt/tmp
/mnt/tmp: cannot open `/mnt/tmp' (No such file or directory)
```

That display in post #3 is only to show that notation like sda1 isn't the name of a directory or standard file, so you can't use such notation in paths to files. (Paths to files contain directories and a file name.)

Again, your destination path in post #1 is invalid because of the use of /dev/sdc1:
```
Error: cannot stat destination "/dev/sdc1/SAMSUNG": not a directory
```

Your rsync command should have a destination path starting at the mount point:
The mount point /media/ubuntu/SAMSUNG is actually the root of the mounted partition's file system, so
```
rsync source-directory /media/ubuntu/SAMSUNG
```
would sync the source directory to the root directory (SAMSUNG).
If you don't want to sync to the root directory, extend the path to another directory.

---

### Post by simongatti on 2018-08-11
> **TheFu said:**
> I made a mistake - actually thought I'd fixed it, but I was multitasking and missed it.
Here's the correction:
```
sudo mkdir /mnt/sam ; sudo mount /dev/sdc1  /mnt/sam
```
All the other commands after my mistake don't work. Sorry.  I fixed the original.  Please do them again, and if anything fails, stop.

Using "code tags"  would really help.  Adv Editing/Reply has a button (#) for it. Please edit your prior posts, so the code will line up. Too hard for me to read otherwise.

Please ensure sdc1 is still the right device. Drives move around sometimes, so it could have changed the device.

I have edited my posts as you asked I think, let me know if I haven't done it correctly.

So I checked that Samsung is still sdc1 and it is
When I put in your revised command I get
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/sam ; sudo mount /dev/sdc1  /mnt/sam
mkdir: cannot create directory ‘/mnt/sam’: File exists
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
```

Looked at the fuser command but I don't understand the syntax so I haven't tried it

---

### Post by TheFu on 2018-08-11
Thanks for the 'code tags' - much easier to read.
There are 2 different possibilities for that problem.
1) Windows was used to access the storage and it didn't get closed properly.  Win8 and later don't close storage at shutdown.  Something to do with "fastboot" ...look up on a Windows forum for how to disabled that from inside Windows.
or
2) Linux isn't letting you mount it again because it is already mounted somewhere else.  The output above says it is mounted on /media/ubuntu/SAMSUNG.   I don't use/allow automatic mounts, but if you can show the permissions, we can figure out what is needed. This command will show them:
```
ls -la /media/ubuntu/SAMSUNG 
```
We need to prove that, before crafting the rsync to get the data off.
It would also help to have the ls -al for the HOME directory you want, I'm guessing that is where the data you want is located.  Userids and groupids matter. That is why you can't just copy the data using a GUI.

After everything is mounted for the source and target storage, then you just need something like
```
sudo rsync -avz /home/simongatti  /media/ubuntu/SAMSUNG/
```
Training '/' characters are important with rsync. Having one or not matters.

I'm assuming after you get the data off, then you'll just do a fresh install and copy the data back?
You have some skills - getting LVM working from a flash boot is good, but to fix the booting issue with LVM is more involved and will need a clear understanding of permissions to be successful.  It seems you're understanding of users, groups, file and directory permissions hasn't gotten to that point yet.

---

### Post by simongatti on 2018-08-11
> **TheFu said:**
> Thanks for the 'code tags' - much easier to read.
There are 2 different possibilities for that problem.
1) Windows was used to access the storage and it didn't get closed properly.  Win8 and later don't close storage at shutdown.  Something to do with "fastboot" ...look up on a Windows forum for how to disabled that from inside Windows.
or
2) Linux isn't letting you mount it again because it is already mounted somewhere else.  The output above says it is mounted on /media/ubuntu/SAMSUNG.   I don't use/allow automatic mounts, but if you can show the permissions, we can figure out what is needed. This command will show them:
```
ls -la /media/ubuntu/SAMSUNG 
```
We need to prove that, before crafting the rsync to get the data off.
It would also help to have the ls -al for the HOME directory you want, I'm guessing that is where the data you want is located.  Userids and groupids matter. That is why you can't just copy the data using a GUI.



 So the **ls** command produces

```
ubuntu@ubuntu:~$ ls -la /media/ubuntu/SAMSUNG
total 273804
drwxrwxrwx  1 ubuntu ubuntu      4096 Feb 23  2013 '$RECYCLE.BIN'
drwxrwxrwx  1 ubuntu ubuntu     20480 Aug 11 10:27  .
drwxr-x---+ 3 root   root          60 Aug 11 12:19  ..
drwxrwxrwx  1 ubuntu ubuntu         0 Feb  5  2014  .Trash-1000
-rwxrwxrwx  1 ubuntu ubuntu     86046 Jun  5  2014 '1310 hsbc oct 13.pdf'
drwxrwxrwx  1 ubuntu ubuntu      4096 Aug 21  2016 '14--04 Backup 160816'
-rwxrwxrwx  1 ubuntu ubuntu    285453 Aug 21  2016  14--04.zip
drwxrwxrwx  1 ubuntu ubuntu      4096 Aug 16  2016 '16-04 Backup 160816'
-rwxrwxrwx  2 ubuntu ubuntu   1037087 Jan 10  2013  1DayDiet-CheatSheets-r3p1231.pdf
-rwxrwxrwx  2 ubuntu ubuntu    731786 Feb 11  2013  23-BellyBlastingFoods-BBF010213WFQ.pdf
drwxrwxrwx  1 ubuntu ubuntu     36864 Aug  4  2016 'Back Ups'
drwxrwxrwx  1 ubuntu ubuntu      8192 Jun  4  2017 'Back up from Documents'
drwxrwxrwx  1 ubuntu ubuntu         0 Aug 24  2016 'Backup HDD 24-08-16'
-rwxrwxrwx  1 ubuntu ubuntu    554439 Aug 24  2016  Backup.zip
-rwxrwxrwx  1 ubuntu ubuntu    335161 Aug  9  2016  Boot-Info_2016-08-09__13h20.txt
-rwxrwxrwx  1 ubuntu ubuntu    342849 Aug 24  2016  Boot-Info_2016-08-24__08h55.txt
drwxrwxrwx  1 ubuntu ubuntu     16384 Jul 21  2013  Cacin
drwxrwxrwx  1 ubuntu ubuntu         0 Aug  6 17:57  Dinopc
drwxrwxrwx  1 ubuntu ubuntu     12288 May  1  2016  Downloads
drwxrwxrwx  1 ubuntu ubuntu    114688 Aug  9  2017 'Duplicity Backup 090817 Ubuntu 16.04'
drwxrwxrwx  1 ubuntu ubuntu         0 May  5  2016  FileHistory
drwxrwxrwx  1 ubuntu ubuntu     16384 Dec 20  2015 'Films and TV'
drwxrwxrwx  1 ubuntu ubuntu     16384 Dec 28  2014  HSBC
drwxrwxrwx  1 ubuntu ubuntu     32768 Jul  9  2013  Images
drwxrwxrwx  1 ubuntu ubuntu         0 Aug  8  2016  Insurance
drwxrwxrwx  1 ubuntu ubuntu      8192 Sep  7  2017  Library
drwxrwxrwx  1 ubuntu ubuntu         0 Aug  8  2016  MIMILAPTOP
drwxrwxrwx  1 ubuntu ubuntu      4096 Apr  6  2013  Mimi
drwxrwxrwx  1 ubuntu ubuntu      4096 May  5  2016 "Mimi's Backup"
drwxrwxrwx  1 ubuntu ubuntu     65536 Feb 18  2013 "Mimi's phone"
drwxrwxrwx  1 ubuntu ubuntu         0 Aug  8  2016  Mint
drwxrwxrwx  1 ubuntu ubuntu      4096 May  1  2016 'Mint Documents'
drwxrwxrwx  1 ubuntu ubuntu         0 Apr  1  2013  Music
drwxrwxrwx  1 ubuntu ubuntu      8192 Dec 19  2015 'My Drawings'
drwxrwxrwx  1 ubuntu ubuntu         0 Aug  7  2016 'New folder'
drwxrwxrwx  1 ubuntu ubuntu      4096 Feb  9  2013  Pictures
-rwxrwxrwx  2 ubuntu ubuntu   1398872 Jul 17  2012 'Portable SecretZone.exe'
drwxrwxrwx  1 ubuntu ubuntu         0 Oct  5  2012 'Samsung Drive Manager'
drwxrwxrwx  1 ubuntu ubuntu      4096 May 22  2016 'Samsung Drive Manager Manuals'
-rwxrwxrwx  2 ubuntu ubuntu    165976 Jul 17  2012  Samsung_Drive_Manager.exe
drwxrwxrwx  1 ubuntu ubuntu      4096 Oct 25  2014  Simon
drwxrwxrwx  1 ubuntu ubuntu      4096 May 22  2016 'System Volume Information'
-rwxrwxrwx  1 ubuntu ubuntu   2269644 Dec 18  2016  TLCL-16.07.pdf
drwxrwxrwx  1 ubuntu ubuntu      4096 Oct 30  2013 'User Manual'
drwxrwxrwx  1 ubuntu ubuntu     12288 Jan 25  2017  b71fd6b549ce511844d764902d0439cb
drwxrwxrwx  1 ubuntu ubuntu      4096 Apr 22 17:37 'backup 22-04-18'
-rwxrwxrwx  2 ubuntu ubuntu     91806 May 21  2016 'backup instructions.pdf'
drwxrwxrwx  1 ubuntu ubuntu      8192 Jan 26  2017  c1d62a239eb0de3d9510
drwxrwxrwx  1 ubuntu ubuntu      4096 Jul  5  2015  data
drwxrwxrwx  1 ubuntu ubuntu         0 Aug 11 10:27  dino
-rwxrwxrwx  1 ubuntu ubuntu   4211152 May  5  2016  hhealth.exe
drwxrwxrwx  1 ubuntu ubuntu      4096 Aug  8  2016 'lexar 19_6_19'
-rwxrwxrwx  1 ubuntu ubuntu 268400013 May  4  2016  tmp1j5lwac8.0

```


and the same command on **/tmp/disk/home**

```
ubuntu@ubuntu:~$ ls -la /tmp/disk/home
total 12
drwxr-xr-x  3 root root 4096 Aug  9  2017 .
drwxr-xr-x 25 root root 4096 Aug 11 11:40 ..
drwxr-xr-x 47 1000 1000 4096 Dec 21  2017 simon
```

> After everything is mounted for the source and target storage, then you just need something like
```
sudo rsync -avz /home/simongatti  /media/ubuntu/SAMSUNG/
```
Training '/' characters are important with rsync. Having one or not matters.

I'm assuming after you get the data off, then you'll just do a fresh install and copy the data back?
You have some skills - getting LVM working from a flash boot is good,  but to fix the booting issue with LVM is more involved and will need a  clear understanding of permissions to be successful.  It seems you're  understanding of users, groups, file and directory permissions hasn't  gotten to that point yet.



I thought I would let you look at the above before attempting the next step.  Not sure why the samsung has linux mounted on it - I just use it as storage and for backing up.  Absolutely I am going to wipe the whole drive and do a fresh install of 18.04 with a separate partition for data plus anything else you might recommend.  Although I've been using ubuntu for several years now I have to say I'm still pretty much an absolute beginner so I really appreciate the help

---

### Post by TheFu on 2018-08-11
```
sudo rsync -avz  /tmp/disk/home/simon  /media/ubuntu/SAMSUNG/
```
That will make a 'simon' directory under SAMSUNG with all the data (and more) that you can stand.

But really the userid, groupid, and permissions stuff like this is something you should learn.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a free pdf you can download without being hassled. It does a good job explaining those topics in the correct order.   Unix permissions are central to all Unix/Linux security.

---

### Post by simongatti on 2018-08-11
**Success!**

 **rsync** is working as I write.

Can't thank you enough.

I will certainly read up on the commands as you suggest.

Would you advise a beginner like me to stick to **ext4** partitions rather than the **lvm2** that I saddled myself with?

---

### Post by TheFu on 2018-08-11
> **simongatti said:**
> **Success!**

 **rsync** is working as I write.

Can't thank you enough.

I will certainly read up on the commands as you suggest.

Would you advise a beginner like me to stick to **ext4** partitions rather than the **lvm2** that I saddled myself with?

Yes and no.  It depends.  There are things that only LVM can accomplish and if you don't have it, then getting it is basically a fresh install.  LVM brings lots of flexibility at the cost of increased complexity.  

I use LVM always on physical storage, but I follow a few rules to avoid being burned. I've lost 80% of my data around 2002 using LVM features that didn't turn out well.  I haven't used those features since.  But I do use the resize up/down and snapshots all-the-time.  Actually, I use snapshots daily, on almost every system here, as part of my backup scripts. Consistent backups with zero downtime, guaranteed?  Can't do that any other supported way that I know. Gotta have LVM for it.

But if you don't need to resize LVs or have perfect backups with zero downtime, then LVM might not be worth the extra hassle.  I can't say. Resizing LVs up and down along with the file system only works if ext4 is used.  Lots of other vendors push using xfs + LVM, but those can only be resized up, never down.   I never correctly size LVs on my first attempt, even after all these decades.

There is ZFS, which merges LVM and a file system, but ZFS isn't supported as a boot file system on Ubuntu.  It is fully supported for data storage, just not booting - so not for /boot/, /, /var/, ... you get the idea.  ZFS has some very advanced capabilities beyond what LVM+EXT4 support.  ZFS is a little less complex in some ways and a lot more complex in others.

There is also BTRFS, which tries to be a lighter ZFS with advanced feature.  Early on, it had data loss issues and compatibility issues with some core things I use, so I never considered BTRFS useful.  Last year, Redhat deprecated support for it and now it seems to only have SuSE for support.  BTRFS doesn't integrate correctly with other tools - basically, it lies about storage to df and du, which I find completely unacceptable.  Those tools are 2nd nature to me. They are 100% THE TRUTH. Any tool that doesn't let df/du tell the truth doesn't get used on my systems.

---

