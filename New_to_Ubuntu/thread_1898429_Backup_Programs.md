---
title: "Backup Programs"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by lile001 on 2011-12-21
What are people's recommendations on backup programs?

For quite a while I have just been making tarballs on an external hard drive.  Currently, I have started using the following system:

Deja Dup, which is based on Duplicity, set to do daily backups of /home on an internal extra hard drive

Tar, programmed manually every friday, backing up everything on the computer to an external hard drive, which is kept in a metal drawer the rest of the time. Although this is a long, detailed command line, it is the same one every time, so I figured it out once and just copy the one I used last time.  

Occasionally I also make DVDs and take them to the bank deposit box, although not often enough.  

Here are several problems with this system:

1.  Deja Dup is too simple:  hard to use to retireve a single, particular file.  It seems to have a "restore to folder" option, but when I use this, it sets about restoring everything, not just that one folder, so I don't understand what this option is accomplishing. The program is too damn simple, unless you want to back up everything, and restore everything.  Maybe there is something I don't understand about using it? 

2. Duplicity, which is under the hood of Deja Dup, is essentially impossible to use for me.  I was unsuccessful in retrieving anything after messing around with it for about half an hour making typos.  Maybe some geeky types here get a big thrill out of typing 250 obscure characters into a command line, but all I see is a 100% risk of typos doing something dangerous that I don't understand.  I am just not going to use a command line program to get anything practical done, unless it is dead simple.  It's like using a hammer and tongs to eat ice cream.  Can't we just use a spoon?

3. Of course I could do more offsite backups, yada yada.  That isn't the question, but it is certainly a valid concern. 

There are a dozen or so backup programs listed here [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) but which are better? 

Which backup graphical front ends are simple enough to use, yet powerful enough to retrieve a single file or folder without pain and suffering?  What do other people use and recommend?

---

### Post by aeiah on 2011-12-21
i use backintime for snapshotting*. i havent needed to restore a particular file, but since all it does is hard link from previous snapshots (for things that havent changed) you can always just search the backup filesystem to retrieve a file. looks like you can do it within backintime too but i havent had too many needs to retrieve stuff. 

this method doesn't play well with compressing your snapshots since it relies on the previous versions to keep storage space down (storage space of all snapshots is size of one snapshot + size of any changes)




* if i was setting things up again, id just replicate the backup procedure using rsync and the --link-dest flag but its the same thing and backintime does offer a clear gui.

---

### Post by tea for one on 2011-12-21
I would suggest that you consider Grsync, which is available via the software centre.

---

### Post by lile001 on 2011-12-21
That brings up another question: WHAT to back up? 

1. Everything - cumbersome, but safe.  I have been using this weekly.  Is that a good idea?

2. /Home - misses a lot of user settings and stuff that I don't know much about.  What, for example, is in /etc?  I don't really understand that.  

If you are not backing up everything, what folders besides /home should one be backing up?  or is Everything a better idea?

---

### Post by Ms. Daisy on 2011-12-21
What do you mean by "everything"- do you mean settings & the OS?  I'm a fairly new user, and it took me some time to wrap my head around Ubuntu backups. But generally what people do and what seems to be recommended is that you just back up data only (if you keep your data entirely within /home then that would be it).  If you need to restore Ubuntu, then you simply reinstall the OS and replace /home from the backup.  General recommendations seem to be that one should back up the data on an external hard drive instead of flash drives or CDs/DVDs.

If you have really customized Ubuntu and you don't like the idea of a clean reinstall, then you can create an .iso of your system.  I've never tried this, but I've seen at least one thread with instructions and links to tutorials if you're interested in this route.

---

### Post by lile001 on 2011-12-21
I jsut learned about Datastorageunit.com, $50 a year buys you 100 GB of offsite storage.  Apparently it works with GRsync.  This would be better than the DVDs in the bank vault, might be a good idea.  I'd use this in addition to the local spare hard drive so there is a quick local backup and then a secure remote backup for when the Feces hits the Air Handling Unit.  Any opinions?

---

### Post by lile001 on 2011-12-21
> **Ms. Daisy said:**
> What do you mean by "everything"- do you mean settings & the OS?  I'm a fairly new user, and it took me some time to wrap my head around Ubuntu backups. But generally what people do and what seems to be recommended is that you just back up data only (if you keep your data entirely within /home then that would be it).  If you need to restore Ubuntu, then you simply reinstall the OS and replace /home from the backup.  General recommendations seem to be that one should back up the data on an external hard drive instead of flash drives or CDs/DVDs.

If you have really customized Ubuntu and you don't like the idea of a clean reinstall, then you can create an .iso of your system.  I've never tried this, but I've seen at least one thread with instructions and links to tutorials if you're interested in this route.


Here is what I mean by "everything" in precise terms:

```

Plug in external hard drive you keep in a drawer. Open a terminal.  Tremble in fear, for here there be dragons. 

Go to the Media directory by typing cd /media.

Type ls -l
Cut and paste the name of the external drive (it changes every damn time) into the following command:
cd [external drive name].  Use right click to paste, control-C doesn't work in Terminal

Type ls -l.  You should see your previous backup files 

Use the following command.  Change [todaysdate] to a format like 2011-12-20:

sudo tar cvpzf [todaysdate]backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude homebackup1.tgz --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/home/larry/.Trash --exclude=/home/qhyrrae/.Trash --exclude=/home/.Trash-root --exclude=/home/.Trash-0 --exclude=/root/.local /
```

---

### Post by lile001 on 2011-12-21
> **Ms. Daisy said:**
> 
If you have really customized Ubuntu and you don't like the idea of a clean reinstall, then you can create an .iso of your system.  I've never tried this, but I've seen at least one thread with instructions and links to tutorials if you're interested in this route.

Although I have a tarball of the entire file system as I indicated, the last time I had a bad crash I installed Ubuntu again from scratch.  This is a pain in the ***, but allowed me to set some things up that I did wrong last time.  Sort of a housecleaning.  So my backing up the entire file system from / on down wasn't really any use at all.   I'd probably do that again, resinstall Ubuntu, it was a couple of evenings work to re-install the programs I have, and I had the chance to clean out some junk that wasn't needed anymore.  For instance, I had several copies of various sound programs, but never removed them once I found one I liked.  "They might come in handy..." like all that junk in my attic.

---

### Post by lukeiamyourfather on 2011-12-21
I suggest you take the time to learn how to use [rsync]("http://en.wikipedia.org/wiki/Rsync"). This is the de facto way to backup files on a Linux system be it to a local disk, local network, or even remote servers. Once you have a routine that you know works the commands can be entered into a shell script, and then you can run the entire backup process with a single command. An example is below.

```

#!/bin/sh
rsync -a --delete --progress /home/luke /mnt/backup/luke
rsync -a --delete --progress /projects /mnt/backup/projects

```

The '-a' means archive mode which keeps things like modified times unchanged (plus a lot of other things). Use 'man rsync' to see the full details. The '--delete' means to delete files on the backup that no longer exist on the source. The first path is the source and the second path is the destination. Each time rsync will look at what has changed (or is new) and only backup those items. This makes the backup faster but still always complete.

If you want to schedule it to run automatically you can use cron. See the manual for cron with 'man cron' for the full details. It sounds like a lot of work (or maybe a little archaic) but in the long run you'll be glad you took the time to learn how to use rsync for too many reasons to list here.

---

### Post by lile001 on 2011-12-21
> **lukeiamyourfather said:**
> I suggest you take the time to learn how to use [rsync]("http://en.wikipedia.org/wiki/Rsync"). This is the de facto way to backup files on a Linux system be it to a local disk, local network, or even remote servers. Once you have a routine that you know works the commands can be entered into a shell script, and then you can run the entire backup process with a single command. An example is below.

```

#!/bin/sh
rsync -a --delete --progress /home/luke /mnt/backup/luke
rsync -a --delete --progress /projects /mnt/backup/projects

```

OK, well thanks for the advice about diving headfirst into command-line driven stuff, but I won't be doing that. I am sure it is just really satisfying to master that stuff, and I am learning more as I go, but I have a business to run, the more time I spend futzing around with Linux the less time I spend making money.  I have just been experimenting with GRsync, which accomplishes what you are recommending without typing a bunch of gobbedegook. This will work a lot better for me.  It's fine to understand what is going on under the hood, however I fail to understand why it is better to use hammer and tongs to accomplish something that can be done in a click.  Discussing this with some folks is like mud wrestling with a pig, the pig doesn't understand why anyone else wouldn't love it. Not implying anything about anyone's ability to squeal, just making an analogy. 

That being said, GRsync allows one to look at the command lines being generated for rsync, a handy feature for learning the nuts and bolts.   This is looking like a useful program, however it lacks one nice feature that the simple Deja Dup has: automatic scheduling.

---

### Post by Paddy Landau on 2011-12-21
I have two backup procedures, one for off-site (on-line) and another on-site (off-line).

*Off-site (on-line)*

I have used [SpiderOak]("https://spideroak.com/") for several years. I find it fantastic, and security is a big plus. It is not free, but it is cheap. It keeps older versions (for as long as you like), so it's easy to go back if you have updated a document and need a previous version.

SpiderOak has other features that are extremely useful, such as synchronising selected folders between computers, and sharing selected folders with other people. It intelligently backs up only changed and non-duplicated data, so despite being over the Internet, it is fast (except for the very first backup).

There is a free trial feature -- use up to 2Gb (no time limit) to test the program. And it's cross-platform.

*On-site (off-line)*

Instead of rsync, I use rdiff-backup. This is rsync with a useful extra feature: it keeps older versions (for as long as you like). This backs up everything onto an external hard drive, and is useful to restore anything that I accidentally delete.

It is not as user-friendly as SpiderOak when restoring older versions, but it's free.

---

### Post by lile001 on 2011-12-21
> **lile001 said:**
> 

That being said, GRsync allows one to look at the command lines being generated for rsync, a handy feature for learning the nuts and bolts.   This is looking like a useful program, however it lacks one nice feature that the simple Deja Dup has: automatic scheduling.

Ubuntu has a graphical scheduling program that interfaces with cron called "scheduled tasks".  This and some experimentation with grsync has allowed me to figure out a simple backup routine that I can understand without having to stay up all night reading manuals.  I had to learn exactly one thing - adding a trailing slash to the rsync command line generated by grsync changes how it treats restored directories.  

Files are stored unencrypted int he target directory, which solves the problem of retrieving one file.  

If I can figure out the online backups now this looks like a good system.

---

### Post by lukeiamyourfather on 2011-12-22
> **lile001 said:**
> ...but I have a business to run, the more time I spend futzing around with Linux the less time I spend making money.

The point of using the command line is to save time in the long run which translates into more time to do other things that make money. :roll:

---

### Post by Jacobonbuntu on 2011-12-22
> **lile001 said:**
> Ubuntu has a graphical scheduling program that interfaces with cron called "scheduled tasks".  This and some experimentation with grsync has allowed me to figure out a simple backup routine that I can understand without having to stay up all night reading manuals.  I had to learn exactly one thing - adding a trailing slash to the rsync command line generated by grsync changes how it treats restored directories.  

Files are stored unencrypted int he target directory, which solves the problem of retrieving one file.  

If I can figure out the online backups now this looks like a good system.

one thing (IMPORTANT!!) gnome schedular is great BUT do not forget that if you have directory names with spaces, put them between "" in the output command of grsync before adding them to gnome schedular. Else the script will stop at the space.

---

### Post by lile001 on 2011-12-22
> **lile001 said:**
> Ubuntu has a graphical scheduling program that interfaces with cron called "scheduled tasks".  This and some experimentation with grsync has allowed me to figure out a simple backup routine that I can understand without having to stay up all night reading manuals.  I had to learn exactly one thing - adding a trailing slash to the rsync command line generated by grsync changes how it treats restored directories.  

Files are stored unencrypted int he target directory, which solves the problem of retrieving one file.  

If I can figure out the online backups now this looks like a good system.

So far so good.  I spend all day stuffing new engineering information into my head, so my goal with computers is to learn the *least *I need to know to accomplish any particular task, then I can go on to do something else.  

Last question:  What to back up?  /home, obviously, but what other directories are important to back up?

---

### Post by Paddy Landau on 2011-12-22
> **lile001 said:**
> What to back up?  /home, obviously, but what other directories are important to back up?
That's it for most people. Unless you have special requirements (which, by your description, you don't), no data is stored anywhere else.

You can back up either your entire [FONT=Fixedsys]/home[/FONT] folder (including the hidden folders and files, i.e. those starting with a point), or only your data. The hidden folders and files usually are not required, but some are -- such as Thunderbird's folder ([FONT=Fixedsys].thunderbird[/FONT]), because it saves all your emails there.

Actually, you want to back up not the entire [FONT=Fixedsys]/home[/FONT] folder, but the entire [FONT=Fixedsys]/home/user[/FONT] folder -- especially if you have an encrypted home folder (you'd rather back up the unencrypted data). If you have more than one user, you want to back up all of the users' home folders. Do not include hidden folders or files within the main [FONT=Fixedsys]/home[/FONT] folder itself.

---

### Post by Zill on 2011-12-22
> **lile001 said:**
> ...Last question:  What to back up?  /home, obviously, but what other directories are important to back up?
Personally, I always backup /etc/ as well as /home/.  The /etc/ directory stores system-wide config info for packages, rather than the user-specific config info which is generally stored in /home/user/ directory "dot" files.

If I need to reinstall the OS then it is a generally a simple matter to copy over config data from the appropriate /etc/ backup file(s), minimising the reconfiguration work required on a "new" installation.  Of course, this should only be done directly if the "old" and "new" package is the same version.  Otherwise there may be slight differences in the config files which must be taken into account.

I currently use [SBackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") for my backups but am now considering changing over to [LuckyBackup]("http://luckybackup.sourceforge.net/") which is, according to the blurb, a "rsync-based GUI data backup utility".  Both applications are in the Ubuntu repos.

---

### Post by srinivasant on 2011-12-28
lile001,

It depends upon your requirement ie., what data are needed for you in case of crash. If you are concerned only about your applications' data, and if you are ok with installing OS by yourself and setting up the new machine after crash, then it is enough to backup only your applications' data ie., your home folder alone (/home/user)

If you need to rebuild your entire system including your system configuration files, then you need look into backing up other files (as Zill said).

Regards,
Srinivasan
[http://www.vembu.com](http://www.vembu.com)

---

### Post by rewyllys on 2011-12-28
> **Zill said:**
> . . . I currently use [SBackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") for my backups but am now considering changing over to [LuckyBackup]("http://luckybackup.sourceforge.net/") which is, according to the blurb, a "rsync-based GUI data backup utility".  Both applications are in the Ubuntu repos.
+1 for LuckyBackup.  I've used it nightly for over a year to back up my /home folder, and have been completely satisfied.

---

### Post by lile001 on 2011-12-29
> **rewyllys said:**
> +1 for LuckyBackup.  I've used it nightly for over a year to back up my /home folder, and have been completely satisfied.

Thanks for all the replies!  I am much enlightened. 

OK, now I have a backup going.  GRsync helped me generate an rsync command line with little pain, which I then copied into a scheduled task in "configure scheduled tasks".  It backs up everything to the spare hard drive (for now) at midnight.  

However, it generates a bunch of warnings because it cannot back up stuff my login doesn't have read/write access to. How do I go about scheduling a task as Root so that it has access to all the files of all the users (me and the wife, basically....)?

---

### Post by Paddy Landau on 2011-12-30
> **lile001 said:**
> How do I go about scheduling a task as Root so that it has access to all the files of all the users (me and the wife, basically....)?
Schedule commands with cron (read up on [crontab]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/crontab.1.html")). Normally, you'd use something like:
```
VISUAL=gedit crontab -e
```But to schedule it as root, you need sudo:
```
sudo VISUAL=gedit crontab -e
```

---

