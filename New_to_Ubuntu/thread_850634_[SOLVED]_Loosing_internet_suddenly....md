---
title: "[SOLVED] Loosing internet suddenly..."
date: 2008-07-05
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-07-05
I'm using a Dynamode wireless USB dongle via Ndiswrapper to connect to my Orange broadband router (made by Inventel) and it has been working flawlessly on hardy heron since it's release, but over the past two weeks  (or there abouts) I've been having this problem were all the currently loading web pages wont load and my downloads will stop and then maybe 3-4min later it will all work again or if i manually disconnect and then reconnect it will work this happens sometimes regularly and other times it may only happen once every couple of hours:confused:

I hope someone can help me with this problem it's so agitating:mad:

---

### Post by f37u5g0d on 2008-07-05
I am not sure how to fix it but try to ping larger and larger packet sizes to something like yahoo.  I once had a problem with ndiswrapper similar to yours and it was caused by ndiswrapper trying to send large packets (like above 1500).

---

### Post by kamitsukai on 2008-07-06
> **f37u5g0d said:**
> I am not sure how to fix it but try to ping larger and larger packet sizes to something like yahoo.  I once had a problem with ndiswrapper similar to yours and it was caused by ndiswrapper trying to send large packets (like above 1500).

This probably sounds incredibly noobish but how would i ping a packet?

---

### Post by bab1 on 2008-07-06
The command is:```
ping -s somepacketsize
```

See the man page:```
man ping
```

---

### Post by bab1 on 2008-07-06
The long story is:  Your packet size is important.  If a router anywhere along the line won't accept the packet size YOU are sending it will drop it.  The specifics to curing this are many and varied.  It is up to your settings.  Most NIC's are set under the max so there is no problem.

Try starting at 1200 MTU

---

### Post by kamitsukai on 2008-07-06
Sorry about this im still a little confused..so i need to type the command

```
ping -s 1200
```

into the terminal? and at what unit should i go up by?

---

### Post by bab1 on 2008-07-06
yes

---

### Post by kamitsukai on 2008-07-06
and at what unit should i go up by?

---

### Post by bab1 on 2008-07-06
You will not be able to go past 1500.  So start at 1600.  The way to stop the command is cntl-c

---

### Post by bab1 on 2008-07-06
the complete command is:```
ping -s 1600 yahoo.com
```

---

### Post by kamitsukai on 2008-07-06
another noobish question what do i do when i get this?

```
dreamsofubuntu@dreamsofubuntu-desktop:~$ ping -s 1600
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination

```

---

### Post by bab1 on 2008-07-06
see at the bottom of page one.  I explained the command on the other page.  Sorry I missed this response for a bit

The answer to this question is; you did not tell ping where to ping to.  should be: ```
ping -s 1600 yahoo.com
```

---

### Post by kamitsukai on 2008-07-06
lol thanks my fault for being an idiot :P OK this is what I'm getting

```

PING yahoo.com (68.180.206.184) 1600(1628) bytes of data.
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=1 ttl=50 time=599 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=2 ttl=50 time=628 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=3 ttl=50 time=711 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=4 ttl=50 time=718 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=5 ttl=50 time=686 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=6 ttl=50 time=321 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=7 ttl=50 time=804 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=8 ttl=50 time=609 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=9 ttl=50 time=485 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=10 ttl=50 time=503 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=11 ttl=50 time=551 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=12 ttl=50 time=503 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=13 ttl=50 time=432 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=14 ttl=50 time=443 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=15 ttl=50 time=500 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=16 ttl=50 time=439 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=17 ttl=50 time=765 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=18 ttl=50 time=329 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=19 ttl=50 time=372 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=20 ttl=50 time=451 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=21 ttl=50 time=420 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=23 ttl=50 time=434 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=24 ttl=50 time=488 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=25 ttl=50 time=486 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=26 ttl=50 time=428 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=27 ttl=50 time=716 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=28 ttl=50 time=405 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=29 ttl=50 time=436 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=30 ttl=50 time=491 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=31 ttl=50 time=640 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=32 ttl=50 time=537 ms
1608 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=33 ttl=50 time=569 ms

```

---

### Post by bab1 on 2008-07-06
try 1700

no need for more than 4 packets.  :D

---

### Post by kamitsukai on 2008-07-06
```
dreamsofubuntu@dreamsofubuntu-desktop:~$ ping -s 1700 yahoo.com
PING yahoo.com (68.180.206.184) 1700(1728) bytes of data.
1708 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=1 ttl=50 time=320 ms
1708 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=2 ttl=50 time=323 ms
1708 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=3 ttl=50 time=319 ms
1708 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=4 ttl=50 time=501 ms

```

thanks for helping:)

---

### Post by bab1 on 2008-07-06
Well now, this is wrong.  You should NOT be able to transmit MORE than 1500.

Ethernet spec's state the MTU (max transmissible units) is 1500.  My pings are stopped at 1500.  I can't ping above that.  You need to have someone go over the settings for your ndis driver.  I don't know anything about that.  I can tell you that this is the problem though.


I need to get some sleep.  The British GP is this morning and I want to watch it on the TV,

Good luck

---

### Post by kamitsukai on 2008-07-06
thanks :D

---

### Post by kamitsukai on 2008-07-06
Hmmmm it also appears reinstalling does nothing :|

---

### Post by kamitsukai on 2008-07-19
Fixed through Private messages Turns out that my wirlesss network adapter was on the way out and it also appears that either one or more of my ADSL filters is damaged...

---

