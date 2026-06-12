---
title: "Periodic running of ntpdate"
date: 2012-11-20
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-11-20
Hi all

several times a day (when I remember..) I run the following in terminal:
```

glenn@design:~$ sudo ntpdate 2.nz.pool.ntp.org
[sudo] password for glenn: 
21 Nov 04:01:18 ntpdate[4084]: step time server 119.47.118.129 offset 91.031078 sec
glenn@design:~$ 

```Is there an easy way that I can automate that process so it runs every 6 hours or so?

I know nothing. nothing.

Glenn

---

### Post by Tony Flury on 2012-11-20
> **Senior_Buckethead said:**
> Hi all

several times a day (when I remember..) I run the following in terminal:
```

glenn@design:~$ sudo ntpdate 2.nz.pool.ntp.org
[sudo] password for glenn: 
21 Nov 04:01:18 ntpdate[4084]: step time server 119.47.118.129 offset 91.031078 sec
glenn@design:~$ 

```Is there an easy way that I can automate that process so it runs every 6 hours or so?

I know nothing. nothing.

Glenn

I would suggest that this is the wrong thing to do - what you really need is to get the ntp deamon running on your pc so that it keeps your machine in step, and should also prevent any nasty step changes which could throw some pograms off.

[https://help.ubuntu.com/12.04/serverguide/NTP.html](https://help.ubuntu.com/12.04/serverguide/NTP.html) - see the section on ntpd.

---

### Post by Zill on 2012-11-20
> **Tony Flury said:**
> I would suggest that this is the wrong thing to do - what you really need is to get the ntp deamon running on your pc so that it keeps your machine in step, and should also prevent any nasty step changes which could throw some pograms off.

[https://help.ubuntu.com/12.04/serverguide/NTP.html](https://help.ubuntu.com/12.04/serverguide/NTP.html) - see the section on ntpd.
+1

NTP/ntpd is the way to go to keep your PC always synchronised.  Just install, configure and then forget all about it. ;-)

---

### Post by Senior_Buckethead on 2012-11-21
Ok, have installed ntp. 
now run
```
glenn@design:/etc$ sudo ntpq -p
```and got:
```

glenn@design:/etc$ sudo ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
+kgb.comnet.bg     209.81.9.7           2 u   25   64  377  383.758  1259.15 689.834
+89.149.57.26          128.10.254.7       2 u   16   64  377  395.395  1276.78 700.364
+prrr.se                     192.36.144.22     2 u   12   64  377  338.570  1279.76 706.608
*205-196-146-72.    209.51.161.238  2 u   34   64  377  227.348  1230.83 683.339
+europium.canoni 193.79.237.14     2 u   31   64  377   377.648  1236.90 688.264
glenn@design:/etc$ 

```Nay of those bad? Some look sus. If so, how do I remove them?

The time servers i have used are:
[B]server msltime1.irl.cri.nz
[/B]**server msltime2.irl.cri.nz**

webpage: [http://msl.irl.cri.nz/services/time-and-frequency/ntp-server-information](http://msl.irl.cri.nz/services/time-and-frequency/ntp-server-information)
Glenn.

---

### Post by Zill on 2012-11-21
Senior_Buckethead:  AIUI, the longer NTP runs the more accurate the time becomes.  Your numbers (delay/offset/jitter etc) do seem quite a bit higher than mine and so it maybe that these will improve after a longer period of running.

However, although you appear to be based in NZ, I suggest you may get better results by using ["pool" servers]("http://support.ntp.org/bin/view/Servers/NTPPoolServers"), which automatically uses different servers in your area to even out load.

I would try editing /etc/ntp.conf and change your two servers for the following four servers:
```
server 0.pool.ntp.org
server 1.pool.ntp.org
server 2.pool.ntp.org
server 3.pool.ntp.org
```
Then restart ntpd:
```
sudo /etc/init.d/ntp reload
```
Enter "ntpq -p" and see what numbers you get.  Then try entering "ntpq -p" after a few hours and see if things get more accurate. (Note that this does *not* need the sudo prefix).

As a real "sanity check", check your PC time against an analogue radio time signal or a GPS/satnav receiver.  It should be spot-on. :-)

---

### Post by Senior_Buckethead on 2012-11-21
Cheers Zill.

---

