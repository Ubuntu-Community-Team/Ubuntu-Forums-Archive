---
title: "Where's Connection Properities in kubuntu?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by abooks on 2008-11-18
After a week of frustration trying to get ubuntu to work, I installed kubuntu and I'm microns from getting it hooked up (I think). Using the Sprint instructions to install my dongle, I got as far as "connection properties", but don't know how to get to them in K. It says I have an internet connection, but apparently without resetting Eth0 to ppp0 (?) the mail and internet programs don't work.

---

### Post by superprash2003 on 2008-11-18
what is the output of ping google.com from your terminal

---

### Post by abooks on 2008-11-18
I'm a rank N00b. . .especially in Kubuntu: you ping from terminal, just "ping google.com"?

Thanks

---

### Post by Tony Flury on 2008-11-18
open the terminal

type :
```

ping google.com

```

and copy the output into a fresh reply in this thread.

also post the output of 
```

ifconfig

```
and
```

iwconfig

```

---

### Post by abooks on 2008-11-18
I just spent 45 minutes putting all the stuff in here, only to find the connection had timed out. I can't cut or paste, and I'm not a fast typer, but if I have to move data from a Linux Machine to a Vista one to send it here, is there some way? Can I synopsize? (snivel. . .)

The ping pinged (64.233.187.99) 56 (84) bytes of data

64 bytes from jc-in-f99.google.com (64.233.187.99) icmp_seq=1 ttl=236 time=181 ms
64 bytes from jc-in-f99.google.com (64.233.187.99) icmp_seq=2 tt1=236 time=198 ms
ditto                                                       3              185
ditto                                                       4               184

and so on

---

### Post by abooks on 2008-11-18
OK, the other readouts:

if config
Eth0 Link encap: Ethernet Hwaddr 00:19:D1:37:B6:EF
UP BROADCAST MULTICAST MTU;1500 Metric:1
RX Packets:0 error:0 dropped; overruns;0 frame;0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
Collision:0 txqueuelen:1000
RX bytes:0 (0.ob) TX bytes:0 (o.ob)
Base Address:0xecc0 Memory:dfde0000-dfe00000

lo Link encap: Local Loopback
Inet addr:127.0.0.1 Mask:255.0.0.0
Inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX Packets:0 errors:0 dropped:0 overruns:0 carrier:0
Collisions:0 txqueuelen:0
RX bytes:0 (0.0b) TX bytes:0 (0.0b)


Ppp0 Link encap: Point-to-point protocol
Inet addr:75.211.86.8 P-t-P:66.174217.64 Mask: 255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1500 Metric:1
RX packets:315 errors:0 dropped:0 overruns:0 frame:0
TX Packets:316 errors:0 dropped:0 overruns:0 carrier:0
Collisions:0 txqueuelen:3
RX bytes: 45824 (44.7KB) TX bytes:24317 (23.7KB)

Iwconfig
lo  no wireless extensions

eth0 no wireless extensions

---

### Post by abooks on 2008-11-19
bump

---

### Post by superprash2003 on 2008-11-19
open firefox and under the address bar type 64.233.187.99 and open it.. does google page open?

---

### Post by abooks on 2008-11-19
Can't get Firefox, though SOMETHING is "connected".

I click on Knetwork Manager. . .nothing happens. I can &#8220;connect&#8221; with KPPP, but when I go to Adept installer, Firefox is there but not available (that faded color you click on it but nothing happens). I get prompts for Kopete and Konquerer but know nothing about them and I can't connect with anything through them. I can&#8217;t find anywhere to type the address you gave.

In thrashing around, now APT doesn't work, so no synaptic package manager.

---

### Post by superprash2003 on 2008-11-20
try it on any web browser.. instead of typing google.com type 64.233.187.99

---

### Post by abooks on 2008-11-20
I tried putting that number in everything that LOOKED like a web browser in Kubuntu, both by name and by number, and nothing worked. From those readouts it looks like both eth0 and ppp0 are in there, but is there a way in kubuntu to make ppp0 dominant?

---

### Post by superprash2003 on 2008-11-21
both ppp0 and eth0 route to the same place right? which is your modem.. so that looks fine..

---

