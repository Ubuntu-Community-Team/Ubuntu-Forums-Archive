---
title: "Some help with failing backups.  Easy question for someone who knows this stuff."
date: 2014-01-23
forum: New to Ubuntu
---

### Post by lile001 on 2014-01-23
I am attempting to use Deja Dup and/or duplicity for backups.  I have been reading and re-reading [this page]("https://help.ubuntu.com/community/DuplicityBackupHowto") about duplicity and so far haven't been able to make much sense out of it as it goes on about passphrases and other stuff I don't really understand.  I'm reluctant to experiment when I am unsure how to proceed, as I don't want to trash an existing backup.  

I had a backup of my computer on a second hard drive (and some other places!) when the computer crashed (On Christmas day.  Merry Phreakin' Christmas.) .  With help from a friend who actually understands all this stuff I was able to reinstall Ubuntu and restore, all is well!  But the computer now has a different name than it used to, so Deja Dup complains about backing up to a place where there is a backup from a differently named computer.  As this requires an OK from me every time, so much for the automatic backup in the middle of the night.  This is the smaller problem, and may go away if I can ever get rid of the old backup using Duplicity.

**What I want to accomplish is remove the oldest backups correctly using Duplicity, then get Deja Dup working correctly so it doesn't fail all the time. ** 

Although Deja Dup is set to "get rid of old backups when the drive is full", it always complains of a full drive and fails to finish backing up.  I am backing up about  33 GB of stuff to a 1 TB drive, so this doesn't make any sense.  So far no backups have worked since Christmas.  

I found a thread that says[ Deja Dup needs a tmp directory]("http://askubuntu.com/questions/191653/deja-dup-backup-change-use-of-tmp-to-another-folder-location"), and if tmp is full that could be the problem (I haven't a clue, just grabbing at straws here)  So I did this:

Make a tmp directory on Bigdrive2, then 
```
TMPDIR=/media/Bigdrive2/tmp export TMPDIR 
deja-dup-preferences
```

/media/bigdrive2/tmp has 190 GB free.   I won't know if this solves the Deja Dup "Backup drive full" problem for several hours as it takes some time to work.  

The next step I'd like to try is making some room with Duplicity. 

So the ingredients I have are a number of old backups in /media/Bigdrive2/backup.  The oldest files are from December 15, 2013, the newest are from Dec 25.  The [Duplicity docs I find ]("https://help.ubuntu.com/community/DuplicityBackupHowto")go on about passphrases and other stuff 
I don't have a clue about.  

Can someone help me craft a correct Duplicity command to get rid of the oldest files in this old backup?  Also is there something else I should do to get Deja Dup backing up and deleting old files properly?  
Yes I RTFM'd, but I am just not following the Duplicity documentation I can find, and don't want to screw things up by fumbling around.

---

### Post by sudodus on 2014-01-23
I do backup regularly, but not with the tools that you use.

The system tmp directory is /tmp  and it is normally in the root partition '/'. There might be too little free space in that partition. Maybe it is possible to set duplicity or DejaDup to use another temporary directory than /tmp. In that case you should be able to change a setting so that it uses
[B]
[COLOR=#222222][FONT=Verdana]/media/bigdrive2/tmp[/FONT][/COLOR][/B]

Try these commands according to the link you referred to

```
TMPDIR=[COLOR=#0000ff]/media/bigdrive2/tmp[/COLOR]
export TMPDIR
deja-dup-preferences
```

Copy and paste one line each time and finish with the enter key.

Notice that it is important to get upper case and lower case correct in linux. **Bigdrive** and **bigdrive** are different directory names.

Good luck

---

### Post by whitesmith on 2014-01-23
A while back I looked into backup tools for an Ubuntu system I was assembling for a buddy. DejaDup seemed like overkill (he's a novice) so I went with Simple Backup Suite. It does the job with a minimum of fuss, yet it's reasonably configurable. Backups can be scheduled, as can a full backup in addition to the incrementals. Cutoff dates are adjustable (e.g., remove all .inc files more than a month old). Why not give this one a peek?

---

### Post by lile001 on 2014-01-25
Thanks, Sudodus.  I think I already did this, although I will go back again carefully checking caps and such. Dislexic Brain doesn't really register caps, which makes me a terrible Linux guy and a suckish C programmer.

Thanks, Whitesmith.  If I can't get anywhere with Deja Dup and/or Duplicity I will give this a try.

The next step I'd like to try is making some room with Duplicity.

So the ingredients I have are a number of old backups in /media/Bigdrive2/backup. The oldest files are from December 15, 2013, the newest are from Dec 25. The [Duplicity docs I find ]("https://help.ubuntu.com/community/DuplicityBackupHowto")go on about passphrases and other stuff
I don't have a clue about.

Can someone help me craft a correct Duplicity command to get rid of the oldest files in this old backup?  This should be easy for someone who knows what they are doing.

Unless we can catch the interest of someone who uses DejaDup and/or Duplicity, I second the advice of *whitesmith*, to select a simpler backup program. I used ***Simple Backup*** years ago, and can verify that it is fairly simple to use.

There are other alternatives too. If you are happy with the command line and shell-script files, ***rsync*** is a very good tool for backup. If you would be happy with synchronizing (1:1 rather than a lot of backup versions), ***Unison*** is a good tool with a GUI user interface. If you want a complete clone or compressed image of the system, ***Clonezilla*** can do it for you.

Here is a good reason not to use [SimpleBackupSuite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite"):  It is not being maintained.

So, attempting to plow through this duplicity stuff solo, the first non-dangerous thing I have found to do is this:

```
duplicity collection-status file:///media/Bigdrive2/backup
```

This tells me, among other gibberish I don't understand very well, that I have two backups in place:  


```
Chain start time: Sun Dec 15 22:14:31 2013Chain end time: Wed Dec 25 07:56:17 2013
Number of contained backup sets: 2
Total number of contained volumes: 5186
 Type of backup set:                            Time:      Num volumes:
                Full         Sun Dec 15 22:14:31 2013              5158
         Incremental         Wed Dec 25 07:56:17 2013                28
-------------------------
No orphaned or incomplete backup sets found.



```

The next thing to look into is room. I was mistaken when I said I had plenty of room.  After counting up some mounted drives that are bound to subdirectories of the home folder, I find I have 300 gigs of stuff I am trying to back up.  Holy Hard drive, Batman!  No wonder I run out of space.  One of the first things I should do is try to prune this down - I believe there are some duplicates of some of this stuff, and a lot of dubious garbage that should have been deleted long ago.  If I had no backup on my empty drive, I'd have 500 Gig or so to put this backup on, so that might be enough, but with an existing backup on there already from the old machine, I think it runs out of space.

So with great trepidation I deleted the old backup files on the extra hard drive Bigdrive2.  Only it still doesn't have any room in it.  
I discovered it has its own trash file, /.Trash-0, which is owned by root and still has all the old backups.  Eventually I blundered on a way to get rid of these from the command line which I won't bore you with.  

So finally I was able to put together a duplicity command after a Saturday morning's study.  What a lot of effort for something simple.  The key was to find a harmless command that can be used with duplicity - "collection-status"  that allowed me to screw around until I blundered into the right syntax.   

The whole command was 

```
 duplicity --no-encryption --exclude /home/lawrence/Bigdrive/.Trash-1000 --exclude /home/lawrence/Shared/.Trash-1000 /home/lawrence file:///media/Bigdrive2/backup
```

And the parts are: 

--no-encryption is needed so I don't need a passphrase every time.  No need to encrypt backups when they stay on my own system.  

--exclude fixes it so I don't backup the trash folders that seem to proliferate on every storage device.  

/home/lawrence says to back up my home directory

and finally, file:///media/Bigdrive2/backup  sends the backup to the correct place.  This was hard to figure out, as I could not understand why there needs to be three "/"s in a row.  

Then set up a cron job (which I also won't bore you with) that runs duplicity every day at midnight invoking the same command as above, after another half-hour's headscratching.  

then copy all this stuff into a text file called "what the hell did I install?" where I keep a record of this kind of stuff.  I can't remember what I ate for breakfast yesterday, let alone some obscure Linux command I made 6 months ago, so any important stuff like this that I set up, I keep a record of so that I can set it up again someday.

Why not use a GUI backup software as suggested above?  Well, Deja-Dup seems to be too simplistic, I started researchign the other ones suggested and the first mention I found of them suggested they were not being supported anymore.  Duplicity, if you ever figure it out, is really straightforward, but has so damn many options.  Well it looks like I have something that works now.

---

