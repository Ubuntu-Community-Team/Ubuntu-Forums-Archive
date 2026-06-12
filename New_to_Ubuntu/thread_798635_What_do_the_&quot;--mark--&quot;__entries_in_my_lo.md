---
title: "What do the &quot;--mark--&quot;  entries in my logfiles mean?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by hovzio on 2008-05-18
For the last day I've seen this entry in various log files. 

May 18 15:40:50 $USER -- MARK --

Can anyone tell me what these "marks" are all about?
I've googled and searched Ubuntu forums but havent found anything. I'm rather new to ubuntu so I apologize if the log entry is irrelevant.I happened to notice that its only been taking place for the last 20 hours or so. Appreciate any info.

---

### Post by Monicker on 2008-05-18
That is just the default timestamp marker.  It should be occurring every 20 minutes.  Its normal and doesn't hurt anything.  You can turn it off if you want, thoughI'd have to check on the details for disabling it.

---

### Post by hovzio on 2008-05-18
Thanks, I guess theres no need to disable them. I was just curious because I've only seen them in recent logs. I assume they are removed??

---

### Post by Monicker on 2008-05-18
They system log files are rotated on a regular basis; eventually that particular log file will be removed from the system.

---

### Post by brian_p on 2008-05-18
> **hovzio said:**
> For the last day I've seen this entry in various log files. 

May 18 15:40:50 $USER -- MARK --

Can anyone tell me what these "marks" are all about?
I've googled and searched Ubuntu forums but havent found anything. I'm rather new to ubuntu so I apologize if the log entry irrelevant.I happened to notice that its only been taking place for the last 20 hours or so. Appreciate any info.

They let you know syslog is still working. Or when it stopped working, for example if your computer crashed.

```
man syslogd
```

and the -m option.

---

### Post by hovzio on 2008-05-18
Nautilus was getting hung up and I had to killall nautilus. I was also in suspend mode a couple times today; maybe something had problems restarting?? I've had yet to experience any system crashes. ;) (Only on rare occasions nautilus acts up.)

Thanks for the help, I'll read up on syslogd.

---

