---
title: "[SOLVED] What is going on with my BASH script?"
date: 2008-08-12
forum: Programming Talk
---

### Post by Titan8990 on 2008-08-12
I have a cron job that backups my computer via rsync. When it does this it keeps a log and drops in the /var/log/backup directory. I have a weekly cron job (which is not functioning correctly) that takes those log files tars them and places them in another folder. 

I'm not sure exactly what is going wrong but it appears that it is taring recursively so I have archives inside of archives inside of archives. A log file is less than 1MB. I have 6 weeks worth of tared log files. The newest one is 2.4GB in size. I tried extracting but it is a endless loop tarballs.

Also, whenever I extract I get the full absolute path name. EG - I extract a tar and it starts with var/backup/oldlogs, var will only contain the folder backup.

Anyways, I was hoping someone could point out the error in my script:

```

#! /bin/sh

tar -cvf /var/log/backup/oldlogs/$(date +%m%d%y).tgz /var/log/backup/*

rm /var/log/backup/rsync*

```

Also, any idea on why the last line in the script would not show up on the board using PHP brackets?

---

### Post by decoherence on 2008-08-12
Either move oldlogs out of backup so it isn't grabbed by tar, or use tar's --exclude flag to exclude them.

---

### Post by Titan8990 on 2008-08-12
Would this be correct? 

#! /bin/sh

tar -cvf --exclude=/var/log/backup/oldlogs/ /var/log/backup/oldlogs/$(date +%m%d%y).tgz /var/log/backup/*

rm /var/log/backup/rsync* 


In the man pages for tar is said something about exclude being related to a pattern. Do you know what that means exactly?

---

### Post by decoherence on 2008-08-12
i'm no tar expert, but 

```
tar -cvf /var/log/backup/oldlogs/$(date +%m%d%y).tgz --exclude=/var/log/backup/oldlogs/ /var/log/backup/
```

would appear to be correct

---

