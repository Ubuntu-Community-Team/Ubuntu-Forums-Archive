---
title: "Backing up OS, programs, and system settings"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by Curbie on 2013-02-24
I would prefer not to ever have to do a another complete reload of my OS, programs, and system settings, is there a way to back them up or will I need to do a bit image of my system disk on to another drive?

---

### Post by arpanaut on 2013-02-24
An Overview: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)
[https://help.ubuntu.com/community/Ca...BackupRecovery]("https://help.ubuntu.com/community/CategoryBackupRecovery")

Good Luck!

---

### Post by sudodus on 2013-02-24
You can do both.

1. A complete image with ***Clonezilla*** when your system is ready, so that you can easily get it back to exactly the same (on the same or a new drive).

2. Incremental or synchronizing backup with ***rsync*** of important files (for example the home directory or a data partition. Many people prefer a home-made script to run rsync, and many people prefer one of the many GUI front ends that use rsync under the hood.

Browse the internet for details, tips and tutorials about tools and methods to backup your data.
--
'Tough guys don't back up their data. They do the all the work twice instead' ;-)

---

### Post by thermion on 2013-02-24
> **sudodus said:**
> 
1. A complete image with ***Clonezilla*** when your system is ready, so that you can easily get it back to exactly the same (on the same or a new drive).


This!

Or you can do something very similar with *partimage* included in the [SystemRescueCD]("http://www.sysresccd.org/SystemRescueCd_Homepage").
As the name suggests, partimage will only backup partitions to imagefiles.

---

### Post by Curbie on 2013-02-24
I evaluated a few data backup programs and so far I like Déjà Dup Backup which seems to handle daily data backups with little overhead, but when talking about &#65279;backing up OS, programs, and system settings, do programs like &#65279;Clonezilla and &#65279;partimage work at a partition level and not the whole drive?

---

### Post by sudodus on 2013-02-24
> **Curbie said:**
> I evaluated a few data backup programs and so far I like Déjà Dup Backup which seems to handle daily data backups with little overhead, but when talking about &#65279;backing up OS, programs, and system settings, do programs like &#65279;Clonezilla and &#65279;partimage work at a partition level and not the whole drive?
Clonezilla can do both (you select what you want). It backs up partitions and also the head of the drive (boot sector and partition table). It can be run via menus or via script files (that are automatically created). And when restoring, it compiles it back to an exact copy of all that contains data (but free space on the drive is skipped).

Partimage is old and cannot image ext4 partitions. Clonezilla uses Partclone, which can, and it is faster too. (I used to run PING 'Partimage Is Not Ghost' until I started with ext4 partitions.)

---

### Post by Curbie on 2013-02-24
sodudus,

When &#65279;Clonezilla makes a partition image, if the partition uses the entire drive, say 500gb, but there is only say 50gb of data on it, does Clonezilla skip the “unused space” when building the backup (a 50gb backup file), or just when restoring the 500gb image?

---

### Post by pfeiffep on 2013-02-24
> **Curbie said:**
> sodudus,

When &#65279;Clonezilla makes a partition image, if the partition uses the entire drive, say 500gb, but there is only say 50gb of data on it, does Clonezilla skip the “unused space” when building the backup (a 50gb backup file), or just when restoring the 500gb image?

I use remastersys to make a live cd of my OS and settings

---

### Post by howefield on 2013-02-24
> **Curbie said:**
> When &#65279;Clonezilla makes a partition image, if the partition uses the entire drive, say 500gb, but there is only say 50gb of data on it, does Clonezilla skip the &#8220;unused space&#8221;..

Clonezilla will create an image from the used blocks on the drive/partition.

Eg, the Clonezilla disk image from this 120 gig SSD that I have Precise and Quantal on is only 3.4gig large.

---

### Post by sudodus on 2013-02-24
> **Curbie said:**
> sodudus,

When &#65279;Clonezilla makes a partition image, if the partition uses the entire drive, say 500gb, but there is only say 50gb of data on it, does Clonezilla skip the “unused space” when building the backup (a 50gb backup file), or just when restoring the 500gb image?
Both

---

### Post by Mark Phelps on 2013-02-24
I believe that PartImage doesn't work on Ext4 filesystems.  I used to use PING (Partimage Is Not Ghost) all the time, and then Ubuntu switched to Ext4 filesystem as the default.

The PartImage folks said they were not updating it to work with Ext4 filesystems and indicated they had no future plans to do so.

---

### Post by TheFu on 2013-02-24
> **Curbie said:**
> I would prefer not to ever have to do a another complete reload of my OS, programs, and system settings, is there a way to back them up or will I need to do a bit image of my system disk on to another drive?

There is a place for a drive image, but it is often not as efficient as the old "backup and recovery" methods.  Images work best when you are afraid of license issues ... like with that *other OS*.

With Linux, you really just need the files that contain 
* all your settings, 
* your data, 
* any customized config files and 
* a list of the programs installed.  
Then when it is time to restore, the steps are:
* installing a base-OS, 
* restoring all the files, 
* restoring the data , 
* restoring customized config files and 
* telling the OS to reinstall all the programs from that list that you created.
This will get you back fairly quickly AND save backing up the 2-4G of OS and application program files. This works best on a system that is well patched.

A key part of Linux files are the permissions (owner, group, ACLs, etc). Sometimes backup tools do not address this in a very good manner. If your target storage for the backup is not a Linux file system, this extra data may be lost.  For example, NTFS does not hold the same permissions as every Linux system, so that information would be lost 80% of the time.

**rsync** is a fantastic tool for mirroring, but a mirror is not a true backup.  It lacks **versioning**, which will address corrupt files or other issues.  rsync can be made to perform fairly efficient versioned backups utilizing hard-links. There are a few scripts available to make this easier, **rbackup **is one.  Again NTFS does not support hard-links, so ... 

My Mom uses** Back-in-Time** to backup her important files. It was designed to be like OSX "time machine" and does a good job. It uses hardlinks, so that might not be a viable option.  Ok, Mom doesn't really know anything about this, but she does like that there are at least 50 different backups that she can restore easily if something bad happens - like she deleted a file accidentally. Makeing B-i-T work for the entire OS is a little more complicated. It really is meant for individual users to backup their HOME dirs.

**DejaDup** is a GUI over **duplicity**.  Duplicity is the CLI tool for **best practice backups** of Linux systems. There are at least 5 other GUIs that can be used over duplicity and if you are knew to Linux, it is probably best to use a GUI. Duplicity supports versioned backup, encrypted backup, and all the other "best practices" - offsite, incremental, etc... 

I've been using **rdiff-backup** for about 4 yrs, without a GUI. It almost always works, the target storage containing the backup does not need to be a Linux File system. Permissions are stored in metadata files. Rdiff-backup has a similar options as rsync, but has built-in support for most of the backup best practices. It only lacks the encryption to disk part, which can be added outside the tool on the target system, if needed.  I've restored about 10 times from rdiff-backup too. Entire systems or 3 files - it is easy since the last backup looks like a mirror created using **rsync**. Here is a script that I've used: [http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup](http://blog.jdpfu.com/2009/10/24/linux-home-backup-with-rdiff-backup)

If you deployed LVM on your system, you might be able to use **LVM-snapshots** for your backups methods. That is an advanced topic, but perhaps the coolest of all the options offered here. 

When you do decide to back up, there are areas that **should NOT** be captured (/proc) and other areas that **must** be part of the backup (/etc/, /home, /var/spool/.  If you backup your $HOME directory, that will capture almost all the most critical personal data and settings on a system, unless YOU put that stuff elsewhere.  Personal data and settings go into $HOME.  System settings and globally installed program base settings are usually placed under /etc.

I wish this was more clear cut, but every install is a little different, so the most important areas on your system may not be the same as on my system due to the way that different programs place data in different locations.   For example, if you've been playing with Apache and created a website, the data for that is usually placed under /var/www. If you use php for the website, plugins might be stored under /var/lib/php5 or /usr/lib/php5 or both. It can get complicated. Other places might be important too.

If you really want to use an image-based backup solution, know that  you'll need to boot up from some external media (flash drive, CD, DVD,  or even a different partition) to make that work. That is a hassle to  me.  It also means that backups cannot follow the **number one** best  practice - 100% automatic.  Also, be certain that whatever file system  you've got is fully supported by the imaging tool.  EXT4 is the usual  file system, but last time I checked, the imaging tools did not support  that file system in an efficient, smart, way.  **Clonezilla** and **partimage** are both great tools when you want an image-based backup.  You can also use the much simpler tools like** dd** or **ddrescue** for the same purpose - these copy bit-for-bit. There is a time for that, but when it will work has become slightly more complex with HDD changes to 4K sectors and either MBR or GPT formatting. With dd/ddrescue, it is important to know that the source and target drives have the same setup.

Sorry if I wrote too much here and complicated things. There is a trade-off between efficiency, completeness, ease of use with all these tools.

**The Checklist**

 
[LIST=1]
[*]Stable / Works Every Time
[*]Automatic
[*]Different Storage Media
[*]Fast
[*]Efficient
[*]Secure
[*]Versioned
[*]Offsite / Remote
[*]Restore Tested
[/LIST]
Good luck.

---

### Post by Curbie on 2013-02-24
Thanks sudodus and all that replied, I will evaluate Clonezilla, sounds like just the ticket.

---

### Post by Curbie on 2013-02-24
P { margin-bottom: 0.08in; }   [SIZE=4]Thanks to all that replied, I normally end my treads with the solution I chose and even though backups seem to be very personal, and strategies and programs used to implement those strategies seem to be all over the place, at lease I feel like I have a pretty good handle on the options now.[/SIZE]
 

 [SIZE=4]After pondering backup strategies for a while, what has protected my data for 30 years (yeah, I still have data I created 30 years ago) are image backups, so I have two drives on my system, one boot drive and one backup drive for daily backtups.[/SIZE]
 

 [SIZE=4]With the current cost of drives I think a occasional image backup of the boot drive and daily backups of home will keep the current data on two drives and a relatively current  system configuration on two.[/SIZE]

---

### Post by sudodus on 2013-02-24
It sounds like a good way to back up your system :KS

Good luck :-)

---

