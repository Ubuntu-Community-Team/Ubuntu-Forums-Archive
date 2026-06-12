---
title: "how to create new folder with date stamp from crontab ?"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by V4705 on 2013-02-25
Hi,
I'm trying to make an archive of a folder so I wrote in crontab:
1 0 * * * mkdir /path/$(date +%F)
2 0 * * * cp -ur /path/to/source/* /path/$(date +%F)/

But I guess the variable "$(date +%F)" can't be used in cronjobs because it doesn't even create the folder...

Is there a way to do what I'm looking for without a script, just with crontab ?

Many thanks!

---

### Post by thermion on 2013-02-25
When do you want all this to happen?
Right now, it should create a folder at 00:01 and copy some files at 00:02.

Is that really what you want to do?

---

### Post by V4705 on 2013-02-25
Yes.
The problem is probably not the time, command or path because it's working without the time variable, the question is how do I make it automatically make a new folder each day and not overwrite the files from previous run.

Thanks (:

---

### Post by steeldriver on 2013-02-25
The problem may be the % character - it has special meaning in cron - I would try escaping it

```
$(date +**\**%F)
```FWIW I usually single-quote date formats as well, i.e.

```
$(date '+\%F')
```

---

### Post by V4705 on 2013-02-25
Thanks! adding \ fixed the issue :)

BTW, the error I got before in syslog was: info (No MTA installed, discarding output).

---

