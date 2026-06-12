---
title: "change NTP server time ,force clients to update times"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by sajjadbaeidi on 2012-11-04
Hello ,
I set up a ntp server on ubuntu server 12.04 .
It's work fine , but now i need that every time that i change the time on my ntp server , all my clients update their times automatically .
which config on server (ntp.conf) or client cant solve my problem .
thx alot.

---

### Post by Lars Noodén on 2012-11-04
NTP will by default only make very, very small changes in the time.  So if there is an adjustment, it will be made in small increments and it can take a very long time to catch up.

From what I recall, the normal behavior of ntp is to exit if the time difference is too big.  So if you make a really big time change on your time server, the next tier down will have to stop ntpd, run ntpdate-debian, then start the ntpd server.

---

### Post by sajjadbaeidi on 2012-11-04
Ok , its true , but i need to change my ntp server time and this server force client to change their time , i mean i change my ntp server time and dont change client out of periodic cron list .
because my ntp clients my have wrong time , i need to change my ntp server to change all clients .
in other way i set crontab list daily but maybe i need to change my time during day .
help me to just change my ntp server time and i sure that all of my clients are sync with server .

---

### Post by Lars Noodén on 2012-11-04
Well, to set the time, one way is like this:

```

sudo service ntp stop
sudo /usr/sbin/ntpdate-debian
sudo service ntp start

```

Can you do that on your timeserver?  I assume it is also running Ubuntu.

---

### Post by sajjadbaeidi on 2012-11-04
I know that but i neet change ntp server time maximum 1 or 2 hours and don't change the clients times.
i want change all times in my network just with change ntp server time.

---

### Post by Lars Noodén on 2012-11-04
Then you'll have to make the changes to the time server's time in very small increments and just let the next level down catch up slowly.  You can't do it in a big jump because [ntp quits if the interval is too big](http://manpages.ubuntu.com/manpages/precise/en/man8/ntpd.8.html):

> -g     Normally,  ntpd  exits  with  a message to the system log if the offset exceeds the panic threshold, which is 1000 s by  default...


That's just how ntpd works.  The other option is to manually intervene on the next level down.

---

### Post by sajjadbaeidi on 2012-11-04
simple question .
i want to set ntp server time then ntp server force client time to sync with itself.
**ntp server change all client's time .**

---

### Post by Zill on 2012-11-04
> **sajjadbaeidi said:**
> I know that but i neet change ntp server time maximum 1 or 2 hours and don't change the clients times.
i want change all times in my network just with change ntp server time.
I am not sure you *can* change ntp server time.  The NTP server should automatically maintain Coordinated Universal Time (UTC).

See ["Network Time Protocol"]("http://en.wikipedia.org/wiki/Network_Time_Protocol#Overview")

---

### Post by Lars Noodén on 2012-11-05
If you change the time on the time server, the clients pointed at it will sync to it.  However, if you change the time on the time server too much, the clients will die unless they were started with the option -g.  

What might work is to start the time server's ntp with -g and point it at a time server with the desired time.  However, if the time difference is large it cant take hours or days to sync fully.

---

