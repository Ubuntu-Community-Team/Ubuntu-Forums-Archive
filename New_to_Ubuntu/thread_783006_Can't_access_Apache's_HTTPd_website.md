---
title: "Can't access Apache's HTTPd website"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by galvao on 2008-05-05
Greetings.

This one have, most probably, a very, VERY stupid and dumb cause, but anyway...

I can't access Apache's HTTPd website: [http://httpd.apache.org/](http://httpd.apache.org/)

This is a clean install of Hardy and I've tried both with Firefox and lynx with the same results:

```
zaphod@magrathea:~$ lynx http://httpd.apache.org

Looking up httpd.apache.org
Making HTTP connection to httpd.apache.org
Alert!: Unable to connect to remote host.

lynx: Can't access startfile http://httpd.apache.org/
```So... any ideas of why this is happening? Remember: This is a CLEAN Hardy install, so I've never tampered with the hosts file or anything like that.

TIA,

---

### Post by rubicon on 2008-05-05
I guess it's problem with lynx.

What gives you ```
HEAD http://httpd.apache.org/
```? Does it connect?

---

### Post by galvao on 2008-05-05
Hi, thanks for your reply.

As, I've stated before, it also happens with Firefox, so it's not a lynx specific issue.

Here's the result of the HEAD command:

```

zaphod@magrathea:~/workspace/insightory$ HEAD http://httpd.apache.org
500 Can't connect to httpd.apache.org:80 (connect: No route to host)
Content-Type: text/plain
Client-Date: Mon, 05 May 2008 16:56:44 GMT
Client-Warning: Internal response

```

---

### Post by Monicker on 2008-05-05
Can you ping the site?  Perhaps there is a routing problem between you and them interfering with network connectivity in general.

Here is what I get:

```
 ping -c 4 httpd.apache.org
PING httpd.apache.org (192.87.106.226) 56(84) bytes of data.
64 bytes from aurora.apache.org (192.87.106.226): icmp_seq=1 ttl=244 time=161 ms
64 bytes from aurora.apache.org (192.87.106.226): icmp_seq=2 ttl=244 time=162 ms
```


And I have no problems pulling up the page from here.

---

### Post by galvao on 2008-05-05
Thanks for your reply.

Yes, there's probably something happening there:

```

zaphod@magrathea:~/workspace/insightory$ ping -c 4 httpd.apache.org
PING httpd.apache.org (192.87.106.226) 56(84) bytes of data.
From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
From 192.168.1.2 icmp_seq=3 Destination Host Unreachable
From 192.168.1.2 icmp_seq=4 Destination Host Unreachable

--- httpd.apache.org ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 18053ms
, pipe 3

```

How can I detect if the problem is with my ISP?

TIA

---

### Post by Monicker on 2008-05-05
I would start with a traceroute to the destination, to see if you can determine where its dying at.

Try a normal traceroute:
```

traceroute httpd.apache.org
```

and with tcptraceroute
```

tcptraceroute httpd.apache.org 80
```

Please show the results of these commands.  The second can be useful for intermediary devices that might reject normal traceroute queries.  You may have to install both packages.

```
sudo apt-get install traceroute
sudo apt-get install tcptraceroute
```

---

### Post by galvao on 2008-05-05
Ok, this is by far the weirdest thing I ever saw:

```

zaphod@magrathea:~/workspace/insightory$ traceroute httpd.apache.org
traceroute to httpd.apache.org (192.87.106.226), 30 hops max, 40 byte packets
 1  192.168.1.2 (192.168.1.2)  3002.651 ms !H  3002.644 ms !H  3002.635 ms !H
zaphod@magrathea:~/workspace/insightory$ tcptraceroute httpd.apache.org
Selected device eth0, address 192.168.1.2, port 39088 for outgoing packets
Tracing the path to httpd.apache.org (192.87.106.226) on TCP port 80 (www), 30 hops max
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
Destination not reached

```

Is it as bad as it looks? The weird thing is that I browse the web, send and receive e-mails, everything a-ok, the problem seems to affect *only* the Apache site...

TIA,

---

### Post by Monicker on 2008-05-05
Its odd that traffic for that site does not even seem to get past your gateway.  The 192.168.1.2 address is your router, correct?  I would think that either your router is blocking it for some strange reason, or you isp's network equipment is immediately telling your router that it is not reachable.

---

