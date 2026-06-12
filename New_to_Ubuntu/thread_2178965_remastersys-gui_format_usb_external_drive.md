---
title: "remastersys-gui format usb external drive"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-10-05
I've just purchased:
750 GB Western Digital (WD) My Passport external 3.0 USB drive

with the intention of creating a live system that I can also use to back up my data.

when I tried to delete everything on the WD I got error essage saying
"My Passport Apps for Mac: Error removing file: No such file or directory
User Manuals: Error removing file: No such file or directory
TestPilotExperimentFiles: Error removing file: No such file or directory"

Now I think it might be advisable to format it in ext4 then run mastersys-gui to put make my system recoverable onto another computer when my current computer dies.

I've read around the topic for a few days, but confess I need the help of ppl more technical than me.

I was hoping to get a step by step guide to 
1. wiping WD properly (it's now got a massive amount of junk on it from earlier attempt)
2. Formatting it with ext4
3. using remastersys-gui (do I have to create partitions on WD, or will remastersys-gui clone my computer in it's current configuration for me? Now that I think more about it - unless my replacement computer is the same, this could be problematic and not meet my needs)

Thank you community in anticipation.

---

### Post by DuckHook on 2013-10-06
Let's tackle the cloning issue first:

It is not hard to clone your HDD so that it can be restored after a complete reformat. This is very convenient if you are replacing your HDD, for example. But unlike Windows where you want to preserve your licences (apps as well as the OS itself), it is usually more trouble than it is worth to clone for the sake of installing on a different computer. Many of us actually prefer to install fresh, and take the opportunity to clean our systems of accumulated cruft and dead apps/files. If enough time has elapsed, it is also a good opportunity to install a more current version. The important thing to bring over is the /home directory which contains all of your personal data. Because Ubuntu is free and the repositories are very complete, it is not hard to reinstall the rest from scratch.

Re: External drive. Some drives have firmware that makes complete erasure of the HDD difficult or even impossible, but I doubt that yours falls into this category. If you wish to wipe your HDD, then you must repartition it. This will replace your old partition table with a new empty one. For all intents and purposes, you will have wiped your old drive. However, you must be *extremely careful* when using partition tools. All data ought to be backed up before you even start. The primary cause of massive grief on these forums come from people who mishandled a partitioning. Usually, it is impossible to recover their data for them.

Partitioning can be done with the *Disk Utility* that comes bundled with Ubuntu, but I prefer *gparted* if using the GUI and *parted* if using the command line. The man pages for any of these commands give you the options you need. Depending on your own circumstances, it may actually not be wise to format this drive with ext4 which is only readable by Linux. If you want your external HDD to be readable by Windows machines, then you should format either in NTFS or FAT32. Or you can create multiple partitions, only the first of which is FAT32, for common use with Windows, whereas the remainder can be ext4.

ext4 does have many advantages over FAT32 including journaling, better error correction and recovery, much better resistance to fragmentation, and the ability to handle large files and large numbers of files. Basically, superior in every way. My own 500 GB external HDD has a small FAT32 partition at the start, and all other partitions are ext4.

---

### Post by Kevin McCready on 2013-10-06
Thanks
I'll probably take you advice, which seems to be not bothering with remastersys? But if anyone else want to chip in that would be good because to rebuild my machine to my specs wouldn't be easy. I work as a Chinese translator and have lots of specially tweaked systems and apps, not to mention all the mods I've made to ~/.config/openbox/lubuntu-rc.xml.  I've tried to document what I've done at each step of the way, but the best laid plans of mice and men ...

One thing I'm not sure about is why you have a partition of FAT32 at the beginning of your HDD.

---

### Post by DuckHook on 2013-10-06
Whole discussions and controversies surround the concept of backup strategies. Your needs are actually a tad more exacting than mine, so take what follows with all appropriate caveats, etc.

Firstly, re remastersys:

This is an app designed for hard-core users who like to spin their own distros, as it were. It is overkill for a backup routine, which only needs to restore your current system if the HDD or computer dies. Moreover, according to Wikipedia, it is currently being passed onto another maintainer, so its future is uncertain. But it also works for the task so you can use it if you don't mind the complexity. I prefer to keep things simpler.

Introducing, rsync:

If you ask most forum users, I think you will find that the majority of them find rsync to be the best and most painless way to create running backups. rsync is an app that syncronizes files between two HDDs. I sync mine as a cron job across the network to a NAS and also manually to an external USB drive (less frequently). The rsync+NAS solution is especially trouble-free and elegant because it occurs automatically in the background, without the need for intervention, and is therefore a no-brainer.

rsync can be set to sync only those directories and files that you want. Therefore, I do not sync my OS, which can be easily re-installed, nor my various virtual machines, which are numerous, made up of huge files, change frequently, and are also easily re-installed. The exceptions are my Windows VMs which I back up manually and infrequently. Instead, I backup the data within those Windows VMs using native Windows backups. Aside from the VMs and a few other exceptions, I back up my whole /home directory (which is actually on its own partition).

To be triply sure, my most critical files like accounting records, etc, are backed up yet again once a month to DVDs that I keep off site. Some call me paranoid, but I am reasonably secure against flood, fire and tornadoes. Many here also swear by cloud storage although I find the idea of keeping my sensitive stuff 'out there' to be scary.

It is not difficult to set rsync to backup your /root as well. This will make sure that all of those special tweaks are looked after. However, I am willing to bet that most of your customizations are actually on your /home directory. That's where apps tend to put their config files and settings. Even your mods to lubuntu are already on /home (as per your post).

Lastly, I have a FAT32 partition on my external drive purely for the sake of utility. It is the lowest common denominator among file systems and will work on Windows machines as well as Linux. It's at the beginning out of habit: Windows will only read the first partition of USB flash drives, so I create all USB-based storage the same way, even though this limitation does not apply on external HDDs.

---

### Post by Ghost_Mazal on 2013-10-07
I can understand the need for a clone. It is actually not so quick and easy to fresh install as most say. Depending on your apps and needs it can literally take up a few evenings just to get everything installed and updated again. Especially if your connection speed is slow and have capped data on your internet.

For easy clone imaging look into Redo backup. The most user friendly way to make an cloned image of your drive.
It is an iso you download and burn to cd. Boot with it , and then easily clone your drive.
There is another app for this called Clonezilla. But Redo backup is much easier and user friendly.

If you load back a Redo image in case of emergency your system will be exactly the same as it was when you made the image.

I usually image my pc once a week and make daily backups with something like grsync of /home and /var/cache/apt/archives
(the latter contains all the .deb packages of the apps you install and their updates. So in worst case scenario if you have to re-install you can copy
those back and at least save the time and data to download everything again as it will see and install them from your hdd )

---

### Post by DuckHook on 2013-10-07
This is workable for one type of installation, but not others. In my case, I have over 800GB of VMs alone. Cloning such quantities of data would take several hours every week and would just be pointless duplication and very resource intensive. If a user rsyncs everything, from / to /home, then this essentially *is* a clone, but with enough fine control to exclude unneeded files like experimental VMs. To restore, install a basic command line system on the new HDD (15 minutes max), then reverse the usual direction of the rsync command, and voila, complete and painlessly restored system. However, as mentioned in my initial post, if a user prefers to clone, whether with remaster.sys, Redo or Clonezilla, I have no objections. It just seems to be duplicated effort and a needless complication.

Your point about a fresh install being difficult and time-consuming for some people with slow or limited connections is a valid one. However, by including the whole system in rsync, you are performing a full backup/restore, so there is no need to download anything.

@OP

rsync is dead easy to use and even easier if you wrap it in a GUI with grsync. As with all things Linux, it costs you nothing to try all the methods suggested and choose the one that works best for you. Happy Ubuntuing!

---

