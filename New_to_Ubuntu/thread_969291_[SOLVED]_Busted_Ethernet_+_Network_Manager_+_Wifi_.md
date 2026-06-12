---
title: "[SOLVED] Busted Ethernet + Network Manager + Wifi = No Connection"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by OZFive on 2008-11-03
Hello,

So here is the deal.  My Niece and Nephew have been running across the room for the last couple of days while their Grandma was in town.  The were allowed into the room with my laptop unsupervised (never allowed)where cords are across the floor.  

I come home from work one day to connect up and cannot connect to the Wired Network.  I check my connections, cord, Network Manager recognizes the connection, but will not connect.  So I try to go to Wifi for a bit to get some last minute reports in and it fails to connect to any Wifi network.  Our usual home network is not connected to (password enabled) and the free signal from nowhere (I have no idea where it is coming from) is not connected.

I am understandably annoyed.  I go downstairs where I am told about the kids in the room and am told by Grandma (my mom) that the kids had tripped over the cord a few times before she was able to get them out of the room.  

So I am pretty sure my Ethernet connector/card in my laptop is bust.  I booted from Live CD to make sure and even tried to boot from a Windows XP partition and nothing would connect the Ethernet but recognized it was there.

This would be a pretty easy fix.  Take it to get it fixed.  But here is the issue.

Why will Network Manager not allow me to connect to the Wifi signals available just because the Ethernet connection would not.  In XP I get a fine signal and that is what I am using now to get on and post.  I know about WICD and will try that too but I am curious as to why NM would not switch to the Wifi instead.

Ideas?

8.10 Interpid Ibex

---

### Post by superprash2003 on 2008-11-03
you may just need to find the right drivers.. have you tried system->admin->hardware drivers ?? if problem exists.. post output of the following commands
1)iwconfig
2)lshw -C network

---

### Post by OZFive on 2008-11-03
> **superprash2003 said:**
> you may just need to find the right drivers.. have you tried system->admin->hardware drivers ?? if problem exists.. post output of the following commands
1)iwconfig
2)lshw -C network

Here is what I got...

> 
matthew@matthew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"XE0E2"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:ED:8E:95   
          Bit Rate:36 Mb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-60 dBm  Noise level=-96 dBm
          Rx invalid nwid:50662  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

> matthew@matthew-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:ca:a8:5c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:9a:a6:9f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.3 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:7e:66:d9:c1:d5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


---

### Post by OZFive on 2008-11-03
I got WICD installed but it is having issues as well.

---

### Post by OZFive on 2008-11-04
Bueller...

---

### Post by lifestream on 2008-11-04
This thread should help you:
[http://ubuntuforums.org/showthread.php?t=940048](http://ubuntuforums.org/showthread.php?t=940048)
(Did a quick google search for " Intrepid AR242x " )
Seems people on that thread have got it working. It's one of those "unsupported" cards.

---

### Post by OZFive on 2008-11-04
Hey THANKS you for pointing me that way!  Seems to be working with wicd and that is a good thing.

Now I am wanting to get back on the ethernet cord and get my full speed available.  

So broken ethernet port.  Tech says I am pretty screwed as they would need to replace the entire motherboard.  I got my laptop for $500 so that would be a pretty screwey thing to do to spend that much money on it again.

Would one of these in my ExpressxCard slot work with Ubuntu?
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1147850020524&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2052479139B01]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1147850020524&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2052479139B01")

---

### Post by OZFive on 2008-11-05
Well I guess I will go an buy one and find out, report back for future users and if it does not work seek further help.

---

### Post by OZFive on 2008-11-05
Sweet.  It works!

So if anyone has a busted Ethernet (Gigabit) port and does not want to spend major $ on a new motherboard or replace thier entire laptop I really reccomend a Linksys EC1000 ExpressCard Adapter.  It was $59.95 up at Frys Electronics (love that place).

Plug and Play with Network Manager 0.7.0

Not with WICD though.

Works really great.  Stupid Geek Squadie would have had me buy a whole new laptop.  Lame.

---

