---
title: "Wrong timezone"
date: 2016-03-21
forum: New to Ubuntu
---

### Post by ScorpioTiger on 2016-03-21
Hi,

I've configured the timezone on my server using 
dpkg-reconfigure tzdata and setting the timezone to Europe/London, yet when I check the time and timezone using timedatectl I'm getting the timezone as America/New_York. 

I've tried several times and it's always wrong. I've checked some other servers that I have and they correctly display "Europe/London". Output from my terminal window as follows;

```

root@myserver:/# dpkg-reconfigure tzdata
Current default time zone: 'Europe/London'
Local time is now: Mon Mar 21 11:33:35 GMT 2016.
Universal Time is now: Mon Mar 21 11:33:35 UTC 2016.
```

```

root@myserver:/# timedatectl
      Local time: Mon 2016-03-21 11:33:45 GMT
  Universal time: Mon 2016-03-21 11:33:45 UTC
        RTC time: Mon 2016-03-21 11:33:44
        Timezone: America/New_York (GMT, +0000)
     NTP enabled: yes
NTP synchronized: yes
 RTC in local TZ: no
      DST active: no
 Last DST change: DST ended at 
                  Sun 2015-10-25 01:59:59 BST
                  Sun 2015-10-25 01:00:00 GMT
 Next DST change: DST begins (the clock jumps one hour forward) at
                  Sun 2016-03-27 00:59:59 GMT
                  Sun 2016-03-27 02:00:00 BST

```

Ok. Something is screwed up on the site. It's completely destroyed my post. Basically I want to know why I get a different timezone displayed using timedatectl to the one I set using dpkg-reconfigure tzdata.

---

### Post by fantab on 2016-03-21
Is there another OS, like Windows, in the picture?

---

### Post by ScorpioTiger on 2016-03-23
> **fantab said:**
> Is there another OS, like Windows, in the picture?

No. This is an Ubuntu 14.04 VPS. I've actually had the problem appear on a couple of servers now.

---

