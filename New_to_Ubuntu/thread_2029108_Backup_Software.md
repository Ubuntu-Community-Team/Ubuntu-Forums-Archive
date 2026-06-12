---
title: "Backup Software"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by daniel_owen_uk on 2012-07-19
Currently have two key folders on my machine.

1. Photos
2. Music

Normally I just move these manually to our fileserver under the stairs.

Is there some software available for ubuntu that will do a period backup of new/changed files?

---

### Post by ptn107 on 2012-07-19
deja-dup

If you're running 12.04 LTS you already have it under System Settings -> System -> Backup.

If you're running 10.04 LTS, 11.04, or 11.10 you will need to install it via the terminal or software center.

---

### Post by bryncoles on 2012-07-19
I like using grsync!  It's in the repos.

---

### Post by sudodus on 2012-07-19
If you like terminal commands, run ***rsync***! The manual ```
man rsync
``` contains good descriptions with examples as well as an extensive list of the options. Rsync is the engine inside many of the GUI backup programs.

An alternative to a backup program is a synchronizing program, for example ***Unison***. This way you can keep the second set of files clean from obsolete files, which can be good or bad depending on the situation.

You may want both of them: Normally you backup your files (one direction only), but sometimes you get rid of obsolete files.

---

### Post by daniel_owen_uk on 2012-08-06
Got round to  playing with deja-dup (or backup as 12.04 likes to call it).

And... it's close...

I would however prefer the files to be backed up as is.  deja-dup creates gz files, that I am sure are smaller (and encrypted should I wish) but I will still prefer a copy.

---

### Post by markbl on 2012-08-06
I've been using rsnapshot, which uses rsync under the covers, to do my cron daily backup for years. Rsnapshot is in the standard packages. It also pulls files from my wife's windows pc running deltacopy, which is a free windows rsync server.

---

### Post by mastablasta on 2012-08-06
> **daniel_owen_uk said:**
> Got round to playing with deja-dup (or backup as 12.04 likes to call it).
 
And... it's close...
 
I would however prefer the files to be backed up as is. deja-dup creates gz files, that I am sure are smaller (and encrypted should I wish) but I will still prefer a copy.
 
then grsync (or rsync in terminal) - it will periodically (on a time you set) check the directories and copy any new files to your file server.
[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)
 
grsync is in software center.

---

