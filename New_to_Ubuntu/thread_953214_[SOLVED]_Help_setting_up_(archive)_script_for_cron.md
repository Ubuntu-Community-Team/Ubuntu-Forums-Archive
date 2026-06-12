---
title: "[SOLVED] Help setting up (archive) script for cron"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by BassKozz on 2008-10-19
I have the following commands that I want to add to cron for weekly and monthly backups...
**_Weekly_**
```

7z a -t7z "/media/backup-drive/Backups/DATA/Weekly/$(date +"%Y%m%d").7z" /media/backup-drive/Shares/DATA -mx9

```
**_Monthly_**
```

7z a -t7z "/media/backup-drive/Backups/DATA/Monthly/$(date +"%Y%m%d").7z" /media/backup-drive/Shares/DATA -mx9

```

Now I can simply add these to my crontab by entering:
```

sudo crontab -e 0 01 * * 0 7z a -t7z "/media/backup-drive/Backups/DATA/Weekly/$(date +"%Y%m%d").7z" /media/backup-drive/Shares/DATA -mx9
sudo crontab -e 0 02 01 * * 7z a -t7z "/media/backup-drive/Backups/DATA/Monthly/$(date +"%Y%m%d").7z" /media/backup-drive/Shares/DATA -mx9
```
Which will run my weekly backup every sunday @ 1am, and my monthly backup on the 1st of the month @ 2am.  But I want to turn this into a script so that I can place the following code after the archiving is completed successfully: 
```

echo "Weekly Backup Successful: $(date)" >> /tmp/mybackup.log
echo "Monthly Backup Successful: $(date)" >> /tmp/mybackup.log

```

But I don't know how to code a .sh script, how can I go about doing this?
And what is the syntax used to comment a script (i.e. "//")?
TiA,
-BassKozz

---

### Post by talsemgeest on 2008-10-19
Take a look here: [http://ubuntuforums.org/showthread.php?t=203279]("http://ubuntuforums.org/showthread.php?t=203279")

---

### Post by BassKozz on 2008-10-20
> **BassKozz said:**
> 
And what is the syntax used to comment a script (i.e. "//")?
Solved: '#' ;)
> **BassKozz said:**
> 
But I don't know how to code a .sh script, how can I go about doing this?
Solved: created the following scripts (1 for each weekly/monthly)
```

#!/bin/bash
#Weekly Backup script
7z a -t7z "/media/backup-drive/Backups/DATA/Weekly/$(date +"%Y%m%d").7z" /media/backup-drive/Shares/DATA -mx9
echo "Weekly Backup Successful: $(date)" >> /media/backup-drive/Backups/DATA/mybackup.log

```
```

#!/bin/bash
#Monthly Backup script
7z a -t7z "/media/backup-drive/Backups/DATA/Monthly/$(date +"%Y%m%d").7z" /media/backup-drive/Shares/DATA -mx9
echo "Monthly Backup Successful: $(date)" >> /media/backup-drive/Backups/DATA/mybackup.log

```
:D

---

