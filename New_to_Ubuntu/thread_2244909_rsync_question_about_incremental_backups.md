---
title: "rsync question about incremental backups"
date: 2014-09-19
forum: New to Ubuntu
---

### Post by watson524 on 2014-09-19
Hi all,

Working through a few things while setting up the new system and the priority is being diligent about backups. For ease of use, I installed grsync while I learn the various commands but it shows you the actual command line command.

Here's my situation:
1.5Tb internal drive that houses all data (except /home which I will back up separately)
750Gb drive
2Tb drive

My plan to to take the 1.5Tb drive and full copy it to the 2Tb drive once per week. Then daily, I want to take the 1.5Tb drive less 7 directories and copy them to the 750Gb drive.

I've done the intial copies over using the following commands:
rsync -r -t -p -o -g-v --progress -s /media/15tbint/ /media/2tbext
rsync -r -t -p -o -g -v --progress -s --exclude-from=/home/michele/.grsync/notfullbackup /media/15tbint/ /media/750gbext

Where the exclude-from= is a file I set up to exclude the 7 directories I don't need daily.

But I noticed at the start I get "rsync: failed to set times on "/media/750gbext/.": Operation not permitted (1)" and at the end on both I get an exit code 23. I suspect the 23 code is tied to the "failed to set times" part but not sure what to do about that or if I should be concerned as when I look at the 2Tb and 750Gb drive, the file counts are as expected as well as sizes.

 I don't really want to tar and keep backups that way that I can pull by date as I don't have the space for it. I just want to look in my /media/2tbext drive and figure out new and changed files and put them over on the other 2 drives without doing the whole thing each time. I have read the man pages and I must be missing something as I can't figure out the switch that says "look for changes, copy those over, keep all else the same". Also, I don't feel a need to have the destination delete files that are no longer on the source. I don't mind keeping them there JUST in case.

I will work on the cron scheduling at a later date but for now I'm just trying to figure out how not to copy the whole thing over each time.

thanks in advance!

---

### Post by bab1 on 2014-09-19
> **watson524 said:**
> Hi all,

Working through a few things while setting up the new system and the priority is being diligent about backups. For ease of use, I installed grsync while I learn the various commands but it shows you the actual command line command.

Here's my situation:
1.5Tb internal drive that houses all data (except /home which I will back up separately)
750Gb drive
2Tb drive

My plan to to take the 1.5Tb drive and full copy it to the 2Tb drive once per week. Then daily, I want to take the 1.5Tb drive less 7 directories and copy them to the 750Gb drive.

I've done the intial copies over using the following commands:
rsync -r -t -p -o -g-v --progress -s /media/15tbint/ /media/2tbext
rsync -r -t -p -o -g -v --progress -s --exclude-from=/home/michele/.grsync/notfullbackup /media/15tbint/ /media/750gbext

Where the exclude-from= is a file I set up to exclude the 7 directories I don't need daily.

But I noticed at the start I get "rsync: failed to set times on "/media/750gbext/.": Operation not permitted (1)" and at the end on both I get an exit code 23. I suspect the 23 code is tied to the "failed to set times" part but not sure what to do about that or if I should be concerned as when I look at the 2Tb and 750Gb drive, the file counts are as expected as well as sizes.

 I don't really want to tar and keep backups that way that I can pull by date as I don't have the space for it. I just want to look in my /media/2tbext drive and figure out new and changed files and put them over on the other 2 drives without doing the whole thing each time. I have read the man pages and I must be missing something as I can't figure out the switch that says "look for changes, copy those over, keep all else the same". Also, I don't feel a need to have the destination delete files that are no longer on the source. I don't mind keeping them there JUST in case.

I will work on the cron scheduling at a later date but for now I'm just trying to figure out how not to copy the whole thing over each time.

thanks in advance!
The easiest way to do this is to use [rsnapshot]("http://www.backupcentral.com/wiki/index.php/Rsnapshot").  The concept was originally thought of by [Mike Rubel]("http://www.mikerubel.org/computers/rsync_snapshots/").  Read the section on [incremental backups]("http://www.mikerubel.org/computers/rsync_snapshots/#Incremental") for the original idea.

I backup about 1TB with rsnapshot.  Except for the original backup it is very fast.  There is no need for restore functions as the files are copied and you can see the daily, weekly, monthly and yearly structure.  It's very intuitive.  I wroe my own wrapper script to mount the backup drive and test before starting the actual backup.

---

### Post by SeijiSensei on 2014-09-19
Are you backing up to a device with an NTFS filesystem?  This will have all sorts of problems because NTFS has no equivalents for many of the features of a POSIX filesystem that Linux uses.  Permissions, timestamps, and symbolic links all have problems backing up to NTFS.  The "rsync: failed to set times" error is one symptom of these problems.

If the device is formatted with NTFS, I suggest you reformat it to ext4 and try rsync again.

Rsync is "differential" if you use simply the "-a" ("archive") switch.  It will only copy files that have changed on the source.  Once you have run it the first time, the next cycle will transfer many fewer files.  Try using just "rsync -av" to make the target a mirror of the source and display a list of the files transferred.  My backup script runs the command:

```
rsync -av source target --exclude-from=/path/to/list/of/exclusions
```

Still this method doesn't really constitute what I think of as an incremental backup, which has a full backup to start and periodic additions indexed by date.  I think I could write a script to do this that would first run "rsync -avn" (using the "-n," or "dry-run," switch) to get the list of files that would be transferred.  Then I'd have the script create a dated subdirectory and run rsync again with that filelist to copy only the changed files into the dated subdirectory.  I might give that idea a try myself!

---

### Post by Michael_McKenney on 2014-09-19
Does rsync work with tape drives?

---

### Post by watson524 on 2014-09-19
> **SeijiSensei said:**
> Are you backing up to a device with an NTFS filesystem?  This will have all sorts of problems because NTFS has no equivalents for many of the features of a POSIX filesystem that Linux uses.  Permissions, timestamps, and symbolic links all have problems backing up to NTFS.  The "rsync: failed to set times" error is one symptom of these problems.

If the device is formatted with NTFS, I suggest you reformat it to ext4 and try rsync again.


Nope took your advice and put everything to ext4 figuring samba (still a problem) could deal with things for what I needed to get through for windows.


> **SeijiSensei said:**
> 
Rsync is "differential" if you use simply the "-a" ("archive") switch.  It will only copy files that have changed on the source.  Once you have run it the first time, the next cycle will transfer many fewer files.  Try using just "rsync -av" to make the target a mirror of the source and display a list of the files transferred.  My backup script runs the command:

```
rsync -av source target --exclude-from=/path/to/list/of/exclusions
```

Still this method doesn't really constitute what I think of as an incremental backup, which has a full backup to start and periodic additions indexed by date.  I think I could write a script to do this that would first run "rsync -avn" (using the "-n," or "dry-run," switch) to get the list of files that would be transferred.  Then I'd have the script create a dated subdirectory and run rsync again with that filelist to copy only the changed files into the dated subdirectory.  I might give that idea a try myself!

I think the -a might be what I'm looking for them as I don't need to worry about dated subdirectories since I don't necessarily care about the "when". So -a basically checks for files and adds new ones and then takes the newer copies of modified ones if the modified date or something on the source is newer than the target? I think I also read that -a actually takes the place of many of the options I have listed individually.

---

### Post by SeijiSensei on 2014-09-19
> **watson524 said:**
> I think the -a might be what I'm looking for

The "-av" combination is pretty much the only rsync option I ever use, along with --include-from, --delete-excluded, etc. when appropriate.

> **Michael_McKenney said:**
> Does rsync work with tape drives?
No, you use **tar** for that:
```

cd /
sudo tar -czpf /dev/st0 .

```
writes a gzip-compressed copy of the file system to the tape device on /dev/st0.  You should also look into the **mt** command which lets you control the device with rewind, fast forward, etc.

What you could do is write a script to run rsync nightly, the copy the backup to tape with tar.

---

