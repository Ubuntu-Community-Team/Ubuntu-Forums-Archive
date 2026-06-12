---
title: "Firefox Issues"
date: 2014-06-24
forum: New to Ubuntu
---

### Post by marcellk98 on 2014-06-24
Recently I got Ubuntu 12.04 LTS and I have had one really big problem. Although my computer is connected to the internet, Firefox does not work at all. Whenever I open Firefox two things either occur. The first is that firefox begins to try and load whatever url I've put in like google for example and it keeps trying to load this page forever. Second scenario is that I will open firefox and immediately it will appear "Server not Found". Please help if you can.

---

### Post by texpat on 2014-06-24
Hi there,

by "connected to the Internet" you probably mean that your computer is hooked up to a router o modem that in turn is connected to a phone socket in the wall. That doesn't necessarily mean that you are actually online.

Can you bring up a terminal and type:
```
ping -c5 www.google.com
```

only if you get an output such as:
```
PING www.google.com (173.194.41.16) 56(84) bytes of data.
64 bytes from www.google.com (173.194.41.16): icmp_seq=1 ttl=55 time=65.4 ms
64 bytes from www.google.com (173.194.41.16): icmp_seq=2 ttl=55 time=65.7 ms
64 bytes from www.google.com (173.194.41.16): icmp_seq=3 ttl=55 time=65.7 ms
64 bytes from www.google.com (173.194.41.16): icmp_seq=4 ttl=55 time=65.9 ms
64 bytes from www.google.com (173.194.41.16): icmp_seq=5 ttl=55 time=66.3 ms

--- www.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 65.456/65.858/66.369/0.378 ms

```

you can be sure that your internet connection is up and running.

If you have connectivity issues you'll get something like
```

ping: unknown host www.google.com
```

---

### Post by marcellk98 on 2014-06-24
After I type the code you have given, it merely says "ping: unknown host www.google.com"

Is there anything I can do to fix this issue then?

---

### Post by whitesmith on 2014-06-24
Power cycle your modem and router. If you still can't ping Google, you may have a bad hookup, bad connectors/cabling, or improper Internet connections. The least likely possibility is a break in your ISP's connections to their backbone. You need to check all of these, more or less in the stated order. TGhe last would have to be done by your ISP, of course.

---

### Post by marcellk98 on 2014-06-24
The thing is everywhere in my house there is internet and any device that can use internet is more then capable of using it, but for my computer it seems that it just won't work. I tried power cycling my router and modem, but it still doesn't load. I checked the wiring and everything is fine as far as i can see. I still don't know how to fix this and if anyone can help me please do so :(

---

### Post by zemega on 2014-06-24
What about Firefox proxy settings?

---

### Post by Impavidus on 2014-06-25
Can you ping to an IP address?```
ping -c5 173.194.41.16
```

---

### Post by buzzingrobot on 2014-06-25
If you can ping an IP but not a URL, it is likely name service resolution is not working, but you do have a working network connection.

If you cannot ping an IP and you cannot ping a URL, you probably don't have a network connection.  You could still have a name service issue, but, first things first.

Also, is it wifi or a wired ethernet link?

---

