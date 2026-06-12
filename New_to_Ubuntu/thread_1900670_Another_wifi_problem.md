---
title: "Another wifi problem"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by chris1216 on 2011-12-26
All,

I recently inherited a MSi L1350D netbook.  It had windows 7 starter, but I have always wanted to try a version of Linux so I backed up the drive,  and over wrote it with Ubuntu 10.04 LTS.  Now my wifi would turn on but not connect to my wireless.  I disabled my MAC filtering requirement on the router and I can connect with no problems.  

Is there a way to connect to my router with the MAC filtering enabled?  I am very new so please go easy.


Chris

---

### Post by anewguy on 2011-12-26
> **chris1216 said:**
> All,

I recently inherited a MSi L1350D netbook.  It had windows 7 starter, but I have always wanted to try a version of Linux so I backed up the drive,  and over wrote it with Ubuntu 10.04 LTS.  Now my wifi would turn on but not connect to my wireless.  I disabled my MAC filtering requirement on the router and I can connect with no problems.  

Is there a way to connect to my router with the MAC filtering enabled?  I am very new so please go easy.


Chris

Did you try putting the MAC address of the adapter in the netbook in the allowed MAC list in the router?

---

### Post by chris1216 on 2011-12-26
yes, and that worked with the windows 7 starter but not now.

---

### Post by anewguy on 2011-12-27
Well, MAC filtering is purely a router function - the PC connecting to it has nothing to do with that - only that it's MAC must be in the table in the router.

Right now I would say you need to check and see what MAC is showing for your adapter in Ubuntu, as perhaps the driver somehow or another isn't broadcasting it.

Open a terminal window and type:

ifconfig <press enter>

Your wireless adapter will probably show as something like wlan0 - look for the hardware address as that will be the MAC address.

If it is different than what you have in the router, add it in (don't let it be something like all zeros though).

If it's the same, we need to dig deeper to see if the driver is sending the MAC address.

---

### Post by chris1216 on 2011-12-27
i opened a terminal, and ran ifconfig and this was the result:


wlan0     Link encap:Ethernet  HWaddr 48:5d:60:62:2c:fc  
          inet addr:192.168.1.142  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5d:60ff:fe62:2cfc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168082369 (168.0 MB)  TX bytes:6901478 (6.9 MB)

---

### Post by lkraemer on 2011-12-27
In a Terminal Window do:
```

ifconfig

```
should give the Hardware address you need.
> 
wlan0     Link encap:Ethernet  HWaddr 48:01:02:03:04:05

Is this the info in the Router?

lk

---

### Post by chris1216 on 2011-12-27
Yes, for my machine I had "wlan0     Link encap:Ethernet  HWaddr 48:5d:60:62:2c:fc" entered as one of the MAC addresses.  I just renabled MAC filtering and it kicked me off.  I am now on a hard line and had to reboot to get the system to recognize it as it kept trying to go back to wireless.

---

### Post by chris1216 on 2011-12-27
As a side note would it matter that I am running 10.04 LTS on a netbook?  And if so would there be a better version to install and run?  I tried the specific netbook version and had the same problem.  I tried 11.10 and same thing.  I went to this version as I liked the interface (if that is the correct term), and the way I was able to navigate between programs the best.

---

### Post by lkraemer on 2011-12-27
On my Router I need to select the Device or give the IP address.
```

ifconfig

```
will give you that information on the second line.
> 
wlan0     Link encap:Ethernet  HWaddr 48:01:02:03:04:5  
          inet addr:192.168.04.40

Then, I am asked for the Days of the Week selection, and the time block each day that a connection is allowed.  Some can also use MAC Filtering.

I'm afraid that you will need to try a few more tests to get it working.

I always disconnect all Wifi devices, and my FreeNAS Server, before
rebooting my Router or Cable Modem.

Ubuntu 10.04.3 LTS is a good choice.

lk

---

### Post by anewguy on 2011-12-27
I also see where it has an inet6 address listed - I'm wondering, perhaps this is a ipv4 vs ipv6 error?  Not sure off the top of my head how to be sure ipv6 is disabled at the ubuntu end - I would need to look it up.

Also, with MAC filtering disabled and you connected wirelessly, click on the network manager icon and then on connection information - see if the hardware address there matches as well.

Dave ;)

---

### Post by chris1216 on 2011-12-27
Thank you lkraemer and Anewguy.  In going through my settings, on the computer and the router I was able to figure out I had a wrong setting in the router.  As someone who is fascinated by this I cannot thank you enough for your help.  No I can walk around my house with the wifi on the netbook running and read this blog.

---

### Post by anewguy on 2011-12-27
Glad things are working for you now!

Dave ;)

---

### Post by chris1216 on 2011-12-27
Thanks.  How do I mark this thread as SOLVED?

---

### Post by anewguy on 2011-12-28
At the top of the thread you'll see a "Thread Tools" option - click on it and click on mark as solved.

---

