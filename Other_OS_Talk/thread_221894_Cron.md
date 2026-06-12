---
title: "Cron"
date: 2006-07-24
forum: Other OS Talk
---

### Post by kriding on 2006-07-24
where can I get alist of CRON commands. I'm trying to set up a task to automatically back up my data and email me when it's done, so that I candownload it.

---

### Post by Hanj on 2006-07-24
I haven't used cron much, but doing what you want shouldn't be hard. To add a task to cron you add a line to your crontab file, which you can edit using the command *crontab -e*. The line contains info on which command to run and when to run it (you can find details [here]("http://www.deluxnetwork.com/linux/guides/crons.php") for instance). 

So just edit the file, and tell cron to run your backup script at a desired interval.

---

