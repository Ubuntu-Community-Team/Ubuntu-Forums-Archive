---
title: "[SOLVED] NEW Dell Inspiron 1520 - no wifi"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by guycross on 2008-11-02
Hey heys, I did the right thing, I searched - found nada
I asked questions on the end of existing posts - no1 replied.
So I am making my own thread, sorry.

I am a 100% ubuntu newbie and I installed through wubi (and I rhyme like a rapper so sue me! -- oopsie got carried away!!)

I am new to unbuntu, everything on my 1520 is working great, but I cannot connect to wifi - I have tried typing the settings into network manager manually - but nothing.

My netowrk is a personal wpa - with a password

My laptop has a Broadcomm 43xx wifi card in it.

Help

Thanks

Guy

---

### Post by Peter09 on 2008-11-02
Can you provide the output of the following terminal commands

```
lshw -C network
```

and

```
ifconfig
```

---

### Post by guycross on 2008-11-02
eth0      Link encap:Ethernet  HWaddr 00:1c:23:a3:0a:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15776 (15.7 KB)  TX bytes:15776 (15.7 KB)


AND

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a3:0a:03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:26:73:09:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: fe:f0:b1:66:9f:63
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

THANKS

---

### Post by Peter09 on 2008-11-02
What do you see in

System->Preferences->Network Configuration->Wireless

---

### Post by nothingspecial on 2008-11-02
Have a look at pg 8 of this thread specifically Ayuthia`s 2nd post. If that does not work read the whole thread.

OOps forgot the link -here it is

[http://ubuntuforums.org/showthread.php?t=963978&page=8](http://ubuntuforums.org/showthread.php?t=963978&page=8)

---

### Post by guycross on 2008-11-02
my crappy attempts at setting it up manually - it hasnt "found" my wireless network - which is running perfectly, as thats what iam using now (on my old p600!)

---

### Post by rotwang888 on 2008-11-02
It's your Broadcom card.  Sorry.  I've been there.  Check [this thread](http://ubuntuforums.org/showthread.php?t=25683) to get you on the road to recovery.  Or better yet, just spend 20 bucks and get yourself an Intel Pro Wireless 2200.

---

### Post by guycross on 2008-11-02
Followed this advice in reply #5 and here I am reply from my dell!!

Thanks to all. (i am sure i will be back)

Guy Cross
[email]guy@sleepywhisper.com[/email]

---

### Post by rotwang888 on 2008-11-02
Sweet! Glad to hear it.  Looks like that's a lot easier in Intrepid than it was in Hardy.  Sorry for the antique link. Install without internet connection! Wow. That sure would have helped me back in the dark ages 6 months ago. Kids these days...

---

