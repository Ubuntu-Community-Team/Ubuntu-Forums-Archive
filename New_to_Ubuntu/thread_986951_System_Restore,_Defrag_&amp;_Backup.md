---
title: "System Restore, Defrag &amp; Backup"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by futuroimperfetto on 2008-11-19
Hi,

 There are a few things that I used to do when I was using Windows XP which I don't do anymore. I would like to ask if there are equivalents to the following features Win XP had:

[SIZE="3"]**(1) Is there a System Restore?**[/SIZE]

When something went bad in XP, I used to go back to a previous system restore point and most of the issues would be solved. Now in Ubuntu I trust that when I do "remove" I do it for good, so no dirt is left behind, but still... Is there anything equivalent to take a snapshot of the settings at a given time?

[SIZE="3"]**(2) Is there a hard drive Defragmentation command?**[/SIZE]

I've read here and there that the Linux file system is different that the Windows one and that I would not really need to defragmentate my hard drive.

However, two days ago I had a problem with a corrupted folder and had to erase it. I'm wondering if it left a bad sector and if there is anything I can do to check the health of my hard drive and how to fix it.

[SIZE="3"] **(3) Is there a Backup command or tool?**[/SIZE]

Here I'm not thinking about anything corresponding in Windows, but I've heard about cool tools Mac OS X has to make smart backups, something where I don't need to manually copy again the files myself.

[SIZE="3"]**(4) How do you thank people in the Ubuntu forums? **[/SIZE]

Uhm... This is an embarassing question, but I haven't understood how I can thank somebody for his/her post. I thank people inside my posts, but this doesn't count as an official "thanks".

If you have a suggestion or an answer to any of these questions, please let me know. Even if it's just reassuring me of why I don't need some of them anymore (for some reason).

Thanks for reading this.

Cheers :)

---

### Post by hyper_ch on 2008-11-19
> **futuroimperfetto said:**
> (1) Is there a System Restore?
No...

> **futuroimperfetto said:**
> (2) Is there a hard drive Defragmentation command?
Not needed

> **futuroimperfetto said:**
> (3) Is there a Backup command or tool?
There are many... I personally use rsync and hardlinks and a small shell script to create 6hourly incremental snapshot-style backups.

> **futuroimperfetto said:**
> (4) How do you thank people in the Ubuntu forums?
In the "forums" section on the bottom of the front-page listing there are a couple of threads. Have a read there.
Cheers :)[/QUOTE]

---

### Post by PartisanEntity on 2008-11-19
> **futuroimperfetto said:**
> Hi,

 There are a few things that I use to do when I was using Windows XP which I don't do anymore. I would like to ask if there are equivalents to the following features Win XP had:

[SIZE="3"]**(1) Is there a System Restore?**[/SIZE]

When something went bad in XP, I used to go back to a previous system restore point and most of the issues would be solved. Now in Ubuntu I trust that when I do "remove" I do it for good, so no dirt is left behind, but still... Is there anything equivalent to take a snapshot of the settings at a given time?

No I do not think this exists yet.

> **futuroimperfetto said:**
> [SIZE="3"]**(2) Is there a hard drive Defragmentation command?**[/SIZE]

I've read here and there that the Linux file system is different that the Windows one and that I would not really need to defragmentate my hard drive.

However, two days ago I had a problem with a corrupted folder and had to erase it. I'm wondering if it left a bad sector and if there is anything I can do to check the health of my hard drive and how to fix it.

The Linux file system hardly fragments and so you do not need to defragment.

> **futuroimperfetto said:**
> [SIZE="3"] **(3) Is there a Backup command or tool?**[/SIZE]

Here I'm not thinking about anything corresponding in Windows, but I've heard about cool tools Mac OS X has to make smart backups, something where I don't need to manually copy again the files myself.

I think there are quite a few solutions. I personally like rsync, it is a command line tool, its use is explained [here]("http://www.psychocats.net/ubuntu/backup").

> **futuroimperfetto said:**
> [SIZE="3"]**(4) How do you thank people in the Ubuntu forums? **[/SIZE]

Uhm... This is an embarassing question, but I haven't understood how I can thank somebody for his/her post. I thank people inside my posts, but this doesn't count as an official "thanks".

If you have a suggestion or an answer to any of these questions, please let me know. Even if it's just reassuring me of why I don't need some of them anymore (for some reason).

Thanks for reading this.

Cheers :)

At the bottom of each persons post, on the right side are some icons, one of those is for thanking: [IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG]

---

### Post by lakersforce on 2008-11-19
As to question 2: Ubuntu automatically checks your harddisk about every 30 mounts or 180 days, whatever comes first.

You can also do this yourself, but I don't remember the command for it. Perhaps the next poster can provide it?

---

### Post by SunnyRabbiera on 2008-11-19
> Is there a System Restore?

In a way yes, and in a way no, ubuntu does not use "restore points" like windows but its possible to enter recovery mode that can allow backups in times of emergency.
Back up your system regularly in any case.

> Is there a hard drive Defragmentation command?
It is not needed, however if the filesystem detects a bad file it will tell you.
Dont worry about fragmentation as ext3 is superior to fat and NTFS.

> Is there a Backup command or tool?
yes there are a few

> How do you thank people in the Ubuntu forums?
The last little icon at the bottom of each post on the right hand side, it kind of stands out as its different then the others,

---

### Post by Peter09 on 2008-11-19
For a backup utility have a look at SBackup its in the repositories. There are few others as well.

---

### Post by bryncoles on 2008-11-19
backups: i prefer grsync to rsync. its the same program, except grsync is a nice, simple click-and-go interface. very user friendly. its a folder synchronisation tool, in case no-one has told you yet!

as for defrags, apparently this happens as part of the checking process every 20-30 boots. 

also, apparently ext3 doesnt fragment until its about 90% disk in use (and i seem to recall windows tellig me it needed at least 10% free space to defrag). 

so as far as i know, theres no dedicated defrag tools for linux systems, but apparently (if you really really want to) you can boot the live cd, open a terminal and type

```
sudo e2fsck -fD /dev/your_partition
```where 'your_partition is the hard disk you wish to defrag, it'll optimise your files, which is effectively defragging it. 

i think this is what is happening with that command: 

> 'sudo' 		gets admin privillages.
'e2fsck' 	is the linux disk checker.
'-' 		appends commands to the disk checker
'f'		forces the operation, so it happens regardless.
'D'		optimises the drive - essentially defragging it.

but ive never tried it, so use with caution!

and as for system restore, i think the usual is to put /home (thats where all your personal files default to) on a separate partition. that way, if something goes horribly wrong (god forbid) you can just reinstall Ubuntu without losing data. 

if you want to move home to a separate partition, google around, or start a new thread and someone will rush to help! ;)

---

### Post by hyper_ch on 2008-11-19
> **bryncoles said:**
> backups: i prefer grsync to rsync. its the same program, except grsync is a nice, simple click-and-go interface. very user friendly.
I prefer rsync because it's nice, simple and very user friendly. Furthermore it allows me to easily setup it up on cron so that I don't even have to manually run it anymore ;)

---

### Post by bryncoles on 2008-11-19
> **hyper_ch said:**
> I prefer rsync because it's nice, simple and very user friendly. Furthermore it allows me to easily setup it up on cron so that I don't even have to manually run it anymore ;)

good call! ive not quite got to grips with automating things through cron and scripts yet - why make life easy eh? ;)

---

### Post by habtool on 2008-11-19
[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

in a terminal/konsole

cd /
sudo touch /forcefsck

on the next boot (one time only), all the HDD will be fsck'd. 

(FSCK can only check unmounted drives.)

Hope this helps

---

### Post by futuroimperfetto on 2008-12-26
Thanks everyone.

I've had a really busy month and after I posted this question I haven't had the time to tinker with anything. I did read the answers though! I haven't checked any backup tool yet, but I'm glad to know that no defrag is needed as well as finally noticing the small medal to thank people (I'm usually never logged in when I read the forum so I actually never saw it before!).

Again, thanks and happy holidays to everyone!

Cheers

---

### Post by habtool on 2008-12-26
For what it is worth, if you want a GUI for rsync, you can use grsync (sudo apt-get install grsync). This is nice if you only backing up a few folders/directories.

Also once you have some experience you can use partimage to back up your entire ubuntu (or windows) partition. This will work similar to Nortons Ghost/Driveimage. You can however not use partimage to back up a mounted partition, so you would need to use a live-cd, or when you dual booting two linux installs.

A nifty utility that backs up using tar and partimage is:quickstart
[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)
(remember you cant use partimage to backup a mounted/running install)

One nice feature of Sun's ZFS, which is not licensed with compatibility with the GPL, on purpose by buggers at Sun, allows snapshotting of a running system.
This is one thing Linux is lacking, but Oracles Chris Mason is developing BTRFS.
This will hopefully go into trial distos by late 2009.
This will allow for snapshotting amongst other nice features.
[http://btrfs.wiki.kernel.org/index.php/Main_Page](http://btrfs.wiki.kernel.org/index.php/Main_Page)
From my reading it will only start going mainstream in 2010, as its still undergoing extensive development and will need fine tuning and testing in the time ahead.

Anyway have a good Festive holiday season and enjoy FLOSS and LINUX ;)

---

### Post by hovzio on 2008-12-26
Hi, as for backups I can only recommend unison-gtk. It can use ssh, ftp protocols and has a nice gui. You can also backup local files. Unison is cool because (if you want) you can backup changes that take place in both directories and update both according to the last time the file was accessed. (good for my two laptops) I guess thats a difference to rsync, its not (if you choose) just a one way backup. What I like about rsync is that its pretty simple to automate backups with little scripts. In unison you can set different profiles, but I dont know how to automate the whole process.

---

### Post by ja660k on 2008-12-26
a question with rsync; i was reading the man page, and i dont know if i read it properly, can i remotly backup something on my pc.. 
ie i want a backup of my website (which is hosted somewhere...) can i back it up onto my pc using rsync..?

i know i can use ftp... or scp 

and vise versa..? backup my pc to my webspace

---

### Post by hyper_ch on 2008-12-26
> **ja660k said:**
> 
ie i want a backup of my website (which is hosted somewhere...) can i back it up onto my pc using rsync..?

i know i can use ftp... or scp 

and vise versa..? backup my pc to my webspace

Yes, if you can login by ssh you can sync:

remote --> local
and
local --> remote

basic syntax is
```

rsync -SOMEOPTIONS FROM TO

```
if FROM is a remote location and TO is a local one, then you backup from remote to local...
if FROM is local and TO is remote, then you backup from local to remote

---

### Post by hcorey on 2009-01-07
Take a look at Back in Time
[http://www.le-web.org/tag/back-in-time/](http://www.le-web.org/tag/back-in-time/)

---

