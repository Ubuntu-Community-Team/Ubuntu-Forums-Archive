---
title: "Script for backup"
date: 2013-04-25
forum: Programming Talk
---

### Post by marjoh05 on 2013-04-25
I found some script online i need to use for backup purpose. I have a windows server that transfer daily backup to my ubuntu 12.04 server. Because Windows Server Backup wont save more than one backup at once to a shared folder i have a script that weekly copy and rename(renames with the date) and puts it in another folder. The only problem is that the HDD gets pretty full after some months, so i need a script that deletes every file thats older than 4 weeks, but wont delete any if there isnt any more files added(if the backup stops working).

Found a script that deletes all files who is older than 3 days: how can i set it to 4 weeks? Or how can i set it to not delete files when its 4 or less folders in my weekly backup folder?

find /u1/database/prod/arch -type f -mtime +3 -exec rm {} \;

Thanks :-)

---

### Post by schragge on 2013-04-25
Seems like a job for [logrotate]("http://manpages.ubuntu.com/manpages/precise/en/man8/logrotate.8.html"). Also see [savelog](http://manpages.ubuntu.com/manpages/raring/en/man8/savelog.8.html).

Answering your direct question, it seems obvious if you know that 4 weeks make 28 days :)
```
find /u1/database/prod/arch -type f -mtime +28 -delete
```

---

### Post by marjoh05 on 2013-04-26
haha, you made me feel stupid now... :P well part one of the probem is solved! thanks :-)

---

