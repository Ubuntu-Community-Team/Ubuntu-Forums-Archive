---
title: "rsync - when it backs up a location"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by Mike_tn on 2012-03-13
What does it mean when rsync's verbose backup run output (in the Grsync gui) shows locations but no files.   I sometimes see what seems to be many locations backed up, lines ending in a slash, but not sure why. By file I mean it has an extension on it and opens with a program, those are not my concern here.

Rsync typical use for me is to back up some ordinary personal nested folders with files in them. They may have a lot of file additions or deletions and the rsync generated file changes appear in a long list with their directory in front of each them. I understand that part. But sometimes I see maybe this rsync output from the gui for folder locations that have always been there;
[FONT=Lucida Console]
[/FONT]```
***Launching RSYNC command (simulation mode):
rsync -r -n -t -v --progress --delete -l -s /home/ /home/awayfromhome/

sending incremental file list
./
share/
share/apps/k3b/
abc/update.log

sent 1073 bytes received 163 bytes 2472.00 bytes/sec
total size is 45328 speedup is 36.67 (DRY RUN)
Rsync process exit status: 0
```I typed that code, it isn't listing everything.  The update.log is a file but the rest is not, but some rsync outputs show not one file copied just directory locations listed for locations that have always been there and have been backed up before. If I didn't change the folder names I was wondering what it was backing up. Perhaps it's copying invisible metadata associated with the location? I just can't connect my doing anything to the locations that appear. The backup itself seems fine as far as I can tell so this is not an emergency just an education in Linux.

---

### Post by wyliecoyoteuk on 2012-03-13
maybe backing up hidden files?

have you tried the extra verbose mode?
e.g.

rsync -r -n -t -vvv --progress --delete -l -s /home/ /home/awayfromhome/

---

### Post by Mike_tn on 2012-03-13
> -vvvHmmm I never tried that. Thanks. Will give it a go next time I see it happen in a dry run.

---

