---
title: "How can I check how accurately the time is synchronized on my Ubuntu 16.04?"
date: 2018-12-24
forum: New to Ubuntu
---

### Post by dmitriano on 2018-12-24
How can I check how accurately the time is synchronized on my Ubuntu 16.04?

I tried  

```
 timedatectl timesync-status
```

but got 'Unknown operation timesync-status' on both 16.04 and 18.04.

The synchronization is enabled:

```
timedatectl status
```
```
      Local time: Mon 2018-12-24 15:14:35 MSK
  Universal time: Mon 2018-12-24 12:14:35 UTC
        RTC time: Mon 2018-12-24 12:14:35
       Time zone: Europe/Moscow (MSK, +0300)
 Network time on: yes
NTP synchronized: yes
 RTC in local TZ: no

```

But it is not clear what is the precision (the difference between local time and the server time) that 'time.is' website can show, for example (but do this from the command line).

also I tried 

```

systemctl status systemd-timesyncd.service
&#9679; systemd-timesyncd.service - Network Time Synchronization
   Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/systemd-timesyncd.service.d
           &#9492;&#9472;disable-with-time-daemon.conf
   Active: active (running) since Mon 2018-11-19 00:45:00 MSK; 1 months 5 days ago
     Docs: man:systemd-timesyncd.service(8)
 Main PID: 538 (systemd-timesyn)
   Status: "Synchronized to time server [2001:67c:1560:8003::c7]:123 (ntp.ubuntu.com)."
    Tasks: 2
   Memory: 896.0K
      CPU: 5.943s
   CGroup: /system.slice/systemd-timesyncd.service
           &#9492;&#9472;538 /lib/systemd/systemd-timesyncd

```

but there is no some useful information.

And, I am not sure, should I open port 123 (do 'ufw allow ntp')?

---

### Post by SeijiSensei on 2018-12-24
If you're synchronized to an NTP server, that's all you need.  

You don't need to allow inbound NTP unless you're using your server as a local NTP host.  I have one machine on my network that syncs with public NTP servers; the other computers on my network sync with that local server.

If you need microsecond or better resolution, you need to read up on [NTP]("https://linux.die.net/man/8/ntpd").

---

### Post by dmitriano on 2018-12-27
I have 'timesyncd' but not 'ntpd' and there is no /etc/ntp.conf on my machine, should I install 'ntpd'? Is it better?

---

### Post by oldrocker99 on 2018-12-27
Personally, I have found the clock to be very accurate, down to the second, which I always display on my desktop. It is updated often, and I consider it to be trustworthy.

---

### Post by dmitriano on 2018-12-27
I was able to [check the sync accuracy with chrony]("https://developernote.com/2018/12/setting-up-time-synchronization-on-ubuntu/").

---

### Post by SeijiSensei on 2018-12-28
[https://unix.stackexchange.com/questions/305643/ntpd-vs-systemd-timesyncd-how-to-achieve-reliable-ntp-syncing](https://unix.stackexchange.com/questions/305643/ntpd-vs-systemd-timesyncd-how-to-achieve-reliable-ntp-syncing)

---

