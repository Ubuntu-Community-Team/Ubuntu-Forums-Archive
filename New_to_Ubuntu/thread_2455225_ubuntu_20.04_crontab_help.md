---
title: "ubuntu 20.04 crontab help"
date: 2020-12-15
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-15
can this be done.  just as an example
if the name of my script is /hhj/ray/home and i have it set to run at a certain time is there at terminal command i could run that would output at what time the job finished /tks

---

### Post by rburkartjo on 2020-12-15
would there be an option using pstree to give me that output

---

### Post by rburkartjo on 2020-12-15
or could i do this
[https://www.techrepublic.com/article/how-to-enable-logging-for-cron-on-linux/](https://www.techrepublic.com/article/how-to-enable-logging-for-cron-on-linux/)

---

### Post by norobro on 2020-12-15
From man cron:> [COLOR=#181818][FONT=monospace]When executing [/FONT][/COLOR][COLOR=#181818][FONT=monospace]commands, any output is mailed to the owner of the crontab (or to the [/FONT][/COLOR][COLOR=#181818][FONT=monospace]user specified in the [/FONT][/COLOR]*MAILTO environment variable in the crontab, if **such exists).*So if you put an echo or printf statement at the end of your script, cron will send a local mail when the script finishes.```
echo "job finished @$(date +'%T')"
```

---

### Post by ActionParsnip on 2020-12-15
I'd use
```

echo "job finished @$(date +'%T')" >> /var/log/scriptname.log

```
or similar. You can have your own log for your own scripts :)

You can also use logger as below
[https://www.howtogeek.com/117878/how-to-view-write-to-system-log-files-on-ubuntu/](https://www.howtogeek.com/117878/how-to-view-write-to-system-log-files-on-ubuntu/)

---

### Post by rburkartjo on 2020-12-15
tks act followed your advise

---

