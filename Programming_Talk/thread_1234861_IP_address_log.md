---
title: "IP address log"
date: 2009-08-08
forum: Programming Talk
---

### Post by rohitvk on 2009-08-08
Hi,

I want to keep a log of IP address. I have created a bash file with following code

dig +short myip.opendns.com @208.67.222.222 @208.67.220.220 |cat >> IP_LOG.txt
date | cat >> IP_LOG.txt

now its working fine. but i want it to run this file periodically and update the log only if ip gets changed.
I tried using a if structure..but the o/p of dig... is not getting saved in a variable
can someone help me with that?

---

### Post by PaulFr on 2009-08-12
Something like ```
#!/bin/sh

ipfile=$HOME/ip_addresses
lastip="0.0.0.0"
if [ -f "$ipfile" ]; then
    lastip=`tail -1 $ipfile`
fi

curip=`dig +short myip.opendns.com @208.67.222.222 @208.67.220.220`
if [ "$curip" != "$lastip" ]; then
    date >> $ipfile
    echo "$curip" >> $ipfile
fi
exit 0
``` works for me. Learn about **_[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)_** or alternatives to find out how you can run this periodically (if you did not know this already).

---

### Post by rohitvk on 2009-08-12
[B]@ PaulFr
[/B]
Thanks man. It worked perfectly.  :P

Also, I want ubuntu to start from hibernate mode at a specified time... coz my broadband plan has weird night hours for unlimited usage. So what I used to do in windows is, put it on hibernate mode while going to sleep, and it would automatically switch-on at 2am..
Is there any way to do the same in Ubuntu? (This would help me a LOT. I am practically using the XP only for this purpose right now! IF I can get this sorted out, I can switch to almost fully Ubuntu)

---

### Post by PaulFr on 2009-08-12
Did you see the thread in **_[http://ubuntuforums.org/showthread.php?t=938533](http://ubuntuforums.org/showthread.php?t=938533)_** (rtcwake) ?

---

### Post by rohitvk on 2009-08-12
> **PaulFr said:**
> Did you see the thread in **_[http://ubuntuforums.org/showthread.php?t=938533](http://ubuntuforums.org/showthread.php?t=938533)_** (rtcwake) ?
 
Thanks

---

