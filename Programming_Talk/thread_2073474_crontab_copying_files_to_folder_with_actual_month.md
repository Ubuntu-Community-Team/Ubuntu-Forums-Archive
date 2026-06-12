---
title: "crontab copying files to folder with actual month"
date: 2012-10-19
forum: Programming Talk
---

### Post by mafi127 on 2012-10-19
Hello.

I need to make a script to crontab what check one folder and copy to another but I  want that a file what will be copyed will be copyed to folder what is named to current month.

right now I'm using this crontab script 

```
find /media/-Arhiiv-/0day/2012/ -maxdepth 2 -mindepth 2 -type d -mtime -7 -exec cp -r {} /home/user/Dropbox/Share/ \;
```

but what i want to make is to use python code like

```
/home/user/Dropbox/Share/{{ now|formatdate('%Y/%m - %B')}}/
```

how can I make it work in crontab?

---

### Post by steeldriver on 2012-10-19
not a crontab expert but have you tried formatting the /bin/date command directly - something like this maybe?

```
/home/user/Dropbox/Share/$(/bin/date '+%B')
```

---

### Post by mafi127 on 2012-10-21
Thank you, that made the trick :)

---

