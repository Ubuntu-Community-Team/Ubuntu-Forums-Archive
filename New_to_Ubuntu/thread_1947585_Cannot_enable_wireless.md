---
title: "Cannot enable wireless"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by azulanson on 2012-03-26
I am running Ubunutu 10.04. A new user and loving it. Everything was going well then my wireless stopped working.

In the notification area I see Networking is enabled and wireless is grayed out.  

I have seen other posts along this line and assume wireless may have become "Hard Blocked".  However, I do not see and am not aware of any buttons on my laptop that do this.  I have tried Fn+F11 and all others to no avail. 

Below is some information about my system... gleaned from other posts.  Hopefully it helps. 

I would really appreciate the help. Thanks. 

> sudo lshw -C network
```
  *-network:0 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:0d:00:d4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:22 memory:b0006000-b0006fff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:61:c4:e8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:b0007000-b0007fff ioport:2000(size=64)
```
> iwconfig eth1
```
eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
> sudo rfkill list all
```
 {nothing printed} 
```

---

### Post by bkratz on 2012-03-27
You probably don't have rfkill installed ( it is not in my 10.04).  You could easily do this in synaptic (system>>administration>>synaptic package manager) . Just  search for rfkill and select it for installation then repeat the rfkill list all command.


Also what type of laptop is it (so we can look for additional information ( like a switch) on googlubuntu).

---

### Post by azulanson on 2012-03-27
The problem persists. I installed rfkill as you suggested, it wasn't selected in the package manager, but I still don't get output. Don't know why that would be. 

The laptop is a Sony Vaio, VGN-FS690.

Anyway, I will definitely search around for some info on googlubuntu.  Thanks again.
 
> which rfkill
```
/usr/sbin/rfkill
```

> sudo rfkill list all
```
{nothing printed}
```

---

### Post by Scott Baker on 2012-03-28
This may sound bizarre, but try this. Disable the networking, so that both networking and wireless show as disabled. Now, re-enable the networking, then try the wireless and see if it re-enables. When I upgraded my Dell M-90, I had to do this a couple of times before it would recognize the wireless sources around it. Now it's behaving as it should, automatically recognizing the wireless sources nearby.

---

### Post by bkratz on 2012-03-28
quote
"
I have seen other posts along this line and assume wireless may have  become "Hard Blocked".  However, I do not see and am not aware of any  buttons on my laptop that do this.  I have tried Fn+F11 and all others  to no avail."

See if the wireless switch is "on"

---

### Post by azulanson on 2012-04-12
Holy crap, it works! It was the switch all along.  I  spent forever trying to figure this out and now I really feel dense.  I've had this laptop for years and years and never noticed that button. 

Thank you all for your replies and assistance.  Sorry it was something that silly.

---

### Post by bkratz on 2012-04-13
> **azulanson said:**
> Holy crap, it works! It was the switch all along.  I  spent forever trying to figure this out and now I really feel dense.  I've had this laptop for years and years and never noticed that button. 

Thank you all for your replies and assistance.  Sorry it was something that silly.


Sure glad you got it. Please return and mark the thread as [solved] with the thread tools at the top of the page.  Again, congratulations!

---

### Post by roelforg on 2012-04-13
[QUOTE=azulanson]
Holy crap, it works! It was the switch all along. I spent forever trying to figure this out and now I really feel dense. I've had this laptop for years and years and never noticed that button. 
 
Thank you all for your replies and assistance. Sorry it was something that silly.
[/QUOTE]
 
I'll bet you have a hp system,
they always put an oversensitive wifi switch on a weired place that allows the bag, your lap, other stuff to press it and turn wifi off... But never the other way around.
 
EDIT: Wrong quote, i meant to quote the op... Fixed

---

