---
title: "rsync script help"
date: 2011-05-03
forum: Programming Talk
---

### Post by ant2ne on 2011-05-03
I'm looking at rsync --help and man rsync (well I skimmed it) and I'm trying to find something that will fit my backup needs.

I want to synchronize (actually locally not remotely) a variety of file types and sizes with a cron script. I want to **never **delete modify the source. But, I do want to update the destination files if the source files have been modified/deleted.

---

### Post by oldfred on 2011-05-03
Several threads with examples, I used MountainXs with modifications:

Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

---

### Post by ant2ne on 2011-05-03
in none of those links do I see anything about NOT removing source files with rsync. At least not explicitly. storeBackup looks cool and powerful, but it is not what I'm looking for.

---

### Post by SeijiSensei on 2011-05-03
Rsync never deletes source files. 

If you select the "--delete" option, it will delete files *on the target* that don't exist in the source, but it always leaves the source files alone.  If you don't use --delete, the target will grow to encompass the most recent versions of all files ever backed up.

I could see a way where the source files might be deleted if you somehow reversed the direction of the rsync process and ran it from the target onto the source with --delete enabled.  However, if you consistently run
```
rsync -av source target [options]
```
the source files will remain intact.

---

### Post by AbsolutIggy on 2011-05-03
> **SeijiSensei said:**
> Rsync never deletes source files. 


Not by default, anyway.. unless you specify the option 
```
--remove-source-files   sender removes synchronized files (non-dir)

```

If you leave this option out, the source files will not be changed!

---

### Post by hjclaes on 2012-03-18
> **ant2ne said:**
> 
I want to synchronize (actually locally not remotely) a variety of file types and sizes with a cron script. I want to **never **delete modify the source. But, I do want to update the destination files if the source files have been modified/deleted.

Hi,

[COLOR=Red]*I think with your backup strategy you have a good chance to lose data.*[/COLOR]

Let me explain:
Some time ago, I found a file (with a presentation) being corrupted (for whatever reason). I didn't access that file for about half a year. I looked into my backup and found the not-corrupted version in a backup which was something more than 6 months old. I have these very old backups, because I'm using storeBackup, which is very space efficient. (Btw, in about a week my oldest still existing backup will be 9 years old. :p )

With your backup strategy, you would save the (last) corrupted version only. This would be disastrous especially if you would run into problems with you file system software or with your hard disk. In this case you have a good chance to destroy (big parts of) your backup also. :shock:

  :)

---

