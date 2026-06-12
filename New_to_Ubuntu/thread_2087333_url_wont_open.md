---
title: "url wont open"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by parth4992 on 2012-11-23
there is a particular url that i am unable to open in ubuntu which works perfectly fine for windows(firefox).i have tried opening it in firefox and chrome in ubuntu.

```
animekens-.chatango.com
```
since i am able to load other chatrooms of same type, i doubt that it is due to flash plugin.

---

### Post by Wim Sturkenboom on 2012-11-23
I guess that the dash after animekens is the problem. That site does not exist.

```

wim@i3-2120:~$ ping animekens-.chatango.com
**[COLOR="Red"]ping: unknown host animekens-.chatango.com[/COLOR]**
wim@i3-2120:~$ ping animekens.chatango.com
PING animekens.chatango.com (64.127.108.174) 56(84) bytes of data.
64 bytes from 64.127.108.174: icmp_req=1 ttl=41 time=379 ms
64 bytes from 64.127.108.174: icmp_req=2 ttl=41 time=411 ms
^C64 bytes from 64.127.108.174: icmp_req=3 ttl=41 time=411 ms

--- animekens.chatango.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 11432ms
rtt min/avg/max/mdev = 379.105/400.644/411.581/15.248 ms
wim@i3-2120:~$

```

---

### Post by SlugSlug on 2012-11-23
diffrent story from my windows box..


```
ping animekens-.chatango.com

Pinging animekens-.chatango.com [72.172.224.100] with 32 bytes of data:
Reply from 72.172.224.100: bytes=32 time=183ms TTL=44
Reply from 72.172.224.100: bytes=32 time=182ms TTL=44


--

ping animekens.chatango.com

Pinging animekens.chatango.com [72.172.232.83] with 32 bytes of data:
Reply from 72.172.232.83: bytes=32 time=182ms TTL=44
Reply from 72.172.232.83: bytes=32 time=183ms TTL=44
```

---

### Post by Wim Sturkenboom on 2012-11-23
OK, point taken ;)

```

C:\Users\Wim>ping animekens-.chatango.com

Pinging animekens-.chatango.com [72.172.224.100] with 32 bytes of data:
Reply from 72.172.224.100: bytes=32 time=674ms TTL=41
Reply from 72.172.224.100: bytes=32 time=769ms TTL=41
Reply from 72.172.224.100: bytes=32 time=665ms TTL=41
Reply from 72.172.224.100: bytes=32 time=582ms TTL=41

Ping statistics for 72.172.224.100:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 582ms, Maximum = 769ms, Average = 672ms

C:\Users\Wim>ping animekens.chatango.com

Pinging animekens.chatango.com [72.172.224.100] with 32 bytes of data:
Reply from 72.172.224.100: bytes=32 time=472ms TTL=41
Reply from 72.172.224.100: bytes=32 time=507ms TTL=41
Reply from 72.172.224.100: bytes=32 time=618ms TTL=41
Reply from 72.172.224.100: bytes=32 time=660ms TTL=41

Ping statistics for 72.172.224.100:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 472ms, Maximum = 660ms, Average = 564ms

C:\Users\Wim>

```

---

### Post by WebHamsteR on 2012-11-23
This is very interesting. It is not working due to linux is following RFC standards and windows does not.

RFC 1035 (Domain names - implementation and specification), which says: "The labels must follow the rules for ARPANET host names.  They must
start with a letter, end with a letter or digit, and have as interior
characters only letters, digits, and hyphen.  There are also some
restrictions on the length.  Labels must be 63 characters or less."
 It´s clear to me that "-whatever-.dot.com" is an illegal host  name and then it must not be resolved. The fact is that any application  that relies its name resolving in C´s "gethostbyname" calls (on Linux:  ping, dig, nslookup, and the like...) will fail with illegal host names. 


[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/121467](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/121467)

---

### Post by sandyd on 2012-11-23
try this
Open a terminal
run
```

sudo nano /etc/hosts
```
add to the bottom, on a new line
```

72.172.224.100 animekens-.chatango.com

```
purge cache, and retry.

Might want to whack dnsmasq a few times on the way out as well to make sure it doesn't cache the original erronous queries

---

