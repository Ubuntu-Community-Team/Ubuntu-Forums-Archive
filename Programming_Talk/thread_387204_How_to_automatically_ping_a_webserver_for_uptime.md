---
title: "How to automatically *ping* a webserver for uptime?"
date: 2007-03-18
forum: Programming Talk
---

### Post by jammodotnet on 2007-03-18
Today in my RSS feeds, I came across this post:
Track your web host’s uptime
[http://www.randomn3ss.com/2007/03/10/track-your-web-host%e2%80%99s-uptime/](http://www.randomn3ss.com/2007/03/10/track-your-web-host%e2%80%99s-uptime/)

Makes me wonder ... wouldn't it be a simple method to use cron *(i think)* + some script to check my websites?

<< i am no coder/programmer, with the exception of XHTML and CSS >>

Am just looking for a few ideas on how this could be done in a simple way?

---

### Post by lloyd_b on 2007-03-18
Idea:  Use "wget" to attempt to fetch a particular file (index.html?) from that site.  Then test to see if the fetch succeeded:
```
#!/bin/bash
TIMESTAMP=`date`
cd /home/me/webtest
wget www.mysite.com/index.html
if test -f index.html; then
    echo "Website available: $TIMESTAMP" >> website.log
    rm index.html
else
    echo "Website down: $TIMESTAMP" >> website.log
fi 
```

Set this up as a cron job, running every N minutes.  You'll wind up with a nice log file in "/home/me/website/website.log", with a list of success/fail messages and the corresponding timestamps.

On the failed side, you could potentially have it running another script to notify you that the site is down (send an email, play a warning sound, etc).

Lloyd B.

---

