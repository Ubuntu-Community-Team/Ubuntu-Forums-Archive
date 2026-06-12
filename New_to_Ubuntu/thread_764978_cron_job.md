---
title: "cron job"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by GoCool on 2008-04-24
I did something on my computer and my cron job stopped working. I think I tried to change my display name which caused it, but not sure. As a remediation I removed the cronjob by giving the following command
```

crontab -r

```
and created the cronjob again by giving the following

```
crontab -e
```

this is what my cronjob looks like when given the command cronjob -l

```
58 06 * * * DISPLAY=:0 /usr/bin/audacious /home/administrator/Music/tc/AntarMan.mp3

```

But nothing happens.


what its basically supposed to do is to play the music at 6:58 am everyday.
Any help on this would be highly appreciated.

---

### Post by GoCool on 2008-04-24
This is how my /var/log/syslog looks like

> Apr 24 11:17:01 sound-room /USR/SBIN/CRON[31804]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 24 11:25:27 sound-room crontab[31867]: (user) LIST (user)
Apr 24 11:25:33 sound-room crontab[31869]: (user) BEGIN EDIT (user)
Apr 24 11:26:19 sound-room crontab[31869]: (user) REPLACE (user)
Apr 24 11:26:19 sound-room crontab[31869]: (user) END EDIT (user)
Apr 24 11:27:01 sound-room /USR/SBIN/CRON[31877]: (user) CMD (DISPLAY=:0 /usr/bin/audacious /home/administrator/Music/tc/AntarMan.mp3)
Apr 24 11:27:06 sound-room crontab[31880]: (user) LIST (user)


If you notice I have asked it to play at 11:27 am but nothing happens.

---

### Post by GoCool on 2008-04-24
:lolflag:

After 3 hours of struggle, I figured it out. It's the username which is causing it. I had changed my display name to something else and this caused the issue. Now when I have my username and display name as the same it works. But it beats me, why it would do such a thing, seems weird.:(

Not sure if its a feature or a bug.

I want to put the thread in resolve status, but if any one has any logical explanation for it, I would love to hear. :guitar:

---

### Post by aimpau on 2008-04-26
Can you check in the last page in here and tell me more about this cron?
[http://ubuntuforums.org/showthread.php?t=762507&highlight=irritating+lock](http://ubuntuforums.org/showthread.php?t=762507&highlight=irritating+lock)

---

