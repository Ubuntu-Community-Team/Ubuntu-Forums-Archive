---
title: "Setup static ip, now no internet access?"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by roseysdaddy on 2013-04-08
I am trying to setup a static ip for this server, at 192.168.1.100, and I can get it to where it is seen on my network, but isn't getting internet access.

Here is my ifconfig output:
[http://imgur.com/RW53w6v,fPxgkAi,G0bG7os#0](http://imgur.com/RW53w6v,fPxgkAi,G0bG7os#0)

here is my network interfaces config:
[http://imgur.com/RW53w6v,fPxgkAi,G0bG7os#1](http://imgur.com/RW53w6v,fPxgkAi,G0bG7os#1)

And here is my router, showing that it doesn't have a "lease"  like my wife's ipad:
[http://imgur.com/RW53w6v,fPxgkAi,G0bG7os#2](http://imgur.com/RW53w6v,fPxgkAi,G0bG7os#2)

Any info would be much appreciated.


Figured out a workaround, just set my router to give the mac address the desired ip, then changed the conf back to dhcp.

---

### Post by sanderj on 2013-04-08
> **roseysdaddy said:**
> 
Figured out a workaround, just set my router to give the mac address the desired ip, then changed the conf back to dhcp.

I wouldn't call that a workaround, but the best solution; it will avoid headaches.

In case of network problems, it always good to run

```
mtr -nrc2 8.8.8.8

```
and see what it says.

---

