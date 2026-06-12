---
title: "[SOLVED] Wireless / can't get ip adress"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-10-16
So I'm having a bit of wireless troubles lately.

After changing from wep to a non secured network for a while and then going back to wep.

When I changed back to wep, it wouldn't connect anymore. 

When I then changed back to unsecured, same thing.

Now gnome doesn't seem to work at all so I'm using fluxbox.

I installed wifi-radar (network manager doesn't seem to on fluxbox)

It sees my wireless network. When I connect (try to do so) it says it can't get a ip adress.

--

The driver is ipw2200, it's up and running.

The interface if eth1.

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

```

lshw -C network

  ```
*-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 05
       serial: 00:15:00:4e:95:6e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firm
ware=ABG:9.0.2.6 (Mar 22 2005) latency=128 maxlatency=24 mingnt=3 module=ipw2200
 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:92:8d:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.1
68.1.4 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

---

### Post by Xerp on 2008-10-16
Looks to me like you're not getting a signal at all. I had this until I changed the wireless channel - took a few attempts to get the best one.

For me, it was down to interference from other people in my areas who also had wireless. I used the gwireless_applet to show my link quality, though there are a few other (possibly better) tools to show signal quailty.

---

### Post by billgoldberg on 2008-10-16
> **Xerp said:**
> Looks to me like you're not getting a signal at all. I had this until I changed the wireless channel - took a few attempts to get the best one.

For me, it was down to interference from other people in my areas who also had wireless. I used the gwireless_applet to show my link quality, though there are a few other (possibly better) tools to show signal quailty.

I hadn't thought of that.

I did a clean install of Ubuntu 8.10. Same thing.

It sees the wireless but won't connect. Never had this problem before.

I'll change the channel and see if that helps.

---

### Post by billgoldberg on 2008-10-16
Changing the channel did the trick.

I was up and running in seconds.

For future readers, you change the channel inside of your routers interface.

Usually it's [http://192.168.1.1](http://192.168.1.1) .

---

