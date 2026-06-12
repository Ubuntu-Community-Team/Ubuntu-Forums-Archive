---
title: "Network has stuck on Manual Config"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by BurntLime on 2008-08-03
I suppose this sounds like a real newbie question, but I have just installed Ubuntu 8.04 (LTS) as a dual-boot on my Acer aspire 1692 Wlmi with windows XP.

I had wireless working on it and it was accessing my network fine.

Started it up about a week ago and it wouldn't access my network, and now when I hover over the network icon it says "Manual Network Configuration" and it won't connect. I have had a look through some of the settings but couldn't make any sense of it, I think I must have set something different to what I should have done. Would rather like to get wireless back as I am down to running a long Ethernet cable from my router to the laptop

The wireless card is a Intel PRO set/Wireless b/g (came with laptop)

Apart from this problem (which I am sure a pair of home plug adapters would solve if it couldn't be fixed) I am absolutely LOVING Ubuntu, much easier and more user-friendly. Much easier to manage and I am relieved of the Blue-Screen-Of-Death!!! Now trying to convert other family members!

Thanks

BurntLime

---

### Post by northern lights on 2008-08-03
Can you post the output of ```
sudo lshw -C network && iwconfig
``` Thanks.

---

### Post by BurntLime on 2008-08-03
Hiya,

Thanks for the quick reply,

The output of the command is as follows: (I copied the whole thing)

joe@Ubuntu-Laptop:~$ sudo lshw -C network && iwconfig
sudo: unable to resolve host Ubuntu-Laptop
[sudo] password for joe: 
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:58:3f:ab
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:c0:9f:9a:ae:e3
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5788-v3.01 ip=192.168.1.67 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

joe@Ubuntu-Laptop:~$ 

Hope this provides some diagnostic info.

Joe

---

### Post by northern lights on 2008-08-03
Well, an Intel PRO Wireless worked oob in my old laptop.

Your device is configured and drivers are assigned. What does ```
iwlist eth1 scan
```result in?

---

### Post by BurntLime on 2008-08-03
The result for the command is:

joe@Ubuntu-Laptop:~$ iwlist eth1 scan
eth1      No scan results

joe@Ubuntu-Laptop:~$ 

thanks for your help

---

### Post by northern lights on 2008-08-03
I know this must sound like either a superfluous question or an insult, but are you sure you are within the reach of at least one WLAN router?

---

### Post by BurntLime on 2008-08-03
No, it's not an insult!

I can touch the top of my router ( linksys HG200 ) with my hand if I move the lid of my laptop, so wireless signal is not a problem.

---

### Post by BurntLime on 2008-08-03
Also, I am sure the WLAN router is working as I have a desktop and another laptop running of of it happily (Packard Bell and Samsung R20 respectively)

joe

Also, I can access the internet through the wireless card if I boot XP or SystemRescueCD.

---

### Post by InTheShires on 2008-08-03
I'm a n00b, so don't expect too much!

But on my Acer, I was having the same problem. It was solved by simply holding the wifi switch on for a few seconds. (Despite the fact the wifi light was already lit up!?) 

I also enabled Roaming.

---

### Post by BurntLime on 2008-08-03
> **InTheShires said:**
> I'm a n00b, so don't expect too much!

But on my Acer, I was having the same problem. It was solved by simply holding the wifi switch on for a few seconds. (Despite the fact the wifi light was already lit up!?) 

I also enabled Roaming.
hi InTheShires,

Thanks for the tip, I'll give it a try tomorrow.

It sounds like it's a good way to restart the wireless adapter.

Thanks for your help everyone.

BurntLime

---

### Post by Methuselah on 2008-08-03
Yeah, try enabling roaming.

---

### Post by BurntLime on 2008-08-03
from checking my laptop i've found that roaming is already enabled, but I will try holding the switch.

BurntLime

---

### Post by cariboo on 2008-08-03
I see your wireless card is listed as eth0 what if you run:

```
iwlist eth0 scan
```

do you get any result?

I have a strange problem my self, if my laptop is within a foot of the router antenna I can't connect, yet If I move about 4 feet away from the antenna it connects with no problem, I've got a Dlink +8db external antenna connected to my smc router, once connected I can put the laptop back where it was and have no problems.

Jim

---

### Post by northern lights on 2008-08-03
> **cariboo907 said:**
> I see your wireless card is listed as eth0 what if you run:```
iwlist eth0 scan
```The OP's wireless device is 'eth1'. 'eth0' is an ethernet adapter.

---

