---
title: "How to do system backup"
date: 2021-08-09
forum: New to Ubuntu
---

### Post by tomislav.stasina on 2021-08-09
Hi everyone, Ubuntu newbie here!

I installed Ubuntu 20.04.2 LTS and I'm starting to dig OS. I installed programs I need to do some work, mounted additional SSDs, personalized system a bit etc., and now I feel comfortable using it. 
I would like to have a local backup in case I mess something up while learning all the stuff. 

What are my options for creating system backup and what will backup affect?

Thank you!

---

### Post by tea for one on 2021-08-09
For backup of the Operating System, I use [https://clonezilla.org/](https://clonezilla.org/)

For backup of personal data, have a look at [COLOR="#0000FF"]grsync[/COLOR] (gui for rsync)  - available via the repositories.

I'm sure other users will chime in with their alternative suggestions.

---

### Post by GhX6GZMB on 2021-08-09
I use Timeshift for system backup. Hasn't failed me yet, I do a backup before fiddling with something. Also rescued me after a total fail (my fault) and format/reinstall.
Remember to include the hidden files in /home in your backups (tick-box option).

For /home backup I use Back in Time.

---

### Post by monkeybrain20122 on 2021-08-09
or [fsarchiver]("https://www.fsarchiver.org/quickstart/"), it has many features and can do live backup (i.e when you are using the system providing you don't alter the file system like installing or removing software)
There is a gui  called [qt-fsarchiver]("https://launchpad.net/~dieterbaum/+archive/ubuntu/qt-fsarchiver"),  it is easy to use but has less options then the cli (e.g, it doesn't have the option to exclude directories)

---

### Post by T6&amp;sfpER35% on 2021-08-10
i use luckybackup to just backup my home (to external drive)
and i use timeshift to backup/restore points on my local hard drive

---

### Post by TheFu on 2021-08-10
There are 3 major types of backups
[LIST]
[*]images
[*]mirrored files
[*]versioned files
[/LIST]
There are pros and cons for each. 

If you are just trying to prevent bonehead mistakes from losing a few files, then the mirrored files could be sufficient and relatively simple. That would be 1 copy only.  Use rsync for that. No downtime should be necessary. Restore of 1 file or entire directories is fairly easy. After the first mirror is created, subsequent updates to the mirror are just a few minutes - only the updates are done.

Images use lots of storage and generally require downtime to get a clean backup.  They can be restored (the full image, not parts) onto a replacement HDD that is the same size or larger and uses the same block size (512b or 4Kb), but you are stuck with the same hardware. A full restore is 1 command, which can be good at 3am.  There isn't any "updating" a backup. Each one is 100% new and takes the same long time to create. If you want 5 copies, then you'll need 5x the storage.  With an "image" backup, that is typically created for an entire partition or the entire HDD.

Versioned backups with files are a little more complex, but provide all the capabilities that normal file-based mirrors provide, but are even more efficient with backup times and storage.  Specific areas to be backed up and excluded files can make this very efficient.

I don't backup the entire OS. I see little reason to backup the 4-10G of an OS when a fresh install of the core OS is 10-15 minutes.  I do backup lists of installed packages, system and personal configuration files and all data (personal and system).  The restore steps are basically, do a fresh OS install from a Live-Boot Ubuntu installer, then restore my data, system data, my settings, system settings, and lastly feed the list of manually installed packages into the package manager to be reinstalled.  The order matters.  At re-install time, applications look for prior settings and prior data. When it sees those, it things - "ah, this is a reinstall, use the existing settings and existing data".  In about 30-45 minutes, my system is back and it is MY SYSTEM with my configurations and all my programs just as they were.  
Because my restore starts with a new OS install, I can change computers and storage layouts completely. The new system ends up being like my old one.  Images can't do that.  I've gone from encrypted storage to unencrypted storage. I've gone from a 32-bit OS to a 64-bit OS as part of an upgrade.  Once had a laptop stolen in an airport.  When I got to the client location, picked up a cheap replacement laptop at the local "big box" electronics store, then restored a backup to it over the internet over night. It was "my system" the next morning.

Additionally, versioned backups help fight not only hardware failures and stupid user tricks (I do something dumb about once a week), but these versions mean a corrupted file gets more time to be noticed. Once had to go back 37 days in my versioned backups to restore a corrupted database. Nobody would keep 37 images. They might keep 4 - say one a week.  With malware, versioned backups will make it clear when thousands of files become crypt-locked.  Chances are that the size of the backups will become 2x the current size. I get daily reports about system backups and 2x a size increase for most systems would jump out.  To be more effective against malware, it would be better to have a different backup server that "pulls" the backups. Just ensure that no clients have direct, unauthenticated, access to the backup server.  The backup server would create the connection and pull the files to be backed up.  This is a more advanced method.
[Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979](Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979) has a very small backup example that is good for 1 user's HOME directory. It is a start.  
For a full system backup, something like:
```
$ sudo rdiff-backup
       --exclude-special-files \
       --include /usr/local --include /etc --include /home --include /root \
       --exclude '**'        /         /Backups
$ sudo rdiff-backup   --remove-older-than 90d --force /Backups
```

would handle many needs. Just be certain to put the list of manually installed packages in a text file that gets included in the backups.  The 2nd command is what limits the number of versions to 90 days. rdiff-backup will use perhaps, 1.4x the original storage to provide 90days of daily, versioned, backups.

Remove the sudo, put those commands into root's crontab and you can have daily, automatic, versioned, backups for most systems.

Do a little test with just /etc/ in the includes.  Do the first run, change a few times in /etc/ and run it again. Go look at what happens in the /Backups directory. The last backup looks like a mirror. 

Run 
```
rdiff-backup --list-increments /Backups
```
and 
```
rdiff-backup  --list-increment-sizes   /Backups
```

If you have multiple systems to backup, put each into a different directory. I use /Backups/{hostname}/ to keep them all straight.

Restores can be just a simple copy using any tool you like.  If I need the most recent backup restored, I can use rsync, but I'll typically use **rdiff-backup --restore-as-of  now /Backups /** . Note how the source is now the backup area and the target is where I want stuff placed?

Of course, the commands can be more complex with all sorts of special included files, excluded file and it might be good to generate some updated system information before each daily backup to be included. Here's what I capture.
```
# ls /root/backup
apt-mark.auto    cpan.list   crontab.root  gem.list    mcpan.list    lshw.list  new-manual
apt-mark.manual  crontab.thefu  dpkg.list     installed-pkgs  new-auto   parted.txt
lvs    vgs   pvs   
```
I may not need the information, but it could be very important too. Just depends on what the failure was which is causing a restore.

---

### Post by GhX6GZMB on 2021-08-10
> **monkeybrain20122 said:**
> or [fsarchiver]("https://www.fsarchiver.org/quickstart/"), it has many features and can do live backup (i.e when you are using the system providing you don't alter the file system like installing or removing software)


So if you install or remove software, your backup doesn't work anymore? Seems pretty senseless to me. Timeshift (rsync-based) doesn't have that issue.

---

### Post by TheFu on 2021-08-10
> **ml9104 said:**
> So if you install or remove software, your backup doesn't work anymore? Seems pretty senseless to me. Timeshift (rsync-based) doesn't have that issue.

All backups have a time homogeneity mandate.  For image based backups there are ways around this issue - typically people will boot from alternate media to make the images, but if the underlying volume managers supports snapshots, then those can be used as well to freeze the blocks to be backed up and let the system keep running.

No backup solution is perfect. They all have issues, caveats, and all can be corrupted either the entire backup or a single file, if steps to avoid the corruption are not expressly taken.  Just because rsync seems to never have a problem, doesn't mean that it doesn't ... for example, rsync with hardlinks for versioning only retains the last owner, group, ACLs and xattrs.  If a file was corrupted 37 days ago, but the owner/group were modified just 15 days ago, the restore of the data from 37 days ago will end up with the wrong owner/group.  Lots of backup tools make that mistake.

Some backup tools are tied into volume management snapshots, which can be a good thing ... provided the backup tool or the volume manager doesn't become confused.

---

### Post by GhX6GZMB on 2021-08-10
@TheFu:
The original question was simple and from a "newbie".
You are scaring people away here!
We all appreciate your knowledge on this, but really... you can take things too far. Just a friendly hint.

---

### Post by monkeybrain20122 on 2021-08-10
> **ml9104 said:**
> So if you install or remove software, your backup doesn't work anymore? Seems pretty senseless to me. Timeshift (rsync-based) doesn't have that issue.


 Well yeah you can either manually backup regularly or make a corn job. But the advantage of fsarchiver is that it basically copies the file system along with the meta data but is quite insensitive to the underlying drive configuration and it is a lot more flexible than say, clonzezila, and it is very easy to use and non intrusive so you can continue to read or browse the web when backup is happening in the background (the gui is especially convenient for new users even though it doesn't allow the fine grain control of the cli). restoration is also very simple (might need to reinstall grub though)

I don't know about timeshift but by reading the manual it seems you need to have a dedicate formatted drive for it and I don't see how it can keep track of installing and removing software without gap unless it is constantly working to sync the system. In that case wouldn't that affect performance?

My need for system backup is basically 1) to restore system should a bad update mess up the system so basically you can created snapshots with fsarchiver and restore system to the point before the bad update (which merely making a list of installed apps for reinstalling doesn't help since you'll get the same defective updated version of foo that messes you up in the first place) and 2) making an identical system in another machine say in case of hardware failure. In that clonezilla is picky about disk size  and detailed drive configuration but fsarchiver doesn't care, again the flexibility beats other tools,  I don't know if timeshift works in that scenario.

In fact I used to "upgrade" my system by creating an installation of the new Ubuntu release in an external hard drive, test it and tweaking configurations to optimise performance and run it for a few months to make sure everything I need is working with no nasty surprises, then  I use fsarchiver to make a clone of it and restore it to my internal hard drive. Not sure if timeshift would work for that.

---

### Post by TheFu on 2021-08-10
> **ml9104 said:**
> @TheFu:
The original question was simple and from a "newbie".
You are scaring people away here!
We all appreciate your knowledge on this, but really... you can take things too far. Just a friendly hint.

Newbies aren't dumb people. They can decide for themselves what is good advice.  2 commands are hardly "scary" - or can easily be ignored. We are all different.  Someone who wants to "dig into the OS", will probably appreciate the different options.

Just a friendly hint.

---

### Post by tomislav.stasina on 2021-08-11
Thank you all for all this useful information.

I appreciate both  basic and advanced replies - although I will start with more basic  solutions and go advanced if I feel I need more. 
@TheFu - thanks for  detailed reply, I will probably read it multiple times. Maybe it's not  all clear now, but it's good to have information somewhere in head to  recall later when I get more comfortable with system.

---

### Post by mastablasta on 2021-08-13
since we are talking about local backup and not separate disk image or external (server) backup and option would be to use BTRFS or ZFS4linux. unfortunately that choice should be made at the system install. but i am just commenting here in case someone else reads this. These file systems can make snapshots of current install on local drive which can later be restored. they dont' guard against disk failure, but they do guard slightly better against user tinkering.  

beside the ones already mentioned in this thread (which are all very good options) there are a few more with GUI interface i tried and found useful:

1. incremental & full backup (push method to internal, external drive or server)

[LIST]
[*]Areca
[*]Duplicati
[/LIST]

2. incremental & full backup (pull method to internal, external drive or server)
[LIST]
[*]UrBackup
[/LIST]

3. full disk image backup
[LIST]
[*]Rescuezilla
[*]Clonezilla
[/LIST]

---

### Post by rsteinmetz70112 on 2021-08-13
For a beginner I'd stay with the backup system provided by the distro. Currently for Ubuntu 20.04 I believe it's Deja Dup. There are a gazillion backup solutions for Linux including the many options listed above and many home brew options, which is what I do. I believe it's more important to start the backups early than to search for the perfect system. You can always change it later if you decide you want to. 

Here is an article on how to set it up. [https://www.lifewire.com/backup-ubuntu-4126286](https://www.lifewire.com/backup-ubuntu-4126286)

---

### Post by TheFu on 2021-08-13
Don't forget **Back-In-Time** [https://backintime.readthedocs.io/en/latest/](https://backintime.readthedocs.io/en/latest/) .  Used that tool for Mom's system years ago.  It was much better than Duplicati at the time. Back-In-Time uses rsync+hardlinks, which is what many of the other tools use to support versioned backups.  For about a decade I used **rsnapshot** which was a script published in an O'Reilly UNIX book that also does rsync+hardlinks.  rsnapshot is in the Ubuntu repos. [https://ubuntu.com/server/docs/tools-rsnapshot](https://ubuntu.com/server/docs/tools-rsnapshot)  There are other variations on rsnapshot, like rbackup.

For Ubuntu Desktop users, [https://help.ubuntu.com/stable/ubuntu-help/backup-why.html.en](https://help.ubuntu.com/stable/ubuntu-help/backup-why.html.en)

Tested Duplicati and in 8 hrs, it hadn't backed up 100G.  Duplicati, DejaDup, duplicity are all in the same family. These tools have all the features for great backups, but the implementation, performance has never impressed me. They work in the very old way, like we did backups in 1970.  Duplicati can't still be that slow.

Newer tools like rdiff-backup work in exactly the opposite way.  It is a comparison between SCCS and RCS version control systems (that probably doesn't help anyone but the old programmers).  Duplicity gets a full backup, then creates diffs off it. The restore process has to being with that full backup, then all the diffs since it happened to restore a system.  rdiff-backup maintains the full backup and creates diffs between B-0 and B-1.  80+% of the time, when we need to restore, it is the last backup that is needed, so that is just a cp to restore.  Duplicity needs a new "full" created weekly or monthly to avoid too many differences and possible corruption.  With rdiff-backup we prune away the oldest diffs as each new backup is created, once we have the number of versions we want. If any intermediate version is removed, all the later versions are considered corrupted. The same applies to all efficient, versioned, backups using forward or reverse diffs.

BTW, I've used **fsarchiver** to create backup images for raspberry pi systems. Good tool, for what it does. Just don't expect versioning or great storage efficiency from any imaging tool.

---

### Post by GhX6GZMB on 2021-08-13
@TheFu:
Based on previous posts by you, I now also use Back in Time now for backing up /home.

I use two backup programs: Timeshift for system backup and Back in Time for /home backup.

This has something to do with my way of working, and my environment, I use laptops that are laid out for several users (not simultaneously, of course), where my account is the admin/sudo user, others are guests.

When I do a system backup, it's normally because I'm experimenting with something on the OS that won't touch the /home files. So no reason to back them up (/ and /home are always on separate partitions).
For this I use Timeshift, because it's optimized (at least in the GUI version) for system backup, is sudo protected and very fast after initial backup.

For /home backups I use Back In Time, because it's NOT sudo protected, and every user has resposibility for his/her own workfiles (this includes myself), and because it's originally designed/optimzed for /home backups.

Needless to say, I do this using the GUI versions.

I understand your preference for CLI use, but I try to approach maximum productivity by balancing CLI and GUI according to the task.

---

### Post by TheFu on 2021-08-13
**Back-in-Time** can do full system backups under root's crontab these days. Think there's a GUI toggle switch.  It has some cool ideas, like having hourly backups for the most recent 2 days, then it selectively removes backups as they get older and older. This happens by default.  I never learned how to create a custom schedule for how to keep what I really wanted, but I assume it is possible.
I'd like hourly for 2 days, daily for 2 weeks, then weekly for 4-8 weeks, then monthly for up to 12 months.  Don't know that I'm interested in retaining a yearly backup or 5.  Alas, Back-in-Time has the same flaw that all rsync+hardlink backup solutions have - they don't maintain the ownership, group, and permission changes over time.  It isn't a problem too often - until it is - then we are screwed.

I can see where Timeshift's integration with brtfs would make it an excellent choice for that file system.

---

