---
title: "[SOLVED] Looking for help to backup with cp, but exclude hidden files"
date: 2006-10-29
forum: Programming Talk
---

### Post by bswilson on 2006-10-29
Friends,

I am trying to create a script for use with multiple users on my Ubuntu system.  I want to use **cp**, essentially in this way:

```
cp -rup /home/user1 /media/BACKUP/user1
cp -rup /home/user2 /media/BACKUP/user2
cp -rup /home/user3 /media/BACKUP/user3
...
```

If I can lick my problem, I'll write a small shell script and call it from **cron**.  My problem is that when I use **cp -rup**, it backs up all the hidden files in the users' home directories, such as the ones that begin with a period.  I don't want to back up things like **.bash_history** or any of the program configurations -- I just want data files.

Has anyone figured this out?  I've tried searching through the forum for people doing this another way, say, with **rsync** -- but I couldn't find what I was looking for...
 
 
[COLOR="Navy"]*Edit 2006-10-30: I forgot to mention, I can certainly do what I'm after by dragging and dropping the files via nautilus; it's just that I want to script this activity...*[/COLOR]

---

### Post by rydow on 2006-11-28
I use rsync on all of home like this:
sudo rsync -a -u --progress home /media/SEA_DISC

Take a look at man of rsync and look for the --exclude option that would give you what you are after I think.

Good luck
Jonas

---

### Post by bswilson on 2007-01-11
Thanks so much, **rydow**!  I have been able to create a script that works, thanks to your tip on using **rsync**.  My external USB hard drive is mounted as /media/BACKUP, so here's my script:

```
rsync -a -u --exclude="- *." /home/ /media/BACKUP
```

This basically backs up all my family's home directories to my USB drive.  The other flags preserve ownership, dates, permissions, etc. (-a) and only copy files that are newer than the destination (-u).  The last flag (--exclude="- *.") tells **rsync** not to copy any file that begins with a dot.

Thanks!

---

### Post by mcglnx on 2007-01-11
> **bswilson said:**
> Thanks so much, **rydow**!  I have been able to create a script that works, thanks to your tip on using **rsync**.  My external USB hard drive is mounted as /media/BACKUP, so here's my script:

```
rsync -a -u --exclude="- *." /home/ /media/BACKUP
```

This basically backs up all my family's home directories to my USB drive.  The other flags preserve ownership, dates, permissions, etc. (-a) and only copy files that are newer than the destination (-u).  The last flag (--exclude="- *.") tells **rsync** not to copy any file that begins with a dot.

Thanks!


You can also create a file containg the list of excluding patterns. This is quite powerful! check the man pages!
Cheers,
M

---

### Post by AgenT on 2007-01-11
[rsnapshot]("http://www.rsnapshot.org/") is even better than rsync because it allows for multiple backups from daily, weekly to even monthly. And it uses the rsync/diff method which means that having daily and weekly backups will NOT use up a lot more space than having just one backup. Only new files will take up extra space. Very useful when, for example, a file is required that was deleted a week prior.

Use rsnapshot with cron and have daily, weekly and monthly backups automated.

---

### Post by mcglnx on 2007-01-13
Well done! excellent!

It uses rsync in fact :)
As well with hard links - this prevent to duplicate disk space. This is native in the OS but for some reason few is using it!
Something quite simple but still inexisting under other OS,...

---

### Post by babounours on 2007-10-24
why do you use --exclude="- *." instead of --exclude=".*" ? as I read it , it excludes all the files ending with a dot not the ones beginning with a dot. moreover the - is not necessary as you already specified the exclude option

---

