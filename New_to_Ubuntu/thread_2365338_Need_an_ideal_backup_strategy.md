---
title: "Need an ideal backup strategy"
date: 2017-07-05
forum: New to Ubuntu
---

### Post by nixietube on 2017-07-05
I've done quite a bit of searching on these forums, and I had originally planned to clone my new Linux laptop to back it up in case I cause problems.  However, many of the posts have indicated that a clone is not a good backup strategy, due to efficiency, lack of revisions, and size.  Given this, I'm at a loss for what people recommend.  I already store most of my files on a NAS device, which has a RAID configuration.  Do I even need to run backup software given my NAS setup?  If so, what backup strategy would you recommend?

---

### Post by Tadaen_Sylvermane on 2017-07-05
I just use a plain rsync script to do incremental backups. I don't bother backing up my whole system, just my data. For issues with problems after updates or whatever I'd advise redoing your laptop with lvm for the partition structure. Snapshots are a wonderful thing.

---

### Post by 1clue on 2017-07-05
RAID is not a backup strategy. It's an uptime strategy. NAS is not a  backup strategy, it's an IT resource management strategy. Your NAS or SAN may  have a backup device and also may have a realistic ability to backup all  the files on the device, but neither of those features guarantees the  other.

Sorry for writing a book. My backup strategy has been learned from many mistakes over the years, some of which were extremely costly to me. My setup requires periodic manual maintenance by design, requires a certain amount of interaction designed to remind me that I need to check what gets backed up every now and then. Mostly my backups can be read by any Linux box with a SATA port. The data is organized in a way that makes it especially easy to search and restore individual files as needed.

A real backup prevents several kinds of data errors:
[LIST=1]
[*]Media error.
[LIST=1]
[*]RAID does this to a certain degree. 
[*]Automatic drive mirroring (rsync or recursive copy) does this. 
[*]Networked backups do this. 
[*]Offline backups using multiple rotated backup media do this. 
[/LIST]
  
[*]Accidental write error. This means the user or app accidentally saved incorrect data.
[LIST=1]
[*]RAID does NOT satisfy this requirement. 
[*]Automatic drive mirroring and networked backups might fix this if the error is discovered and repaired before the mirroring task runs, but not after. 
[*]Offline backups do this. 
[/LIST]
  
[*]Malicious destruction of data (malware, ransomware, manual hacking, disgruntled employee/disgruntled teenager)
[LIST=1]
[*]RAID does NOT satisfy this requirement. 
[*]Automatic drive mirroring and networked backups might fix this if the error is discovered and repaired before the mirroring task runs, but not after. 
[*]Offline backups do this. 
[/LIST]
  
[*]Disasters. (fire, flood, earthquake, tornado, etc. that may even destroy your entire work site.) 
[*]Theft of data.
[LIST=1]
[*]Backups don't fix this at all, but you need to think about it because it's very possible that a backup will help someone steal data. 
[*]There is no backup scenario I know of that cannot be exploited by a data thief. Offline backups can be physically stolen, online backups are already conveniently packaged into a zip of some sort. Permissions are often more lax on the backup directory of a live backup. 
[*]Online third-party backup sites seem especially risky to me with regards to data theft. Even if the company is reputable this sort of site seems like it would be really tasty for a black-hat hacker to hit. 
[/LIST]
   
[/LIST]

 Backups need to have some characteristics:
[LIST=1]
[*]They MUST be restorable.
[LIST=1]
[*]I've been making backups personally and professionally since the mid 80s. I've used tapes (audio cassettes in the 80s, various digital tapes, DAT, ...), floppies, CDROM, DVD, Blu-Ray, network shares, NAS-centric backups, SAN-centric backups, USB flash drives, USB hard drives, eSATA drives, you name it. 
[*]I've backed up entire systems (bootable backups), just critical data, and incremental system backups. 
[*]Many of these media were provided by a single vendor, using software specifically created for backups. 
[*]Of that software, pretty much all of it required the same device and the same software to restore the data. 
[*]In the late 90s I actually had to use a backup and found out that I couldn't restore from it. Once I had reconstructed my hardware and software manually, without the lost data, I checked my other backups and found that none of the systems I had been using created valid restorable data which could then be used as intended. 
[*]Since then I've been focused on using the simplest, easiest-to-use backup scheme I could come up with. 
[*]I'll tell you what I do, but your scenario will probably need to be somewhat different. 
[/LIST]
  
[*]They MUST have recent copies off-site. 
[*]You MUST have recent copies on-site but preferably offline. 
[*]They MUST rotate media so that if one media set is damaged there is still a useful backup from a reasonable date. 
[*]If your backup device fails, you MUST be able to use the backups from another device.
[LIST=1]
[*]If you use a proprietary device, that means you need to have two or more of the exact same device, at least one of which is brand new and has never been out of the box. 
[*]This includes software to run it. 
[*]I'll also say that the devices should all be bought at the same time to prevent version changes from messing things up. 
[/LIST]
  
[*]If your data are encrypted you MUST back up the encryption keys on a separate device. Storing keys with the encrypted data is akin to having 'password' as your password. Not backing up your keys is in no way different than throwing away your backup media. 
[*]I avoid block-level backups and device-level backups. Errors in media are backed up as errors in the new media, and this sort of backup is harder to search and requires knowledge by whatever IT staff is working that day. 
[/LIST]

Convenience features that greatly improve the value of backups:
[LIST=1]
[*]It's really nice to have an easily searchable online backup of the most recent data, searchable by whoever owns any specific piece of data. Of course this needs to have adequate security. 
[/LIST]


Here's what I do:
[LIST=1]
[*]On each host (computer) I collect important data in a backup form into a separate device only used for backups. This is an online backup.
[LIST=1]
[*]Regular files are stored in native form. 
[*]The files are stored in the same directory structure as they are found on the filesystem:
[LIST=1]
[*]Files from /etc go to /var/backups/local/etc for example 
[*]Files from /home go to /var/backups/local/home 
[*]You only have the latest backed up copy of your data, which was all generated on a specific date. 
[/LIST]
  
[*]Database backups are in the format useful to the database engine. 
[*]Any other special files are treated appropriately for the data and the application it uses. 
[*]System executables (e.g. files Ubuntu installs) are not in the backup unless they're modified. The system installer is in effect a backup device, at least if you keep your system updated. 
[*]No giant tarballs of multiple files. 
[*]Generally no compression unless it's inherent to the file type 
[*]The backup is scripted using system shell commands, not any backup-oriented software. 
[*]The backup script is also backed up and becomes documentation of your backup process. 
[*]This process should be somewhat manual. On servers I trigger it manually.
[LIST=1]
[*]This forces the backup process to be in my face to some extent, rather than configured once and forgotten about for years. 
[*]Fire-and-forget backup schemes get stale, you wind up backing up data you no longer use and not backing up the new stuff that really matters. 
[*]If you have to trigger the backup (assuming an IT professional who cares about what's on a server) you will occasionally look at your script and presumably modify it. 
[*]Users of desktop systems do not apply here. 
[/LIST]
   
[/LIST]
  
[*]On a networked system designated as a backup device:
[LIST=1]
[*]Create a backup tree. For brevity I'll shortcut the directories: 
[*]Create /backups/<hostname>/<yyyy-mm-dd>
[LIST=1]
[*]You may find it more useful to create the datestamp as a parent of hostname. 
[*]I date the backups here so I have a more reliable idea when the backup was made, but when the new backup is finished the old one is deleted. 
[/LIST]
  
[*]Copy, with permissions, the /var/backups/local/* files into the above tree for each host. 
[*]This is an automated, scripted backup which does NOT use rsync. Each time you copy it pulls all files from the origin to an empty directory. 
[*]For me, this is NOT a compressed or tarred backup. Compression and tarring increase the risk of data loss. A corrupted tarball of some directory (/var/lib/mysql) loses all the data in that directory, instead of a possibly fixable single database or even single table. Same with /etc or /home or whatever else. 
[*]If anything is encrypted it is done on an individual file level as needed. 
[/LIST]
  
[*]On the above system, there is an ejectable SATA drive. In my case it's a slot-loaded SATA, not an eSATA but eSATA is fine. USB3 would also be fine for a non-commercial setup.
[LIST=1]
[*]I have at least 4 active backup media sets at a time. These can be the biggest SATA drives you can get, they are only online during backups or restores so they don't need to be fancy. Fancy costs more.
[LIST=1]
[*]One media set is a 'long-term' set. For example, end-of-month or end-of-quarter backups. These backups are not deleted to make room for another. 
[*]Short-term media is reused. I use a weekly backup schedule, I have one active device for week 1, another for week 2 etc.
[*]I say "media set" because there may be more than one backup media for any given date. 
[/LIST]
  
[*]Data on the drive is formatted ext4 or xfs, depending on your backup and power supply scenario. If you don't have dual power supplies and redundant battery backups (or better) on this box then don't use xfs.
[LIST=1]
[*]You may need to adjust your partition type based on presence of windows backups or whatever. 
[/LIST]
  
[*]Directory structure on each device for my setup is /yyyy-mm-dd/hostname. Yes this is backwards from the structure on part 2. I find it more convenient for each end use case. 
[*]My backup script:
[LIST=1]
[*]Checks the size of /backups in step 2's filesystem. 
[*]If there is insufficient space:
[LIST=1]
[*]AND the media IS NOT an end-of-month media, delete the oldest backups until there is enough room. 
[*]AND the media IS end-of-month media, then:
[LIST=1]
[*]Pull the drive set and start a fresh one. 
[*]Duplicate the full media set. 
[*]Move the duplicate to an off-site vault. (Vault means a place to store media safely, which in general is NOT a conventional safe) 
[*]Move the original to an on-site media vault or a different off-site vault. 
[/LIST]
   
[/LIST]
  
[*]Copy the files from /backups onto the new media set 
[*]Transfer the fresh backup to an off-site vault (rotate vaults each time if you have more than one. I have a separate vault site for each backup set, or 4 sites which are not my office) 
[/LIST]
  
[*]If I ever get the slightest error on a backup drive I retire it and start a fresh one. 
[/LIST]
   
[/LIST]

---

### Post by ra7411 on 2017-07-05
I'm no expert, and you've heard from at least one person who probably is - I'll just tell you what works for me on a desktop.

1) I back up my user files with Grsync, nightly, into an HD separate from my o/s HD. Once a month I do this same backup to a USB HD which is kept unconnected to any machine to protect it from the effects of a lightening strike.

2) At install, I created a separate partition for /home (which has lots of gigs in it) so that I can backup/restore my o/s quickly when something goes wrong. Restoring the o/s with all its installs and settings makes what would be a PITA problem, minor.

3) I backup my o/s partition with both clonezilla and qt5-fsarchiver, into an HD separate from my o/s. I've done restores using clonezilla that went fine. I haven't had a need to do a restore from qt5-fsarchiver since I installed it a couple months ago. qt5-fsarchiver has the advantage that it can be used to backup the o/s, while the o/s is running, instead of having to shutdown and boot from a dvd or usb.

4) Critical files I additionally backup on cloud storage - backups that way are slow due to my ISP's low upload rate.

5) A couple times I've run into bootup failures - I was able to fix things with a boot repair disk. If that hadn't worked, I would have gone to my sda (the whole drive, not just the o/s partition) clonezilla backup which contains the bootup stuff. On my system, that sda backup/restore has lots of gigs and takes lots of time, so I do it infrequently. If I had to go that route, I would do an sda restore, confirm I can bootup, then I'd restore the most recent sda1 backup I have to get as current I as can.

---

### Post by nixietube on 2017-07-05
You have given me quite a bit to think about, and I very much appreciate people taking the time to respond.  Since I'm fairly new to running a Linux-only computer as my main machine, this will take me some time to implement and to make sure I've done everything correctly.  That said, I will certainly enjoy setting everything up along the way.

---

### Post by Habitual on 2017-07-06
[Simple, Secure Backups for Linux with rsync]("http://rsync.net/resources/howto/rsync.html")
[Full System Backup using rsync]("https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync")
[Incremental Backups on Linux]("http://www.admin-magazine.com/Articles/Using-rsync-for-Backups")
[rsync - Community Help Wiki]("https://www.google.com/url?q=https://help.ubuntu.com/community/rsync&sa=U&ved=0ahUKEwjzq_Lc6_TUAhUm5YMKHXi9DgIQFggFMAA&client=internal-uds-cse&usg=AFQjCNGdSCXNXKGBw2J5iGKhpSt6RUsAkg")

1clue's post nailed it. Quality Response that one.

Tip: rsync is every where. :)

---

### Post by 1clue on 2017-07-06
Thanks for the kudos, but I don't consider myself an expert. I'm a guy who did the wrong thing enough times to develop something that works for me.

Rsync is not a backup strategy either. It's a smart file duplication  tool designed to maintain a remote mirror. It can be used in a backup strategy. I don't use it in mine because in my case it would always do a full recursive copy of every file, and there are more efficient ways to do that.

The good thing about rsync is that it allows copying between two machines and only sends the stuff that changes.

The bad thing about rsync is that you get a copy of whatever it was you copied. If you do frequent backups with rsync, then half of the reason you have backups (accidental file edits or corruption) is out the window. This is true for all backup types, but people seem to run rsync "backups" more frequently due to (theoretically) less bandwidth used.

I'm not saying rsync is a bad tool, I'm saying that if you use it then take into account the human factors in your backup. In order to protect against accidental edits or file corruption, you need a backup from before the corruption happened, and time to retrieve it. If you're working late doing end-of-quarter books, you're going to go to sleep and then wake up in a day or two. If your backup already fired off then any accidental accounting error in your books has propagated to your live backup and your only way out is to dig through offline backup media, if you have it.

Choosing the appropriate point in time to make a backup, and choosing the appropriate frequency of backups are two of the biggest problems in doing good backups.

---

### Post by SeijiSensei on 2017-07-06
I posted the script I use here today at: [https://ubuntuforums.org/showthread.php?t=2365360&p=13662950#post13662950](https://ubuntuforums.org/showthread.php?t=2365360&p=13662950#post13662950)

I don't do incremental backups with rsync.  I make images of every directory and file in my include lists each day and store them in rotated subdirectories.  I back up local directories like etc, var, and home, and remote server directories containing web sites, mail, and the like.  Linode takes snapshots of my virtual servers every night in case disaster strikes.  I'm so glad I no longer have to deal with the problems posed by real hardware.

---

### Post by nixietube on 2017-07-06
Thanks, these are all great suggestions.  SeijiSensei, I like your backup script, but it is going to take me a little bit to become familiar enough with Linux to be able to understand everything you've written in the script.  I'm off to Linux Journey now to better understand some of the inner workings of Linux.

---

### Post by jacko777 on 2017-07-07
From what I saw on the web site, rsynch is shockingly expensive..  is there something I can get for a complete disk image a little (a lot) cheaper.?

---

### Post by SeijiSensei on 2017-07-07
I don't know what you saw, but the program **rsync** (no "h") is an open-source utility licensed under the GPL.  It comes with, or can be installed on, any Linux system for free.

If you want to clone your installation, there's clonezilla: [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by 1clue on 2017-07-07
> **SeijiSensei said:**
> I don't know what you saw, but the program **rsync** (no "h") is an open-source utility licensed under the GPL.  It comes with, or can be installed on, any Linux system for free.

If you want to clone your installation, there's clonezilla: [http://clonezilla.org/](http://clonezilla.org/)

Or Windows or Mac, I believe. Although file permissions seem a bit odd when syncing across platforms.

---

### Post by SeijiSensei on 2017-07-07
> **1clue said:**
> Or Windows or Mac, I believe. Although file permissions seem a bit odd when syncing across platforms.

I don't think you really can sync across incompatible filesystems without losing information.  NTFS wouldn't know what to do with Unix permissions or ext4 file systems and NTFS access control lists.  And, yes, I'm sure rsync is free on all platforms.  Andrew Tridgell believes firmly in the GPL.

The only sure way to write a Linux backup to an NTFS filesystem is to create a tarball of the backup and write that to NTFS.

---

### Post by 1clue on 2017-07-07
> **SeijiSensei said:**
> I don't think you really can sync across incompatible filesystems without losing information.  NTFS wouldn't know what to do with Unix permissions.  And, yes, I'm sure rsync is free on all platforms.  Andrew Tridgell believes firmly in the GPL.

Don't know much about rsync, I almost never used it. But in almost any commercial NAS you can get mac/unix/windows file shares in native format (appleshare, nfs, cifs) and at least some of them you set permissions on a file or folder, and the permissions carry across to the other operating systems and share types. So whatever filesystem they actually store data on must be able to port to other platforms.

---

### Post by Tadaen_Sylvermane on 2017-07-08
> **1clue said:**
> Thanks for the kudos, but I don't consider myself an expert. I'm a guy who did the wrong thing enough times to develop something that works for me.

Rsync is not a backup strategy either. It's a smart file duplication  tool designed to maintain a remote mirror. It can be used in a backup strategy. I don't use it in mine because in my case it would always do a full recursive copy of every file, and there are more efficient ways to do that.

The good thing about rsync is that it allows copying between two machines and only sends the stuff that changes.

The bad thing about rsync is that you get a copy of whatever it was you copied. If you do frequent backups with rsync, then half of the reason you have backups (accidental file edits or corruption) is out the window. This is true for all backup types, but people seem to run rsync "backups" more frequently due to (theoretically) less bandwidth used.

I'm not saying rsync is a bad tool, I'm saying that if you use it then take into account the human factors in your backup. In order to protect against accidental edits or file corruption, you need a backup from before the corruption happened, and time to retrieve it. If you're working late doing end-of-quarter books, you're going to go to sleep and then wake up in a day or two. If your backup already fired off then any accidental accounting error in your books has propagated to your live backup and your only way out is to dig through offline backup media, if you have it.

Choosing the appropriate point in time to make a backup, and choosing the appropriate frequency of backups are two of the biggest problems in doing good backups.

Used properly rsync is quite effective for backups. but if you only keep your incrementals for a day or 2 then yes its about worthless. I have most of mine going back 30 days. Some 6 months.  doesn't take much more space than the folder being backed up. key is --link-dest. Then each backup is complete but you only backup changes. I don't think people who say rsync is bad for backups understand how to use it quite honestly. If the above problem happened it isn't rsyncs fault. Its your own fault for failing to use it properly in which case any backup program can be worthless, not just rsync.

---

### Post by HermanAB on 2017-07-08
I only back up my data and occasionally I make a backup tar ball of /etc to capture the configuration of things.

There is no point in backing up all of Linux and the applications.  There are enough copies of it around the world already.

---

### Post by 1clue on 2017-07-08
> **Tadaen_Sylvermane said:**
> Used properly rsync is quite effective for backups. but if you only keep your incrementals for a day or 2 then yes its about worthless. I have most of mine going back 30 days. Some 6 months.  doesn't take much more space than the folder being backed up. key is --link-dest. Then each backup is complete but you only backup changes. I don't think people who say rsync is bad for backups understand how to use it quite honestly. If the above problem happened it isn't rsyncs fault. Its your own fault for failing to use it properly in which case any backup program can be worthless, not just rsync.


[LIST=1]
[*]I don't use incremental backups. Ever.
[*]If your backup runs every night, for example, how do you find out what file /home/you/foo.txt looked like two weeks ago?
[/LIST]

The reason why rsync is not a backup strategy is because it's a simple tool.  As I said above it can be used in a backup strategy but is not one. If it were a backup strategy you should be able to just fire off 'rsync' and it would take care of everything in your corporate office.

The reason I don't use it is because I don't do any incremental backups. Incremental backups save space and time when you're creating the backup, but that time and that space are irrelevant when you actually NEED the backup. A backup is needed when:
[LIST=1]
[*]You had a hardware failure and you need to rebuild data.
[*]You had a software failure and you need to rebuild data.
[*]Somebody accidentally trashed your customer database (for example) and you need to rebuild data.
[*]Somebody got ransomware or other malware and you need a trusted copy of your data.
[*]...
[/LIST]

In every one of these scenarios the fact of an incremental backup is a hindrance. In most of these scenarios it's possible that the backup fired off after the data corruption took place, which means your rsync backup is worthless.

A real backup is a frozen image of what your information looked like at a certain point in time. You should have multiple images so you can get some reasonable idea what it looked like at any time N backups ago. Rsync assists in absolutely no way with that scenario.

Rsync can help you maintain a mirror of some authoritative data, which means it could act as the copy tool in first or second stage of a backup strategy. In that way it would save time, if your first or second stage acts on an already populated destination.

---

### Post by TheFu on 2017-07-09
On Linux, if someone suggests you need to use commercial software, chances are they are getting a kickback or work for that company.  I have deployed commercial software on Linux for work, but never at home.  It isn't generally the situation that commercial software on Unix is any better than the F/LOSS stuff.  I'd guess about 90% of all commercial SW for Linux is 90% F/LOSS with 10% GUIs on top to make managers happy.  Any Unix admin wouldn't be taken in by this sort of offer, but many people coming from other OSes seem to be.

Lots of great info above.  I don't agree with all of it, but that's fine. We each need to find our ways in this world and what works for 1 person probably won't work for another because of their experiences and failures.

I've failed a bunch over the years.

The good news is that for about the last 10 years, my backup methods have made sleeping at night very easy.  I know that any disk failure is a minor inconvenience, not a terrible loss of data event.

I used rsync to do backups in the early 2000s. Then I was burned.  The source disk became corrupted and the lack of versioning meant that the next rsync overwrote all the good, non-corrupted, file versions.  From that point on, I always did versioned backups.

If you don't use tape/sequential storage, then doing "incremental" backups makes less and less sense every year.  Around 7 yrs ago, I switched to "reverse-incremental" backups.  The most recent backup looks like an rsync mirror, but all prior versions are compressed diffs from the prior backup. This captures changes in files and permissions over time.  When I was doing rsync backups would take 45+ minutes per machine. Switching to the newer method and backups require 2-3 minutes per machine.

Snapshots are NOT a backup method any more than RAID is a backup method.
RAID solves 3 problems.  Versioned backups solve 1001 problems, including all problems that RAID can experience/have/cause.
Snapshots are a technique to ensure a backup is consistent.  It is also a way to quickly rollback any updates, but if retained much longer than 1 day, a snapshot is just wasted space and loses usefulness like ice on a sunny, hot, day outside.

I use rdiff-backup.  
* don't backup the entire OS, 
* just the data, 
* list of installed programs, 
* system and program settings and
* my HOME.
I've restored systems to working with just that information - usually takes about 30 - 45 minutes. I start with a fresh OS install - which takes about 15 minutes. The rest of the time is restoring the latest backup (usually from last night) for the settings and my data, followed by taking a list of programs (included in my daily backups) and having APT install those for me.

Had a HDD failure on my media server 2+ months ago. It was the OS disk that failed. Getting the OS back was easy, but getting data restored took longer ... it was a huge disk that was nearly full.  It was a minor inconvenience, ZERO data loss.

There are some nice rdiff-backup how-to guides on the internet. You can and should use snapshots as part of that strategy if you don't want any services to be unavailable during backups.

---

### Post by Tadaen_Sylvermane on 2017-07-10
Based on your post I use versioned backups with rsync, not incremental. My apologies for confusion. Mixed up words. 

Isn't rdiff-backup just a frontend for rsync?

---

### Post by TheFu on 2017-07-10
> **Tadaen_Sylvermane said:**
>  Isn't rdiff-backup just a frontend for rsync?

NO! rdiff-backup is NOT just a front-end to rsync.  It used librsync, but it works differently.  It isn't a front-end to rdiff either.  Instead of using hardlinks (which have all sorts of limitations) as rsync "versioning" does, it uses file metadata storage and compressed diffs.  That means rdiff-backup captures ownership, group, permissions AND ACLs as they change over time.  rsync does not.

rdiff-backup stores the last backup like an rsync mirror. Older versions are compressed diffs off that over time.  Each older compressed diff "set" is stored under different directories to the size of the mirror.

rdiff-backup's options are similar to those for rsync. Include, exclude, special files are all handled. If you are using rsync, it doesn't take much to test rdiff-backup.  Do a test with something small, but meaningful - /etc/ .   3 minutes and 2 backup runs will teach more than we can possibly say here. I think you'll be a convert.

rsync is missing some important things that solid backups require.

---

### Post by Habitual on 2017-07-10
I run this every time someone says or mentions "backup" :)
```
#!/bin/bash
cd $HOME ; sync
/usr/bin/udisksctl mount -b /dev/sdc1 /media/jj/external  > /dev/null 2>&1
/usr/bin/ionice -c 3 /usr/bin/rsync -avz  . /media/jj/external/LM17/ --delete
/usr/bin/du -sh /home/jj/ /media/jj/external/LM17/
#EOF
```

See also [https://ubuntuforums.org/showthread.php?t=2360351&p=13641422#post13641422](https://ubuntuforums.org/showthread.php?t=2360351&p=13641422#post13641422) for summary of pieces/parts.

---

### Post by TheFu on 2017-07-10
Might be a little issue.

That script creates a mirror of all the corrupted, encrypted, or removes recently deleted files on the external storage media.

Versioning by the backup tool which will see the corruption or encryption and create new versions is important.

---

### Post by Habitual on 2017-07-10
Good points.
It was merely an example, or starting point.
I suppose I could implement a "date +%u" mechanism for 7 day rotation.  :)

I've been meaning to build on it.
interactive and/or with c-line args, woot. Here we go!

---

### Post by 1clue on 2017-07-10
ISO-style timestamp script, I call it 'ts':
```
#!/bin/bash

date +%Y$1%m$1%d-%H$2%M$2%S

```

Usage:
```

**$ **ts - :
2017-07-10-14:09:22

**$ **mkdir /backups/`ts - :`

```

The first argument is the delimiter used in the date part. The second argument is the delimiter for the time part.

---

### Post by TheFu on 2017-07-10
Or just use
```

$ rdiff-backup --exclude **/.cache --exclude-special-files  $HOME /media/jj/external/LM17/
$ rdiff-backup --remove-older-than 7 --force /media/jj/external/LM17/
```

Of course, if you capture crontabs and use dpkg --get-selections, then you'd have the things needed to mostly restore the system and all programs pretty quickly.  Get the output from lshw and lsblk and you'd have hardware, drivers, and disk layout information.  I like to put that information as text files into /root/backup-data/ .

I'm not really a fan of local backups for a few reasons. Too easy for a nasty program to see the storage and encrypt it. Using a backup server to "pull" the backups (over ssh) would remove that risk. And since real backups need to run as root, be certain to setup ssh-keys for remote root access from the specific backup server IP only.  rdiff-backup uses the same userid@server: addressing as rsync and automatically uses ssh, honoring the ~/.ssh/config file just like every other ssh-based tool.


Of course, after you see how little extra storage rdiff-backup needs for each version, you might just go with 30, 60, 90, 120 days of backups. Why not, if you have the storage?

---

### Post by samson-danziger on 2017-07-11
Just thought I would throw in my 2 bits in here. I have a spare 128GB drive mounted on /backups on my laptop. 
Everyday I have a cron job which copies all my home directory, and all installed packages to a folder called /backups/backup.0/. It also copies backup.0 to .1, .1 to .2, etc.
So after a week I have /backups/backup.{0..6}, where 0 indicates today, and 6 is 6 days ago. 

Every week, I also create a snapshot backup which is uploaded to Amazon Glacier. This is just a tarball of /backups/backup.0. I save that as latest.tar.gz, and I move the previous file to previous.tar.gz. 

Fortunately I have ever had to use them, but with this setup I have local copies of my home directory for the past 6 days, and a snapshot of what it was like somewhere between today and 1 week ago, and 1 week and 2 weeks ago. 

Links to my files below.
Daily: [https://pastebin.com/j9ScQcqt](https://pastebin.com/j9ScQcqt)
Weekly: [https://pastebin.com/dTPK8wnB](https://pastebin.com/dTPK8wnB)

---

### Post by paulconnolly on 2017-07-21
Thanks everyone, I'm now testing out rsync for backing up, so far so good!

---

### Post by Michael_McKenney on 2017-07-21
A backup strategy falls into multiple areas.   How many backup sets you have that are distinct?  Backup rotation, how often you backup before you get back to the first set.   Testing your backups!  

In my data center is tape based, I have Monday to Thursday, weeks 1 and 2.  Fridays go F1 to F8 in sets.  First backup each month is retired and stored.  Tapes allow me to take them home or store them offsite.   I do have a Barracuda device that backs up two VMs offsite.   We were considering a offsite backup solution but it would require 300-500 Mbps of bandwidth to accomplish it.   We have 4TB of data that changes too often for even disk deduplication.

At home,  I have three tape drives and a USB backup drive on my workstations and servers.   I use Symantec Backup Exec 2010 on XP Pro x64 and does 3 concurrent backups of the three machines.  It is GUI based.  I tried Bacula on Ubuntu.  It crashed constantly.   It would do only one computer at a time.   I have USB drives that I copy files off to like my web sites as a quick backup of new content.  I have 6 sets of tapes that rotate about every 2-3 weeks.  

I test my backups every weekend.  A backup is only as good as the restore.    Testing is more important than just backing up.   You need to verify your data was copied correctly and not corrupted.  The problem with real time backups is cryptolocker virus can destroy your backup drive and live drives.   Tapes are only done when scheduled.   Yes, they are expensive.   Another problem with USB backups is it is one device.  Most people don't rotate backup drives.   What happens if you only backup also fails or is corrupted.   It is best to have multiple backups that are rotated.

---

### Post by 1clue on 2017-07-22
> **paulconnolly said:**
> Thanks everyone, I'm now testing out rsync for backing up, so far so good!

Remember that a pure rsync backup solves fewer than half of the potential reasons why you would need a backup.

---

### Post by HermanAB on 2017-07-23
Howdy,

My tuppence worth:
Normally, people think of 'what to backup'.  A better strategy is to think of 'what NOT to backup' and make your script such that it will backup everything except files that are larger than some big number (to exclude ISO files, archives and cruft) and a few specific types of filenames, such as *bak, *wav, *mp3 - stuff that you can always get again from somehere.

The advantage of using the 'exclude' parameter is that you then don't need to amend the backup script ever again.  It will always work.  Also consider that since your taste changes as you get older, therefore making a backup of music files and movies for example is not particularly useful either.

---

### Post by col48 on 2017-07-23
My tuppence worth is that the ideal strategy is very personal to the individual.

I have two Ubuntu systems in separate partitions on the same hdd.  Every so often I log in to the secondary (little used) one and copy the complete more heavily used partition to a folder with a unique date-specific name on an external hdd, using rsync.  This takes less than an hour - I don't have much by way of mp4 files and so on.

Advantages:
It's simple - finding a backup file is very like finding its original equivalent.
No specific password to remember
Backups are under my hand
Computer is tied up with backing up when it suits me at the time.

Disadvantages:
My latest backup is as old as the last time I initiated it.
One day the external hdd will be full (probably around 2020 at the present rate) unless I delete old backups, which takes time.
If the external hdd is corrupted during the backup process, I may lose all the backups.

I have only needed to resort to a backup 4 or 5 times - always because of deleting a file prematurely or badly messing up an edit.

Works for me, but not purely ideal for most!

---

