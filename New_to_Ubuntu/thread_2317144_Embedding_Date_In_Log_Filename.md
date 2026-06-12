---
title: "Embedding Date In Log Filename"
date: 2016-03-13
forum: New to Ubuntu
---

### Post by kazz2 on 2016-03-13
I have used sudo crontab -e to create a pair of chronological backups of the two main shared directory structures on my server. That command is of the format:

```

30 2 * * * rsync -avh --delete /mnt/plex/ /mnt/extbkp/serverBackup/plex/ 2>&1 | tee -a /var/log/extbkp/backup.log && rsync -avh --delete /mnt/common/ /mnt/extbkp/serverBackup/common/ 2>&1 | tee -a /var/log/extbkp/backup.log

```

I would like to change the log filename (backup.log) to begin with the current date beginning with year then month, followed by day. Resulting in a filename something along the lines of:

```

YYYY-mm-DD-backup.log

```

I've seen the use of quotes or tick marks and what appears to be a keyword 'date' followed by percent signs, etc. But I've not had any luck making that work when using > to convert output to a file. Can anyone help me identify a proper syntax?

Thank you!

---

### Post by steeldriver on 2016-03-13
cron is funny about percent signs - see [http://unix.stackexchange.com/questions/29578/how-can-i-execute-date-inside-of-a-cron-tab-job](http://unix.stackexchange.com/questions/29578/how-can-i-execute-date-inside-of-a-cron-tab-job)

So it would probably need to be 
```

`date +\%Y-\%m-\%d`-backup.log

```

or (using the alternate command substitution syntax)
```

$(date +\%Y-\%m-\%d)-backup.log

```

---

### Post by kazz2 on 2016-03-14
I do believe you nailed it in your first example.

I saw the update to the thread late last night and updated my cron job to give it a shot. Sure enough, I have an appropriately named log file today.

I was trying to test it interactively at the command line and having a hard time. The final affirmation will be tomorrow when I check and see a new file with tomorrow's date at the beginning of it's name. I need to make it work w/o sudo at the command line but my big fire's out for now.

Thanks again!

---

