---
title: "WICD wireless set-up difficulty"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by bwrth on 2012-03-29
Hi, 

It's lovely and sunny outside in the garden :wink: and I'm trying to connect to my wireless network on my dual-boot Lubuntu/XP system.

I found in the One-Stop Lubuntu thread that I can install WICD to set-up wireless more easily. Great. I tried it before coming outside, putting in the 'pre-shared key' on my encrypted wireless network and it doesn't work (after a couple of minutes of whirring and thought, it comes back with an error message: ERROR, Connection Failed, Bad Password. (I have checked and rechecked that the password is correct. I am trying to connect to the right network). None of the WPA options work (eg. Passphrase/PSK/Hex data (not that it's hexadecimal). I'm logging in now from XP on the same working wireless network. Please can anyone help me connect? I will reboot to Lubuntu to try any suggestions anyone might have to help me connect or I can go inside and hook up to the wired connection if required. Thanks in advance if you can spare a few minutes.

---

### Post by TeoBigusGeekus on 2012-03-29
Have you installed any drivers for your wireless card?
What model is it?
```
lshw -C network
```

---

### Post by bwrth on 2012-04-02
[TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094"), sorry for not noticing you had replied. I forgot to subscribe to the thread at the time I posted the message, which I have now done! Will reboot into Lubuntu and try your suggestion and see what card came with this laptop. I hadn't realised the wireless issue can be a tricky one. Wanting to fix it the same day may have been a bit over-optimistic, I now realise!!

---

### Post by bwrth on 2012-04-02
I have not installed any drivers for my wireless card. The card is able to see all the wireless networks in the vicinity but it cannot connect to them, not even to an open network without a password (I tried briefly, removing the password on the router and even without a password,  Lubuntu would not connect).

Here is the output I got in the terminal in Lubuntu:

...
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

> sudo lshw -C network
[sudo] password for bwrth: 
  *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:c4:c9:80:75
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=1.1-2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:e4600000-e461ffff memory:e4620000-e4620fff ioport:4020(size=32)
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth2
       version: 02
       serial: 00:1a:73:e6:b6:16
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:e4000000-e4003fff
>

---

