---
title: "Partitioning like Windows"
date: 2022-01-10
forum: New to Ubuntu
---

### Post by haszeich on 2022-01-10
Hello, I recently installed Ubuntu 20.04 LTS and I am trying to partition my 2 SSD's: one for system files(the usual C: drive on windows) and the other for games, pictures and programs(commonly D: on Windows). I already installed ubuntu on the 500GB drive but I have only managed to 'mount' the other drive. Can I organize my files the same way I used to do it on Windows or is 'mounting' the only way to go?

---

### Post by TheFu on 2022-01-10
a) The term "drive" is actually incorrect.  In both Windows and Linux, the term "partition" is accurate. It really is too bad that MSFT decided to name something incorrectly which leads those users to unnecessary confusion. On Windows, your C: and D: "drives" really are partitions.  There is a huge difference and for Linux, it matters greatly. Use the wrong device and you'll corrupt the data.

b) In Unix/Linux, we mount file systems.  Those can take up an entire partition or use some volume manager like LVM if you need/want advanced management capabilities.  The mount location is just an empty directory anywhere except the top directory, /.   Besides that, you can mount anywhere, but there are common things that get mounted to specific locations.  For example, it is very common to have a separate partition for /home/ which is where all the files for each userid are typically (but not required) placed.  There are instructions for "moving HOME to a new partition" in the ubuntu wiki.

c) Another method to make access to additional storage is to use symbolic links from your HOME directory to another partition.  For a long time, NTFS didn't have any similar idea to the Unix symbolic link that has been around 50+ yrs.  Basically, you'd mount the 2nd partition to /media/{username}/docs then create a symlink from your HOME to that location.  ln -s /media/{username}/docs ~/Documents is the command.  Just be certain that any existing ~/Documents directory has been removed first.  It is impossible to create a file system object (file, directory, symlink, etc) if other file system object already exists with the same name, in the same location.

Lots of people use this method, outlined in "c)" too.

The main issue with any of these techniques is ensuring that your backups capture all the locations with files you don't want to lose. Most backup tools copy the symbolic link as a link file, but don't follow it and backup where it points.

So ... here's an example file system setup:
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                        SIZE TYPE  FSTYPE      MOUNTPOINT
sda                       465.8G disk      
&#9500;&#9472;sda1                      512M part  vfat        /boot/efi
&#9500;&#9472;sda2                      732M part  ext2        /boot
&#9492;&#9472;sda3                    464.6G part  crypto_LUKS 
  &#9492;&#9472;sda3_crypt            464.6G crypt LVM2_member 
    &#9500;&#9472;ubuntu--vg-root        25G lvm   ext4        /
    &#9500;&#9472;ubuntu--vg-swap_1     4.5G lvm   swap        [SWAP]
    &#9500;&#9472;ubuntu--vg-home--lv    75G lvm   ext4        /home
    &#9492;&#9472;ubuntu--vg-stuff      100G lvm   ext4        /stuff
```
Ignore the sda3_crypt line. I use an encrypted container in the sda3 partition. Doesn't matter to you.
As you can see, I have /home as a different "partition" (it is actually an LVM-logical volume, but for this discussion, consider it a partition).
/home gets backed up.
/stuff does NOT get backed up.  Everything in /stuff is actually stored somewhere else where it gets the real backups.

Inside my HOME directory, I could easily access all the storage in /stuff by creating a symbolic link to that directory.
Also, note that these partitions all use native Linux file systems, not NTFS.  This is important, since NTFS doesn't provide the expected capabilities needed for most Linux programs related to owner, group, permissions and ACLs.

You might notice that sda3 is 460G in size, but my "partitions" only add up to be less than 250G.  Here's the actual storage used today:
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                      Type  Size  Used Avail Use%
Mounted on
/dev/mapper/ubuntu--vg-root     ext4   25G   18G  5.9G  75% / 
/dev/sda1                       vfat  511M  4.5M  507M   1% /boot/efi
/dev/sda2                       ext2  721M  176M  509M  26% /boot 
/dev/mapper/ubuntu--vg-home--lv ext4   74G   23G   48G  33% /home 
/dev/mapper/ubuntu--vg-stuff    ext4   99G   65G   30G  69% /stuff
```
There is plenty of excess storage available both already there and unallocated. The power of LVM is being able to add storage to an existing LV easily, later, but that only works if the pool VG has unused space available. It takes about 5 seconds to extend an existing LV where and when it is needed. The system doesn't need to be stopped, rebooted, or anything else. The extend command can be used while the file system is active, being used. That's very handy.

---

### Post by oldfred on 2022-01-10
I still use standard partitions, not LVM.
Back with XP I had two data partitions, one NTFS for some data I wanted to share with Windows and then an ext4 (back then it probably was ext3?) for Linux data. Now no Windows but still have at least one main data partition, but may split some data into another partition. I have found some data grows faster (like grandkids photos). I have to plan a bit more than with TheFu's LVM as partitions are not as easy to resize. But I also do not fully partition a drive & leave some room for future.

I have multiple installs, and therefore keep /home inside / but have all data in data partitions. I do not want main working install's /home corrupted by some experiment I may try in a second install. But can have all my data in every install mounting & linking the data.

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by TheFu on 2022-01-10
> **oldfred said:**
>  I have to plan a bit more than with TheFu's LVM as partitions are not as easy to resize. But I also do not fully partition a drive & leave some room for future. 

This can work. The trick is to leave sufficient space AFTER each partition so expending into that space provides a little buffer - perhaps long enough to get more storage and move some of the data to a different partition.  Maybe 10-20G AFTER each partition would be sufficient for that planning.  With 500GB-14TB HDDs, leaving that little bit of slack isn't too wasteful.

So, on my 500GB HDD (example above), the space for the OS and boot files would use about 40GB total.  I'd leave 20G after that for the future.
Next I'd create a partition for /home ... say 50G per userid to start, but leave at least 50G unused AFTER this partition.
Next I'd create a partition for stuff - /stuff ... I'd start it around 250GB into the drive, so all the space from AFTER the /home to the start of the /stuff would be empty for future needs.  Same for /stuff.  Start with 50G, but leave the rest unused for future needs.

If it isn't clear, expanding simple partitions "to the right" is easy, but expanding them "to the left" is hard work.

I started using this technique long ago on Windows.  There always seems to be wasted space, but that is the price for flexibility.
Regardless, symolic links are helpful to make accessing storage on a different partition easier.

---

### Post by GhX6GZMB on 2022-01-10
I think you both have been 100% successful in scaring a new Ubuntu user away.
Congratulations. "No need for greenhorns here, eh? Let's keep the club exclusive (chuckle, pull on cigar)".

Seriously, @TheFu and @oldfred, your carpet-bombing newcomers with detailed information reaching into the farthest crevices of Ubuntu is not helpful.
Step-by-step is the way to go.
I was once a newcomer myself, and even though I work with Lubuntu for more than two years now, your replies often go 100% over my head.

Try to step back, think, and either let another newcomer reply (who's got these issues much closer), or try to be just a little bit pedagogic.

I respect your knowledge immensely, this is just an appeal For "soft-starting" with new users.

Cheers.

---

### Post by QIII on 2022-01-10
I'm not sure that after 4 hours I would assume that anyone has been scared away.

Both TheFu and oldfred have been helping newcomers here for many years.  Personally, I'm happy to defer to their judgement.

---

### Post by TheFu on 2022-01-10
> **ml9104 said:**
>  I respect your knowledge immensely, this is just an appeal For "soft-starting" with new users.

Rather than complain, please offer the easier method that does what this user wants.  The goal is to help him/her resolve what they want. There are 50+ ways to solve anything and if you have an easier method, we'd all love to know it.

It is hard to know what background anyone may or may not have when they post here.  Some first time posters have 25 yrs of computing experience and don't want to be talked down to.  Others have always had an IT department and barely know to click the "email" and "web" icons on an existing desktop.  I've found no method to determine the level of experience/expertise any poster is accurately, even when they say "I'm new to Ubuntu."  That doesn't mean they don't have 5 yrs of Fedora or 20 years of BSD or Unix knowledge.

If you have a different option or you know that something posted by me is incorrect, please, please, please, provide the alternative and say what I got wrong.  Simple, accurate, information is the goal, but there are often subtle things that should never be assumed. I think that's where I excel - noting those subtle issues.  

In the end, the method that actually works for the poster is the one we need and want.  Any post that goes towards that goal is appreciated, at least by me.

---

### Post by The Cog on 2022-01-10
Simplifying things down a bit:
I will assume that you intend to place one partition of each of your SSDs. I gather you have already installed Ubuntu on first SSD. This gives you a chance to look around and get familiar with the folder layout. Maybe too detailed for now: [https://linuxhandbook.com/linux-directory-structure/](https://linuxhandbook.com/linux-directory-structure/)

If you look at the directory structure, you will see a /home directory under which you will find a separate directory for each user you create. User root is an exception that has its home directory off of the top level instead, but ignore that - it's not something you will be using much, if at all. So for instance, all your personal documents and settings will be in /home/haszeich. Normal users rarely if ever store data outside of their own /home/username folders. I would suggest that you use your second drive to store the /home directory. This is what I do. It is about the closest you will get the the Windows C: and D: arrangement - system on one drive, user data on the other.

Mounting a drive involves making a drive's contents appear in an existing directory (if the directory was not empty, the original contents become hidden until the drive is unmounted again). This is the **only** way to get to see the contents of another drive. Removable drives often get auto-mounted in temporary directories such as /media/backup1
So what you probably want is the first drive (sda1 perhaps) to be the root drive and the second drive (sdb1 perhaps) to be mounted at /home and contain user's home directories.

The easiest way to achieve this is by choosing "something else" at the partitioning step of the installer program. Put one partition on each drive formatting them as ext4, use first drive and /, and the second drive as /home. The installer will configure the system to mount /home at boot time, so that the first user's home directory is stored on the second drive as you wanted.

It is possible to move /home to a separate partition after install, but there is some fiddling:
* Mount the new drive to a temporary location (e.g. /mnt/tmp)
* Copy the existing /home contents to /mnt/tmp
* edit /etc/fstab (defines what mounts where) to mount the new drive as the system boots
* reboot
As long as the second drive is mounted at /home, the original /home contents remain hidden (and unchanged).

Hope this helps.

---

### Post by GhX6GZMB on 2022-01-10
Putting yourself in the place of someone who's only been used to DOS/Windows is not easy.

The first question is: "where's the C: or D: drive?"

Explaining that UNIX/Linux/Ubuntu only has a directory tree and nothing else is the first mental major leap.
Then, explaining that HD-resources must be assigned to the places in the directory where storage is needed is the second one.

When these two points are fixed in the mind of the newcomer, progress is possible.

It's a major mindset twist that takes some of time and mental effort.

These are totally basic things that s newcomer may be totally alien to, which led to my post.

Your work/inputs are 100% valued, no question there.

Cheers.

---

### Post by The Cog on 2022-01-10
I have to agree with that bit of mind warp. The idea that all of this directory tree lives on one disk, apart from **this particular** directory and its contents, which lives on a completely different disk can be a very alien concept to ex Windows (or DOS) users. 
And then there's /dev which is full of device driver interfaces that look like files, and /proc and /sys that show internal operating system data made to look like files (just figments of the OS's imagination, hallucinations almost). Yikes!

---

### Post by TheFu on 2022-01-10
> **ml9104 said:**
> Putting yourself in the place of someone who's only been used to DOS/Windows is not easy.

Very true, especially if your main OS has been Unix since 1990 and was MVS before that.

There are thousands of little details that we forget to mention, since we'd never get around to answering the question.  That's why inputs and ideas by lots of different people filling in details is so helpful.

/dev/sda is a drive. The whole drive.
/dev/sda1 is the first partition on sda.
/dev/sda2 is the second partition on sda.
See the relationship?

So, if a Windows user has 2 physical disks, fully allocated as NTFS - C: for the OS and D: for data, then it is probably using /dev/sd[COLOR="#FF0000"]a[/COLOR]1 for C: and /dev/sd[COLOR="#FF0000"]b[/COLOR]1 for D:.   That translation can be confusing at first.  Since technically, C: and D: aren't drives, they are partitions.  Again, Linux tools will say "partition" for those slices on a drive. "Slices" is a Unix term, not often used by Linux, but almost always used by other Unix-like OSes. Ignore it. I just needed a different term than partition for something less than the whole drive.

---

### Post by GhX6GZMB on 2022-01-10
There you go again...

---

### Post by yancek on 2022-01-11
If you understand that "mounting" simply means to "make accessible", things will be a lot simpler for you.  Windows "mounts" partitions also they just don't use the terminology.

If you want to put programs on a separate drive or partition from the system partition it is not likely to work as libraries on the system partition are needed.

Your statement about the C and D drive is basically accurate but only if you have a single boot windows.  Otherwise, it gets confusing pretty fast.  And as stated above, C, D, E, etc. in widows can refer to either a hard drive or simply a partition on a hard drive and this is something which seems to confuse users who are switching from windows to Linux.  Mounting isn't the problem for a user who want specific programs on a specific partition.

---

### Post by rsteinmetz70112 on 2022-01-11
The idea of Drive Letters I think predates the original IBM PC DOS and even its predecessor CP/M. I believe IBM, among others used it in some of their earlier operating systems. In any event when early PCs were around they rarely had hard drives but often had 2 floppy drives A: and B: later as hard drives because popular it was common to name them C:. Even later the number of these drives proliferated and became something different. 

Unix never had this convention and as far as I know always operated as a single hierarchical file system starting at / and continuing on from there. Storage can be mounted at any place on the tree.

---

### Post by yancek on 2022-01-11
Back in the 1970's, it was common to name the hard drive C because, as you said, most computers at that time came with 2 floppy drives (A and B) and often had no hard drive so when there was a hard drive, I guess it would have been logical to call the drive/partition C.

It was interesting to dual boot windows and my first experience with it was first using W98, then installing to dual boot with W2K.  When I did this, W2K placed itself on a logical partition (shown as sda5 in Linux) and W2K put its boot files on the first primary partition where W98 was installed.  This was easy to see as the boot files for W98 were different from W2K.  This being all new to me, I was surprised to see when I booted W98 that it showed system files as C partition and the 2nd windows partition (W2K) as the D partition and when I booted W2K, it showed it system as C and W98 as D.

---

### Post by haszeich on 2022-01-12
Thank you for the support, I have managed to partition first SSD as / and the second one as /home as @The Cog suggested following a reinstallation of the OS

---

### Post by The Cog on 2022-01-12
Great news. 
It may be worth re-reading the earlier posts now you have seen the basics work, but don't sweat it too hard - you have plenty else to chew on with an unfamiliar OS.
You can mark the thread solved using the Thread Tools pull-down top-right of the page.

---

### Post by GhX6GZMB on 2022-01-12
> **haszeich said:**
> Thank you for the support, I have managed to partition first SSD as / and the second one as /home as @The Cog suggested following a reinstallation of the OS

Great. Thumbs up, you're on the right way :)

---

