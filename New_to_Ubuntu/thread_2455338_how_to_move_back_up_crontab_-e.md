---
title: "how to move back up crontab -e"
date: 2020-12-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-17
made the dumb mistake of deleting my crontab-e
so made a script that backs up cron job once a day
it saves crontab -e to /home/ray/cron-backup.txt
in the event that i again delete what is the correct mv paste terminal command to install the backup-txt and to i have to switch to root to run/tks

---

### Post by TheFu on 2020-12-17
Open 2 terminals - say A and B.
Run **crontab -e** in A.
Use **more ~/cron-backup.txt** in B (i.e. the other terminal).

Use that fancy mouse to copy/paste between the windows.
While you are there, perhaps adding a handy comment to the crontab with the positional meanings spelled out would be good too?
```
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command --arg1 --arg2 file1 file2 2>&1
```
That is only valid for crontabs created through the **crontab -e** command. It isn't valid for any located in /etc/ anywhere.
Those are all comments.

---

### Post by rburkartjo on 2020-12-17
fu could i do it in one command also you said more did you mean move/tks

---

### Post by TheFu on 2020-12-17
'more' is a pager program. It was what I meant.  You could use 'less' of you prefer. Less is a pager too.  Almost always, I'll use more or less rather than 'cat' - cat is next to useless 99.9999% of the time we see it.  I use 'tac' more often than 'cat'.  You can look up what tac does and it will make sense. ;)

mv'ing a file into a crontab location doesn't do some important checks or signal cron to re-read files. Don't do that.

---

### Post by rburkartjo on 2020-12-17
fu tks again

---

### Post by kevdog on 2020-12-21
Had no idea tac was even a utility.  Made me laugh.

---

### Post by ActionParsnip on 2020-12-21
You can make a crontab backup using
```

crontab -l > $HOME/Desktop/crontabBackup-`date +"%d-%m-%Y"`

```
Is this what you are doing?

---

### Post by ActionParsnip on 2020-12-21
> **TheFu said:**
> 'more' is a pager program. It was what I meant.  You could use 'less' of you prefer. Less is a pager too.  Almost always, I'll use more or less rather than 'cat' - cat is next to useless 99.9999% of the time we see it.  I use 'tac' more often than 'cat'.  You can look up what tac does and it will make sense. ;)

mv'ing a file into a crontab location doesn't do some important checks or signal cron to re-read files. Don't do that.

I'd prefer dog to be the name of the command rather than tac. I have made aliases ;)

---

