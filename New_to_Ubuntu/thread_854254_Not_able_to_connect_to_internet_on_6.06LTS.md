---
title: "Not able to connect to internet on 6.06LTS"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by waterrr on 2008-07-09
Hi,
I installed the Ubuntu 6.06LTS server and am not able to connect to the internet or ping anything in the terminal...please help

---

### Post by Seisen on 2008-07-09
Please post the results of ```
lspci 
``` in the terminal.

---

### Post by waterrr on 2008-07-09
I'm running this from another laptop so I'm not able to copy n paste the results because it's extremely long, is there another method that where I'm able to type the results to you?

---

### Post by waterrr on 2008-07-09
im going to reinstall everything, ill post an update

---

### Post by waterrr on 2008-07-09
i reinstalled and it's able to ping, but it wont stop pinging...it keeps repeating the information (or continuously pinging)

---

### Post by lazyart on 2008-07-09
Control-C to stop the pinging.

I'd have suggested that if you're going to reinstall, go with a more current version (7.10 or 8.04).

---

### Post by Canis familiaris on 2008-07-09
> **waterrr said:**
> i reinstalled and it's able to ping, but it wont stop pinging...it keeps repeating the information (or continuously pinging)
Isn't repitition of pinging infinitely normal?

EDIT: Yes it is.

You could press Ctrl + C to  end the pings

You will get an output like this:
```
PING yahoo.com (206.190.60.37) 56(84) bytes of data.
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=1 ttl=54 time=318 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=2 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=3 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=4 ttl=54 time=320 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=5 ttl=54 time=320 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=6 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=7 ttl=54 time=320 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=8 ttl=54 time=321 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=9 ttl=54 time=321 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=10 ttl=54 time=321 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=11 ttl=54 time=321 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=12 ttl=54 time=321 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=13 ttl=54 time=321 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=14 ttl=54 time=320 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=15 ttl=54 time=321 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=16 ttl=54 time=320 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=17 ttl=54 time=321 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=18 ttl=54 time=321 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=19 ttl=54 time=322 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=20 ttl=54 time=322 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=21 ttl=54 time=323 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=22 ttl=54 time=323 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=23 ttl=54 time=323 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=24 ttl=54 time=324 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=25 ttl=54 time=318 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=26 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=27 ttl=54 time=318 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=28 ttl=54 time=318 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=29 ttl=54 time=318 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=30 ttl=54 time=317 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=31 ttl=54 time=317 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=32 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=33 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=34 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=35 ttl=54 time=318 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=36 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=37 ttl=54 time=318 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=38 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=39 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=40 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=41 ttl=54 time=318 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=42 ttl=54 time=318 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=43 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=44 ttl=54 time=319 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=45 ttl=54 time=320 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=46 ttl=54 time=320 ms
64 bytes from w2.rc.vip.re4.yahoo.com (206.190.60.37): icmp_seq=47 ttl=54 time=320 ms

--- yahoo.com ping statistics ---
47 packets transmitted, 47 received, 0% packet loss, time 46011ms
rtt min/avg/max/mdev = 317.846/320.230/324.002/1.618 ms

```
Look at the last line in a similar ping and check How many packets are transmitted and recieved. If packet loss is in single digit figures, then the internet is working.

---

