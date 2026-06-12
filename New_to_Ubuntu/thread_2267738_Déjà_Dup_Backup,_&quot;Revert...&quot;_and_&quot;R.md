---
title: "Déjà Dup Backup, &quot;Revert...&quot; and &quot;Restore...&quot; not working on some files"
date: 2015-03-03
forum: New to Ubuntu
---

### Post by pmi2 on 2015-03-03
The "Restore Missing Files..." and "Revert to Previous Version..." functions do not seem to work on some (not all but only ***some***) of the folders backed up using Deja-Dup. I am referring to the app just called "Backups" in System Settings.

I have verified that backing up and restoring the complete directory tree, from say ~/Music on down, works with no errors.  Therefore I know that all files get backed up.  I have also verified that restoring individual files using right-click and Revert or Restore works in most folders, but not all.

Where it does NOT work is inside some music folders a couple levels down, which I created when I ripped a few new CDs.  Not all music folders, just in one or two.

In that instance, "Restore Missing..." does nothing, and produces no error.
"Revert..." tries to run, but fails with the following:

> Could not restore ‘/home/peter/Music....’: File not found in backup

Again, I have verified that the file in question ***is*** in the backup and ***does*** get restored with a complete directory tree, just not with this function from inside the folder in the File Manager.

I have also verified that the same functions work on the rest of my Home directory as expected, just not on some of my music sub-folders.

Thanks for reading.

-------------

Ubuntu 14.04, installed about ~3 weeks ago, .mp3's ripped from CDs using Audex, mid-range desktop with a quad core i5 and 4Gb ram, OS installed with default file system, only change was adding one line to fstab to automount a second hard drive.

---

### Post by deadflowr on 2015-03-03
Duplicate threads
See here
[http://ubuntuforums.org/showthread.php?t=2267440](http://ubuntuforums.org/showthread.php?t=2267440)

Instead of posting a new thread, simply bump the old one
From [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Bumping your thread if you receive no answer is acceptable. Premature and excessive bumping could attract staff attention and action. If you wish to bump, consider time zones - the one with your answer might be asleep. Bumping your post means it will not appear in the unanswered posts search and will escape the notice of the Unanswered Posts Team.

This one is now closed

---

