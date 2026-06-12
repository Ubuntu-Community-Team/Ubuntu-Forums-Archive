---
title: "crontab dont wokr when line include \;"
date: 2012-10-27
forum: Programming Talk
---

### Post by mafi127 on 2012-10-27
Hei. I have problem whit crontab. I have set this script to be executed every two hours.

```
find /media/-Arhiiv-/0day/2012/ -maxdepth 2 -mindepth 2 -type d -mtime -7 -not -name Sorted -exec cp -r {} /home/tamps/Dropbox/Hardcore/$(/bin/date '+%B') \;
```

When I run this manualy everything works perfect but when I add this line to crontab. 

```
0 0-23/2 * * * find /media/-Arhiiv-/0day/2012/ -maxdepth 2 -mindepth 2 -type d -mtime -7 -not -name Sorted -exec cp -r {} /home/tamps/Dropbox/Hardcore/$(/bin/date '+%B') \;
```

Then it dosent work. I checked syslog and theres this line

```
Oct 27 18:00:01 mafia CRON[4511]: (tamps) CMD (find /media/-Arhiiv-/0day/2012/ -maxdepth 2 -mindepth 2 -type d -mtime -7 -not -name Sorted -exec cp -r {} /home/tamps/Dropbox/Hardcore/$(/bin/date '+)
```

I notice that in the syslog there isent the last two characters "\;". How can I fix this problem whit crontab?

---

### Post by Vaphell on 2012-10-27
i don't see %B there either
can't you avoid the problem entirely by wrapping that command in a script and calling it?

---

### Post by spjackson on 2012-10-27
The % symbol has special meaning in a crontab entry. You need to escape it like this:
```

date '+\%B'

```
See "man 5 crontab" for details.

---

### Post by mafi127 on 2012-10-28
thank you, made little bash script and now its working fine :)

---

