---
title: "Remove all partitions not windows or ubuntu 12.10, including separate home partition."
date: 2012-11-26
forum: New to Ubuntu
---

### Post by Rick Campbell on 2012-11-26
Looking for a safe way to clean out old partitions.  I can't find which partition is which even for the separate home directory I want to remove.  Don't want to remove boot record's partition.  
Can I delete with gparted from live cd 12.10 everything that's not running with the little key showing beside it aside from windows' partitions?

---

### Post by em3raldxiii on 2012-11-26
Hey Rick, I am not 100% sure but I don't think that's quite the best solution.  Others will likely clarify for us here, but I think the first thing you want to do is have a look at your FSTAB file to see which partition is which.

```
gedit fstab
```

(it should be read-only without sudo, so this is safe to run).  

In there will a reference to your hard drive partitions and how they are mounted in Ubuntu.  Your Windows partition(s) will most likely be formatted to NTFS or FAT32 or some other Microsoft filesystem, and those should be indicated when you fire up GParted.

Removing the /home partition on Ubuntu (or any Linux) could potentially be disastrous by breaking a number of configuration settings.

I hope that gets you some points to start from.  With any luck, someone else will chime in ...

---

### Post by DuckHook on 2012-11-27
Please tell us your objective and give your current system layout. If objective is to remove older versions of Ubuntu, then you must be sure how your system is set up so that you remove only those partitions that are not essential to 12.10 and Windows. If this is a virgin install of 12.10 with no prior Linux system, then there is nothing that can be removed.

Your stated approach is dangerous and will likely end in tragedy. When you boot from a Live-CD, every partition in your HDD is open to deletion. This includes Windows and Ubuntu 12.10. Therefore, you must first determine which are your indispensable partitions before  even thinking about modifying them. Here are the steps I would recommend:

1. Back up all of your important data to an external drive/USB stick and check that the backup is good. This is by far the most important step. With a good backup even the worst screw-up becomes an annoying inconvenience whereas without a backup, it's a disaster.

2. In a terminal, type (or copy and paste) the following:

```
sudo parted /dev/sda print > ~/Desktop/partition_table
```

This should generate a file on your desktop with the name "partition_table" that contains your partition info. It will look something like the following (yours will look different depending on what and how you installed):

```
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End    Size    Type      File system  Flags
 1      1049kB  105GB  105GB   primary   ntfs         boot
 2      105GB   205GB  100GB   primary   ext3
 3      205GB   207GB  1999MB  primary   linux-swap
 4      207GB   500GB  293GB   extended               lba
 5      207GB   500GB  293GB   logical   ntfs
```

We are trying to understand your partition layout first before modifying or deleting anything.

3. Post this info back to this thread. Either attach the file or post its contents.

---

### Post by Rick Campbell on 2012-11-28
Model: ATA TOSHIBA MK2035GS (scsi)
Disk /dev/sda: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

```
Number  Start   End     Size    Type      File system     Flags
 1      1049kB  10.5GB  10.5GB  primary   fat32           boot, diag
 2      10.5GB  105GB   94.8GB  primary   ntfs
 3      105GB   109GB   3696MB  primary   ntfs
 4      109GB   200GB   91.1GB  extended
 8      109GB   123GB   13.9GB  logical   ext3
 9      123GB   128GB   5126MB  logical   ext4
19      128GB   134GB   5574MB  logical   ext4
15      134GB   142GB   8036MB  logical   ext4
11      144GB   149GB   4987MB  logical   ext4
17      154GB   155GB   1062MB  logical   linux-swap(v1)
16      155GB   164GB   8709MB  logical
12      165GB   166GB   937MB   logical   linux-swap(v1)
10      166GB   168GB   1892MB  logical   linux-swap(v1)
 6      168GB   173GB   5280MB  logical   ext4
18      173GB   183GB   10.2GB  logical   ext4
13      183GB   191GB   7572MB  logical   ext4
14      195GB   196GB   577MB   logical   linux-swap(v1)
 7      196GB   197GB   1250MB  logical   linux-swap(v1)
 5      197GB   200GB   3076MB  logical   linux-swap(v1)
```


See, what a mess.  I'm so ashamed.  I have a separate home partition set up for personal pictures and stuff I never use.  It says it's 14GB but I can't tell which one it is.
Thanks for helping.

---

### Post by DuckHook on 2012-11-29
No need to be embarrassed. I'm sure many people have even more convoluted partition tables. I take it that you have installed many versions of Linux over time and each time chosen the "install alongside" option?

First, a brief explanation of what this info is telling us:

Partitions 1, 2 and 3 contain your Windows installation and must not be deleted. Partition 4 is an extended partition that has been subdivided into all of those numerous logical partitions and contains all of your Linux installations including the Ubuntu 12.10 you want to keep. If we determine which partitions belong to 12.10, then we can delete the rest without impacting your usability. And just so you know, you cannot simply delete your /home partition because Ubuntu uses it to store your profile including such essential things as your desktop, email, etc. These are in hidden directories, so they are not easily noticeable to you.

Please boot into your 12.10 installation (it's very important that you boot into the installation that you want to *keep*) and type the following:

```
df -l > ~/Desktop/disk_layout
```

This will produce a file named "disk_layout" on your desktop. Post that info back to this thread.

We are very close to knowing what we need to know. Just a little housekeeping (along with proper backup) will soon tidy everything up.

---

### Post by audiomick on 2012-11-29
> **Rick Campbell said:**
> 
```

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  10.5GB  10.5GB  primary   fat32           boot, diag
 2      10.5GB  105GB   94.8GB  primary   ntfs
 3      105GB   109GB   3696MB  primary   ntfs
 4      109GB   200GB   91.1GB  extended
 8      109GB   123GB   13.9GB  logical   ext3
 9      123GB   128GB   5126MB  logical   ext4
19      128GB   134GB   5574MB  logical   ext4
15      134GB   142GB   8036MB  logical   ext4
11      144GB   149GB   4987MB  logical   ext4
17      154GB   155GB   1062MB  logical   linux-swap(v1)
16      155GB   164GB   8709MB  logical
12      165GB   166GB   937MB   logical   linux-swap(v1)
10      166GB   168GB   1892MB  logical   linux-swap(v1)
 6      168GB   173GB   5280MB  logical   ext4
18      173GB   183GB   10.2GB  logical   ext4
13      183GB   191GB   7572MB  logical   ext4
14      195GB   196GB   577MB   logical   linux-swap(v1)
 7      196GB   197GB   1250MB  logical   linux-swap(v1)
 5      197GB   200GB   3076MB  logical   linux-swap(v1)
```

...It says it's 14GB but I can't tell which one it is.

The only one that is 14GB is number 8.

Do what Duck Hook is suggesting, though. Don't just start erasing things blindly.

---

### Post by newb85 on 2012-11-29
> **audiomick said:**
> Don't just start erasing things blindly.
Indeed.  I once erased my Windows partition by mistake.  The only consolation there was that it took a couple months to realize the mistake.  ;)

---

### Post by Elfy on 2012-11-29
I'd start by looking at what these tell you, should be able to see which is your home and /
```

cat /etc/fstab 

df -h
```

---

### Post by coffeecat on 2012-11-29
> **Elfy said:**
> I'd start by looking at what these tell you, should be able to see which is your home and /
```

cat /etc/fstab 

df -h
```

+1

@Rick Campbell, also  - you have 6 swap partitions. If you are clearing out everything except your 12.10 installation, you will only need the swap partition associated with 12.10. In addition to everything else suggested, run:

```
sudo blkid
```

That will list all the UUIDs for the partitions. Find the UUID for swap for the system(s) that you want to keep in /etc/fstab and keep that one. The others can go. It's better to check the UUID because, although there will be a comment line in /etc/fstab telling you which partition number (e.g. "/dev/sda7") swap is, subsequent partition manipulation may have renumbered that one. Better to rely on UUID.

---

### Post by Bartender on 2012-11-29
1) Back up whatever personal data you have in your 12.10 install.
2) Using the Ubuntu LiveCD or a GParted LiveCD, delete every partition inside the extended partition.  Keep the extended partition, don't delete that.
3) Install Ubuntu to the free space inside the extended partition.

Wouldn't that be much simpler, and less likely to cause problems with a confused GRUB and/or fstab file, than trying to remove all the unwanted partitions?  Also avoiding potential problems if/when the OP attempts to expand the one desired installation into the freed-up space...

---

### Post by DuckHook on 2012-11-29
@Elfy, @coffeecat & @Bartender all have excellent suggestions that solve the OP's issue. All I need do is explain:

To Rick Campbell:

@Elfy & @coffeecat are providing instructions that allow you to see which of the partitions belong to your current 12.10 install.

```
cat /etc/fstab
```

will output something like the following (yours will be different):

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx none            swap    sw              0       0
```

```
df -h
```

will produce something like the following (again, yours will be different):

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  3.0G  8.0G  28% /
udev                  239M  4.0K  239M   1% /dev
tmpfs                 100M  784K   99M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  248M  160K  248M   1% /run/shm
none                  100M  8.0K  100M   1% /run/user
/dev/sda2              25G  5.6G   18G  25% /home
```

In both cases, the parts that say "/dev/sda?" where "?" is a number will tell you which partition is being used by your 12.10 install. This is why you must invoke these commands *while you are running your 12.10 system*. Knowing which partition number is the one you want to keep means that you can delete the rest.

@Bartender's suggestion is somewhat different, but also quite valid. He/she is recommending that you nuke **all** of your Ubuntu/Linux logical partitions (which all reside inside partition #4--the extended partition) and just reinstall 12.10. This will allow GRUB to detect your Windows installation and set up one and only one clean pristine version of 12.10 for a simple dual boot machine.This has the added advantage of not confusing GRUB when it tries to find all of those missing older versions after their partitions have been deleted.

At this point, the choice is really yours. If you have lots of programs, data and configurations in your 12.10 installation, then you may find it less irritating to delete the partitions you don't want. If you don't have much of anything in your 12.10 installation, then you may just want to start fresh and follow @Bartender's instructions.

---

### Post by Rick Campbell on 2012-11-30
Thanks everyone.  Fun for me.

Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda19       5358008 3192908   1892924  63% /
udev              501140       4    501136   1% /dev
tmpfs             203552     904    202648   1% /run
none                5120       0      5120   0% /run/lock
none              508876     676    508200   1% /run/shm
none              102400      36    102364   1% /run/user

I thought I was using 12.10's home because it is empty each new install.

---

### Post by Rick Campbell on 2012-12-01
I opened gparted from ubuntu 12.10 cd and deleted partition 19 and 18 but 17 was mounted with a little lock icon and 16 said it needed me to unmount it.
Hm.
Can I delete the "unallocated" partitions too?
Still running, and I feel so much lighter already.

---

### Post by Bartender on 2012-12-01
Hi, Rick -
It's not hard to [unmount partitions]("http://gparted.sourceforge.net/display-doc.php?name=help-manual#gparted-unmount-partition") when running from an Ubuntu LiveCD.  

However, I've never followed the instructions.  What I do once or twice a year is just download the latest .iso version of the stand-alone [GParted LiveCD]("http://gparted.sourceforge.net/download.php").  After downloading the latest version, I use Brasero (or ImgBurn on a Windows PC) to create a bootable CD from the .iso.

Then I boot from that disc.  A GParted LiveCD doesn't mount any partitions, so there's no unmounting.  It just makes more sense to me.

---

### Post by Bartender on 2012-12-01
> **Rick Campbell said:**
> Can I delete the "unallocated" partitions too?


What do you mean?  Isn't the "unallocated" space just free space?  Usually unallocated means there isn't a partition.  Except, of course, when the unallocated space is 'inside' an extended partition.

When you're done deleting unecessary partitions, you *should* be able to expand the partitions you want to keep into the unallocated space.

However, there is always a risk when moving/expanding partitions that contain data.  Especially the bootable partition with the OS.

---

### Post by Rick Campbell on 2012-12-01
Thanks.  
All the viewpoints are speeding the learning process.
I right clicked on the mounted partitions and turned swap off and then was able to delete everything.  Cool.
Now, installing without auto in the partitioning...  it asks me where I want to put / or /home so when I put / in my huge free space it formats to ext4 but then says I should have a swap partition to go with it.  
I love it.  Operating Systems that talk.
Should I have made swap first with about 4 MiB in it?  First time not using auto install.  I know you guys, Bartender, DuckHook have read volumes on this and are saving me reading time but this sure is fun learning partitioning with the real thing.  Now I know what they are talking about in the tutorials.
Can I spare you guys by just choosing the automatic partitioning now?

---

### Post by Bartender on 2012-12-01
Rick -
I was under the impression that you were going to try deleting select partitions and keep the ones you wanted.  

Have you now decided to wipe them all and start over?

If so, choose "Something Else" and when you get to the partition table, just choose to install Ubuntu into the emptied out extended partition.  If that's what you have now.  You can manually partition swap if you want to.  It might be a little confusing the first time but it sounds like you're up for it.  Just carve out a small partition (a bit more than your installed RAM if you want suspend) and format it as "linuxswap".  It'll be a brown color if you did it right.  Then you can just leave the rest alone if you want and tell the installer to install Ubuntu to that extended partition.

There are small tweaks to the Ubuntu installer almost every time a new versioncomes out, so I'm not sure what you're saying about the installer mentioning a swap.  If that's what it wants, just go ahead and make one manually.

ANOTHER ROUTE IF YOU WANT TO MANUALLY PARTITION / & /HOME:
If you want to manually partition / and /home from the "Choose Something Else" window, you just carve out about 15 or 20GB for /.  Format it as ext4, and make SURE to mount it as /.  Then create swap as described above.  The swap partition doesn't have to be "mounted", just format it as linuxswap and the system will do the rest.  Whatever's left out of the extended partition, create another ext4 partition, and make SURE to mount it as /home.  Double-check that you have a partition mounted as /, a swap partition, and another partition that will mount as /home, then move on to the next step.

I don't think it makes any difference whether swap is created before /home or after.  I always create the / partition first, then swap, then /home, but I just do it that way out of habit.

---

### Post by Rick Campbell on 2012-12-01
Yes, I deleted all and installed automatically:

Model: ATA TOSHIBA MK2035GS (scsi)
Disk /dev/sda: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  10.5GB  10.5GB  primary   fat32           boot, diag
 2      10.5GB  105GB   94.8GB  primary   ntfs
 3      105GB   109GB   3696MB  primary   ntfs
 4      109GB   200GB   91.1GB  extended
 5      109GB   199GB   90.0GB  logical   ext4
 6      199GB   200GB   1062MB  logical   linux-swap(v1)

---

### Post by Rick Campbell on 2012-12-01
How do I look now:

Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda5       86526336 3157256  78973768   4% /
udev              501140       4    501136   1% /dev
tmpfs             203552     856    202696   1% /run
none                5120       0      5120   0% /run/lock
none              508876     156    508720   1% /run/shm
none              102400      48    102352   1% /run/user

---

### Post by DuckHook on 2012-12-02
Sorry. Been travelling past 2 days and completely off-line. In the interim, it seems that you've picked up the ins-and-outs of partitioning real fast. Congrats!

Looks to me like you've got a vastly simplified system now that should work well. If you want us to look at (admire?) the end result, do:

```
sudo parted /dev/sda print
```again, and post the result. I suspect that it will now have just your Windows partitions and a very simple Linux install on the extended.

For your future installs, I would highly recommend (at some point) a separate /home partition (doesn't look like you went with one here) and then simply *replacing* the current version (instead of *alongside*. Hope you followed the good practice of backing up all critical data before your did any of this.

If everything is running well, please mark this thread "solved" using the thread tool at top of page. And again, congrats on furthering your partition knowledge.

edit: ouch! Overlooked your prior post. You've obviously already shown us your new partition table and it looks real clean. You are go for liftoff

---

### Post by Bartender on 2012-12-02
Looks like swap came out smaller than the OP wanted, but that's not a deal-breaker.  Rick, you could go in with gparted and expand the swap partition if you really wanted to.  Better to do it right now than wait.

On the other hand, if it's not something that's going to keep you up at night, just let it ride.  Not a big deal if you've got enough physical RAM and don't care about hibernating (or is it suspending?) the PC.

To be honest, I'm not sure what "enough" physical RAM is these days so that the OS doesn't try to write to the swap partition.  Is it 2GB?  4GB?

Plus you can tell the system to avoid using swap by tweaking swappiness.  Hey, here's a good [article]("https://help.ubuntu.com/community/SwapFaq") about the subject.  I'll have to read it.  Sheez, there are some complicated directions.  I thought you could just push one partition aside and expand swap but looks like it's more complicated than that...

Towards the end of the article it mentions that swap is needed for hibernation.  Hibernate, sleep, suspend, argh

---

### Post by newb85 on 2012-12-03
[QUOTE=Bartender;12384719}Towards the end of the article it mentions that swap is needed for hibernation.  Hibernate, sleep, suspend, argh[/QUOTE]

Yes, but hibernation is disabled by default in the last couple releases of Ubuntu, since it doesn't work right with all systems.  Unless the OP plans to re-enable it, it doesn't need to be a consideration in swap.

I'm sitting on 6GB of both swap and RAM, and I don't think my swap ever goes above a few MB.  (But then, maybe I don't tax my system enough.)

---

### Post by Bartender on 2012-12-03
newb -
Thanks for the update.  Too often I reply with old news that's been true for years, but now changed, and I didn't get the memo.

---

### Post by Rick Campbell on 2012-12-09
Thanks guys.
My Ubuntu has always been lightning fast.
I needed this clean-up so I can speed up my Windows Vista O.S.
I know.  Delete it.
But I still need it for QQ instant messenger.
Wish I could expand Windows partition.

---

