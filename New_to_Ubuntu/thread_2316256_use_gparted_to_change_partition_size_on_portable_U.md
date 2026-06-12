---
title: "use gparted to change partition size on portable USB HDD?"
date: 2016-03-06
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2016-03-06
I have a new Toshiba 2T portable HDD that I want to use principally for backing up my Ubuntu /home files, and so want to reformat the existing 1.82Tib NTFS partition to approx 0.4Tib NTFS and make a new 1.4Tib EXT4, using gparted. When I attempt to reduce the 1.82 NTFS partition size to 0.40 as a first step, I get a scary warning that effecting such change may affect the ability of the drive to "boot".

I don't think of USB drives "booting", but I guess when they are plugged in and become visible, this can be described as (or is) a boot process.

So to help me avoid screwing up the usability of the portable drive, can I disregard the warning and proceed, or do I need to go about this another way? 

Trying to get this done soonest so I can do my backup today, so any early guidance appreciated. Thanks.

---

### Post by Bucky Ball on 2016-03-06
Ignore it. You don't have an OS installed on the drive or partition. Solved.

---

### Post by Odyssey1942 on 2016-03-06
BB, That was quick, painless and easy. Thanks for the quick reply. I'm on it!

---

### Post by Odyssey1942 on 2016-03-06
Might have jumped the gun marking this solved. Attempted to back up to the EXT4 partition using BackInTime (which I named, "Ext for Linux"), and got the message:

> Can't write to: /media/EXT4 for Linux. Are you sure you have write access?

This baffles me. Since I set it up on the computer I am trying to back up from, how could this be?

---

### Post by fantab on 2016-03-06
Can you plug in your "backup HDD/USB" and post the output of the following here:

```
sudo fdisk -l
sudo parted -l
```

Also check your HDD/USB for a "Write Protect" switch.... if there is one, then you will have disable the feature.

---

### Post by Odyssey1942 on 2016-03-06
There are no physical switches on the portable. Were you thinking of software?

robert@i3-2120:~$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00001736

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    31250431    15624192   82  Linux swap / Solaris
/dev/sda2   *    31250432    89843711    29296640   83  Linux
/dev/sda3        89845758  1953523711   931838977    5  Extended
/dev/sda5        89845760  1066405887   488280064   83  Linux
/dev/sda6      1066407936  1953523711   443557888   83  Linux

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000d4ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    48828415    24413184   83  Linux
/dev/sdb2        48828416   250068991   100620288   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000398931968 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x85d63c95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1          206848   835024895   417409024    7  HPFS/NTFS/exFAT
/dev/sdc2       835024896  3907028991  1536002048   83  Linux
robert@i3-2120:~$

robert@i3-2120:~$ sudo parted -l
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  16.0GB  16.0GB  primary   linux-swap(v1)
 2      16.0GB  46.0GB  30.0GB  primary   ext4            boot
 3      46.0GB  1000GB  954GB   extended
 5      46.0GB  546GB   500GB   logical   ext4
 6      546GB   1000GB  454GB   logical   ext4


Model: ATA TS128GSSD340 (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  25.0GB  25.0GB  primary  ext4
 2      25.0GB  128GB   103GB   primary  ext4


Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      106MB  428GB   427GB   primary  ntfs
 2      428GB  2000GB  1573GB  primary  ext4

---

### Post by yancek on 2016-03-06
External drive partitions are by default owned by root in most Linux systems.  If you can access the Linux partition from its mount point (under /media?), check the owner:group and permissions with this command:  ls -l /media/user/sdc  You will have to change 'sdc' to whatever the actual mount point for the partition is.  Then you can use the chown command to change the owner.  You can also run your command prefixing sudo to get root permissions.  I don't use BackinTime so don't really know what it is, GUI backup software?

---

### Post by Bucky Ball on 2016-03-06
Check where it is under /media. Probably /media/username/your_partition

> sudo chown -R username:username /media/username/your_partition

Replace 'username' with your username and the path with the correct path. An example might be:

> sudo chown -R bucky:bucky /media/bucky/data

Incidentally, you should have posted a new thread as this has nothing to do with resizing a partition using Gparted (and nothing to do with the message you were getting and asking about initially). Posting questions not related to the thread title on an answered thread decreases your chances of support.

---

### Post by HermanAB on 2016-03-07
The disk will always mount owned by root, unless you jump through a few more hoops.  Therefore the path of least resistance, is to make a directory on the USB disk owned by your user account:
$ sudo mkdir /run/media/myusername/partitionname/whatever
$ sudo chown myusername: /run/media/myusername/partitionname/whatever

Then everyone will still be happy when you plug it in again the next time.

---

### Post by Odyssey1942 on 2016-03-07
Between the three replies (thank you), I think I am beginning to get a handle on this. It appears that there are at least 2 issues:

I named the partition EXT4 For Linux. Maybe I shouldn't have used spaces (either omitted them or used underscores), but so far (CLI impaired) my attempts to rename it to EXT4ForLinux has been for naught.

It also makes me wonder if there is a limit to the length of the name? Is there?

Root ownership. My pathetic attempts to develop info yields that it is indeed owned by root, but until I can rename it, I probably cannot change ownership so we will take it one step at a time.

BB, I take your point. Yes, the original post was solved and I should have started anew in a different subforum, and still can if those currently involved fall away. But maybe we are close enough to nail it down quickly.

---

### Post by howefield on 2016-03-07
> **Odyssey1942 said:**
> I named the partition EXT4 For Linux. Maybe I shouldn't have used spaces (either omitted them or used underscores), but so far (CLI impaired) my attempts to rename it to EXT4ForLinux has been for naught.

You should be able to escape the spaces by using a backslash or enclosing in quotes.

Eg,

```
EXT4\ For\ Linux 
```
or
```
"EXT4 For Linux"
```

I usually use the backslash with spaces in file paths.

---

### Post by Odyssey1942 on 2016-03-07
In a total muddle. Been trying to progress this with GUI's (no joy at all) and CLI (which I do not know), but no cigar.

Here is what I know:

The drive shows as Disk /dev/sdc: 2000GB (see post #6) and I can see in the file browser:

--/media/Toshiba EXT, formatted NTFS which I (robert) have read and write privileges, and System Monitor tells me is /dev/sdc1, all of which is fine.
and
--/media/EXT4 For Linux (which I want to rename as EXT4ForLinux) which has root level permissions (which I want to change to robert), is formatted EXT4, and System Monitor tells me is /dev/sdc2

If someone will please walk me through the commands to rename EXT4 For Linux and change permissions (I am at /media$ in the CLI), I will be most grateful.

---

### Post by oldfred on 2016-03-07
I normally try to remember to change label when I format a partition. But if I forget or later need to change label use Disks.
Now with gpt there are two different labels, one if file system and one is partition. Disks lets you change both easily.

See also
man e2label
e2label <dev> <label>
tune2fs -L <label> <dev> 


You can see file system labels/name
sudo parted -l
If gpt partitioned this will show both filesystem and gpt label.
sudo blkid

Once I changed to Ubuntu from XP, I stopped using spaces.
I use justonename, CamelCase, or under_score.

---

### Post by Odyssey1942 on 2016-03-07
OldFred, thanks, but

If by "Disks" you are referring to the "Disk Utility" found under Applications/Accessories (in 12.04), I had tried that and because I don't know how to run that as Root, it will not permit me to change the label.

If you are referring to some other GUI, where can I find please (Ubuntu Software Center doesn't seem to know anything about "Disks")

```
e2label "EXT4 For Linux" EXT4ForLinux
```
gave error message > e2label: Is a directory while trying to open EXT4 For Linux
Couldn't find valid filesystem superblock.

```
robert@i3-2120:/media$ sudo mv "EXT4 For Linux" EXT4ForLinux
```
> mv: cannot move `EXT4 For Linux' to `EXT4ForLinux': Device or resource busy

---

### Post by yancek on 2016-03-07
>                               mv: cannot move `EXT4 For Linux' to `EXT4ForLinux': Device or resource busy                      

That would indicate the partition is mounted so unmount it and run the command again.

```
sudo umount "/media/EXT4 For Linux"
```

---

### Post by oldfred on 2016-03-07
You have to tell e2label which device.

Without label to change to, it shows current label
fred@Z170N:~$ sudo e2label /dev/sdb6
data

So your entry should be something like: 
sudo e2label /dev/sdc1 EXT4ForLinux

Not sure if quotes are required if no spaces or not.

---

### Post by Odyssey1942 on 2016-03-07
yancek, unmounted and re-ran command, and got this message:

> mv: cannot stat `EXT4 For Linux': No such file or directory

But in fact it did rename it to EXT4ForLinux, so I'm not fussy about how it worked

oldfred, since renaming now done, will ask again about "Disks"?

and for anyone, how to change permissions of EXT4ForLinux to robert (from root).

Thanks.

---

### Post by oldfred on 2016-03-07
To see where mounted if already mounted.
sudo mount

Mine is
/dev/sdb6 on /mnt/data type ext4 (rw,noatime,data=ordered)

Which is from this in fstab:
```
# Entry for /dev/sdb4 :
UUID=f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data ext4 noatime 0 2

```

Seems like a better way as you have more control over what is executable. See post #8 & 10 by morbius1.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data
#where $USER should be your login name
#or to see user
echo $USER 

Instead of /mnt/data you would use where ever you have mounted EXT4ForLinux

If just manually mounting using Nautilus by clicking on it, it will be in /media/$USER
If you have added a fstab entry then it can be whatever you used.
I still mount in fstab with UUID, but have told myself that mounting with labels might be easier.

---

### Post by Odyssey1942 on 2016-03-07
OldFred, I have greatest respect for your seemingly unlimited grasp of so many of these subjects, but I have reread yours and the links several times and do not feel any wiser. It is just way over my level of technical understanding.

To be honest, I am just trying to get my computers upgraded so that I can go back to work, which is piling up over the many days that I am spending trying to figure out how to do all this stuff. Just as an aside, I can certainly see, and completely sympathize with those who try Linux, but finally give up and go back to Windows where things are so infinitely simpler.

I will stick with this a bit longer, but at this point, I just want to move on an get back to work. If anyone can assist me in less technical terms, I would be so grateful.

Edit: To summarize (only the last two days of several), yesterday morning (or maybe it was Saturday), I started trying to back up my /home directory to a portable USB drive. So far I have managed, with your help, to rename the partition that I want to back up to, but still cannot write to it because it has root privileges (I don't know why as I certainly did not intend for this result) and I am not root. Arrrrrgh!

---

### Post by yancek on 2016-03-07
If the partition in question you want to give your user ownership is: /media/EXT4ForLinux  the command you need is:

```
sudo chown -R robert /media/EXT4ForLinux/
```

If you want your group to be the same as your user do:

```
sudo chown -R robert:robert /media/EXT4Linux/
```

The above assumes the user is actually robert.

> but finally give up and go back to Windows where things are so infinitely simpler.

Before you can learn Linux, you first need to unlearn windows which is very different.  Someone who started with Linux/Unix/Mac/BSD would have the same problems trying to learn windows.  If you've been using windows, you're familiar with it.

Windows, from it's start in 1985, focused very much on ease of use.  This was pre-internet so initially it wasn't much of a problem.  With the onset of the internet, the ease of use created enormous problems for microsoft because they didn't put much effort into internet security.  In fact, Gates stated in the July, 2004 issue of Fortune magazine that internet security was not a priority in the development of W95, W98 hence all the malware and viruses.

Anyhow, post back if you get it to work.

---

### Post by Odyssey1942 on 2016-03-07
Yancek, That changed the permissions to robert. And BackInTime appears to be happily doing it's thing. 

Thank you so much for getting me over that hump. I really feel guilty not being able to work this stuff out by myself and I do try. I read and read and read. And get confused. Unsure how to start. My computer experience goes back to the early 60's (so you will quickly figure out that I'm in my 70's) At my age, retention is a tiny fraction of what it was only 10 or 20 years ago, so most of what I read and learn doesn't stick very long at all, and certainly not from upgrade to upgrade. It really is interesting, but at the same time frustrating because I need help with every step of the way.

My computer experience started with Cobol and Fortran, way before Windows, debugging code with 8 console lights (one byte at a time). That was a billion years ago in computer progress. And yes, I come to linux/Ubuntu from a Windows background. Windows drives me crazy with its constant interruptions and neediness. Once in place and working, Ubuntu is an enormous pleasure by comparison.

The biggest part of my problem is that between upgrades, I am just pounding the keyboard on work and projects, so I'm just a plain vanilla user who values the rock solid operation of Ubuntu. So I forget what I learned on the last upgrade. I am now taking lots of notes each time with the objective of easing the path next time. Hopefully I will get to a place where I can do most of it without help. Big maybe!

Again, my thanks for your quick and direct help. I'll probably be back tomorrow with a new thread as I get started on the upgrade. Til then......

P.S. While I was writing the above, BackInTime backed up my /home to the portable drive, all 6.5 GiB. I hope that it is all intact.

---

### Post by Bucky Ball on 2016-03-07
Good news! You got there. Please mark as solved to help others (see first link in my signature at the bottom of the post). This will not close the thread to further discussion.

---

### Post by oldfred on 2016-03-08
Screen shot of Disks. Older versions of Ubuntu called it Disk Utility and it looks a lot different. Most of the extra functions are now behind icons, both upper right and gears under partitions.

---

### Post by pauljw on 2016-03-08
Just out of curiosity, what is the reasoning for reformatting the backup drive to ext4?  I have an IOmega 2T USB drive that is NTFS that I just plugged in and it works.  No muss, no fuss.

---

### Post by Odyssey1942 on 2016-03-08
Hello Paul, I am not very well qualified to answer that question, but I have asked it and as I recall the reasoning was that in the event of a restore, EXT4 avoids permission issues (or maybe does) where a backup from NTFS will have permission issues that will need to be adjusted.

Obviously NTFS is more flexible in that both Windows and Linux will read and write to it.

May I ask if you have ever had to restore from your NTFS and if so did you have any issues? And if so, please describe. Thanks.

---

### Post by yancek on 2016-03-08
>  (so you will quickly figure out that I'm in my 70's)

Well, that makes two of us.  It took me a while to realize taking notes saved a lot of time in the long run.  You've got a lot more experience with computers than I have.  I got my first personal computer about 15 years ago with W2K.  Don't know anything about programming, a 10 line script is a big accomplishment for me.

If you are backing up a Linux system or data, use a Linux filesystem on the backup drive partition.
If you are backing up windows, use a windows filesystem (ntfs).

> 
Obviously NTFS is more flexible in that both Windows and Linux will read and write to it.

ntfs isn't actually more flexible.  A default windows system is not even capable of reading a Linux filesystem.  The reason ntfs can be used is because Linux developers wrote software to enable read/write to ntfs.

---

### Post by Bucky Ball on 2016-03-08
A tip for you two: Zim. I use it for all handy bit; links, code, whatever. It is in the repositories. Check it out. Best part is you can search for specific notes easily. Just search for 'Grub' for instance and any notes you've taken about Grub are right there.

It is always on on my computer. Just sayin'. :)

---

### Post by pauljw on 2016-03-08
> **Odyssey1942 said:**
> Hello Paul, I am not very well qualified to answer that question, but I have asked it and as I recall the reasoning was that in the event of a restore, EXT4 avoids permission issues (or maybe does) where a backup from NTFS will have permission issues that will need to be adjusted.

Obviously NTFS is more flexible in that both Windows and Linux will read and write to it.

May I ask if you have ever had to restore from your NTFS and if so did you have any issues? And if so, please describe. Thanks.

Oh, well if that's the case I understand your desire to go thru the process and I'll be considering doing the same.   Thanks for that info.  

No, I have not had the need to restore as yet so I couldn't tell you if permissions would be affected.  Seems there is no shortage of things to learn. :)  Hope your upgrade goes smoothly.

Paul

Edit:  I just verified that you're correct about the permissions.  I'm going to be redoing my backup drive tomorrow.  Thanks again!!

---

### Post by oldfred on 2016-03-09
@BuckeyBall
> A tip for you two: Zim.
+1

Some users may be under the mistaken impression that oldfred knows something.
But he also uses Zim, sees someone else's good answer and copies it into Zim.
But even then sometimes has issues remembering what to search for. :)

---

### Post by HermanAB on 2016-03-09
OK, thanks for the tip.  I'll give Zim a try.  I use the notes utility on my Mac and it works great.  I've been looking for something similar on my Linux machines.  The simple sticky note utilities are not good, because they cannot search.

---

### Post by Odyssey1942 on 2016-03-09
Zim sounds like just what the doctor (the medical version being my new best friends) ordered. Thanks very much for that. Thanks also for all the empathy, and support. Absolutely could not do it without all of you.

BTW, some of these many issues are beginning to sound familiar so hopefully that is a sign of progress.

robert

---

