---
title: "using cron to run xvidcap"
date: 2009-02-04
forum: Programming Talk
---

### Post by slaroy on 2009-02-04
I have a little shell script that successfully runs xvidcap to grab the screen.

```
#!/bin/sh 
TODAY=$(date +%F) 
HOUR=$(date +%H) 
MINUTE=$(date +%M) 
#printf '%s--%s:%s' "$TODAY" "$HOUR" "$MINUTE" 
$(touch /home/telecom/Videos/Recorded/test.txt) 
$(mv /home/telecom/Videos/Recorded/* /home/telecom/Videos/Zipped/) 
$(gzip -f /home/telecom/Videos/Zipped/*) 
$(/usr/bin/xvidcap --audio no --mf --file /home/telecom/Videos/Recorded/$TODAY--$HOUR:$MINUTE.mpg --time 5 --cap_geometry=1024x768 --gui no --fps 29.97)  
wait 
```

This works just fine if I run it from the command line using ./capture.sh

If I try to run it using cron nothing seems to happen, and I can't find any error logs. Does anyone have any ideas of how I might get this might work? /etc/crontab is below.

Thanks!
Steve

```
# /etc/crontab: system-wide crontab 
# Unlike any other crontab you don't have to run the `crontab' 
# command to install the new version when you edit this file 
# and files in /etc/cron.d. These files also have username fields, 
# that none of the other crontabs do. 

SHELL=/bin/sh 
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/home/telecom/Videos 

# m h dom mon dow user  command 
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly 
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ) 
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly ) 
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly ) 
*/1 *   * * *   root    /home/telecom/Videos/capture.sh  
# 
```

---

### Post by johnl on 2009-02-04
I would check that $DISPLAY is set when running as part of a cronjob.  If it's not, xvidcap won't know what screen to capture.

---

### Post by slaroy on 2009-02-04
> **johnl said:**
> I would check that $DISPLAY is set when running as part of a cronjob.  If it's not, xvidcap won't know what screen to capture.

That solved it. I added the following line to /etc/crontab, and it worked. Thanks!

```

DISPLAY=:0.0

```

---

