---
title: "Apache logs continue to change back to UTC [SOLVED]"
date: 2023-02-21
forum: New to Ubuntu
---

### Post by hanji866 on 2023-02-21
I'm new to Ubuntu, and this is an odd one for me.

I have my timezone set with
```
timedatectl set-timezone America/Denver
```

I also run this:
```
dpkg-reconfigure tzdata
```

When I restart apache2 it will show logs as MTC, but within a minute or so, will revert back to UTC

Current output of timedatectl
```
Local time: Tue 2023-02-21 15:14:05 MST
Universal time: Tue 2023-02-21 22:14:05 UTC
RTC time: Tue 2023-02-21 22:14:05
Time zone: America/Denver (MST, -0700)
System clock synchronized: yes
NTP service: active
RTC in local TZ: no
```

```
xxx.xxx.xxx.xxx - - [21/Feb/2023:15:14:17 -0700]....
xxx.xxx.xxx.xxx - - [21/Feb/2023:22:15:20 +0000]....
```

Maybe it's about the RTC in local TZ should be yes?

Thanks!
hanji

---

### Post by #&amp;thj^% on 2023-02-21
Without  getting into a long reasoning, The solution, in short, is to normalize your timezone settings. Ideally, use something like UTC for both server and applications.
EDIT: Mine:
```
timedatectl
               Local time: Tue 2023-02-21 15:19:12 MST
           Universal time: Tue 2023-02-21 22:19:12 UTC
                 RTC time: Tue 2023-02-21 22:19:12
                Time zone: America/Denver (MST, -0700)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: no

```

---

### Post by hanji866 on 2023-02-21
Thanks for reply. I guess, the point, is I don't want UTC, and trying to get everything on the system to be MTC

---

### Post by hanji866 on 2023-02-21
> **1fallen said:**
> Without  getting into a long reasoning, The solution, in short, is to normalize your timezone settings. Ideally, use something like UTC for both server and applications.
EDIT: Mine:
```
timedatectl
               Local time: Tue 2023-02-21 15:19:12 MST
           Universal time: Tue 2023-02-21 22:19:12 UTC
                 RTC time: Tue 2023-02-21 22:19:12
                Time zone: America/Denver (MST, -0700)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: no

```



That is basically what my output is. So, do I need to make a change on apache's side?

---

### Post by #&amp;thj^% on 2023-02-21
Also, you might check for SetEnv lines in the apache config.

Personally I think keeping logs in GMT is a good idea...

---

### Post by hanji866 on 2023-02-21
> **1fallen said:**
> Also, you might check for SetEnv lines in the apache config.

Personally I think keeping logs in GMT is a good idea...

I personally like to reference the time quickly - I don't think in UTC. Also, just to clarify, /var/log/messages are showing the correct time. My php.ini also is set to 'America/Denver'. I did a grep in /etc/apache for anything TZ/Timezone/UTC, etc.

Thanks for the help.
hanji

---

### Post by #&amp;thj^% on 2023-02-21
Remember that the TZ variable is global to the process.  If a *mod_perl*
or PHP script sets that variable, it will I think  affect logs written
out by Apache

---

### Post by TheFu on 2023-02-21
> **hanji866 said:**
> Thanks for reply. I guess, the point, is I don't want UTC, and trying to get everything on the system to be MTC

Unix computers are UTC. This is necessary for lots of reasons. It is just the display of the time which gets localized.  Don't try to fight it.  Just set your TZ environment variable to whatever you'd like to be displayed.  Then,
```
$ journalctl -S today
```
will show the correct times based on the TZ, as you want.  As for apache logs, you'll need to read the apache documentation for log formatting. [https://httpd.apache.org/docs/current/logs.html](https://httpd.apache.org/docs/current/logs.html) seems to spell out how to force the timezone of the system to be honor, but it isn't the default.

---

### Post by #&amp;thj^% on 2023-02-21
Or this:
```
TZ="America/Denver" date
Tue Feb 21 04:59:26 PM MST 2023


```
Sorry I forgot the OP is new here.
```
tcsh
me-82b5:~> date
Tue Feb 21 05:05:30 PM MST 2023
me-82b5:~> 

```
```
timedatectl
               Local time: Tue 2023-02-21 17:18:33 MST
           Universal time: Wed 2023-02-22 00:18:33 UTC
                 RTC time: Tue 2023-02-21 17:18:34
                Time zone: America/Denver (MST, -0700)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: yes

Warning: The system is configured to read the RTC time in the local time zone.
         This mode cannot be fully supported. It will create various problems
         with time zone changes and daylight saving time adjustments. The RTC
         time is never updated, it relies on external facilities to maintain it.
         If at all possible, use RTC in UTC by calling
         'timedatectl set-local-rtc 0'.

```

---

### Post by hanji866 on 2023-02-21
Okay.. I found the issue. I'm running apache in a chroot. I copied /etc/localtime before I set up the timezone. So it was reading that. Removing that file and copying a fresh version fixed.

Thanks again for all the help and suggestions!
hanji

---

