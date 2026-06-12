---
title: "Timing out whilst on-line"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by 0rod on 2013-01-27
I am running Ubuntu 12.04 and use Firefox as my web browser:  I am also using Windows XP with Firefox as my web browser.  I am trying to pension off the Windows machine and get all my programs to run under linux but whenever I go on-line with the linux machine no matter what I am doing, after a short time I get a "can find server at xxx", then if I click on the "Try Again" button it sometimes finds it after a few seconds and other times takes me back to the error message.  

My connection is via satellite (NBN Co) so this could be the the problem but the Windows machine sitting beside it and using the same LAN seems to have no problems.

I would greatly appreciate any help or suggestions.

cheers all

---

### Post by audiomick on 2013-01-27
You may get help quicker with a little more info.

Are you on a cable or wireless?

Do
```
sudo lshw -c network
```

and post the results here so that people can see what network adapters you have.

---

### Post by 0rod on 2013-01-27
It makes no difference; it looses it on both ethernet and/or wireless.  Lost connection 3 times trying to get back to this forum.  I suspected the satellite at first but I've found that it does it on ADSL2 also.  I figure it has to be either the hardware or the Ubuntu/Firefox combination.  Maybe I'll try a different browser and see what happens.

Thanks for the reply Michael, I will do the other bit and post it as soon as I can.

It looses connection whils I am typing and I have to re-send to get the message through

Cheers
Rod

---

### Post by 0rod on 2013-01-27
G'day again Michael,
the results of the sudo thing follow; 

 *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 00:90:f5:bf:89:1c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:53 memory:f6320000-f6323fff ioport:d100(size=128) ioport:d000(size=256) memory:f6310000-f631ffff memory:f6300000-f630ffff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: e0:b9:a5:4a:42:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-36-generic firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:c000(size=256) memory:f6200000-f6203fff

---

### Post by audiomick on 2013-01-28
I don't know off hand if the Realtek WiFi needs proprietary drivers. I would tend to assume so, as it seems that most wireless adaptors do. Did you installs proprietary drivers for it? Given that it is working at all, I expect so.

Edit: wait on, just thought to look at the specs here. This machine has this Realtek adaptor
```
 description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.

```

Not the same one as yours, but it is fair to assume that you need drivers for it.


The wired connection shouldn't need any drivers or anything else, for that matter. It should just work. I believe I have seen reference to that ethernet adaptor, maybe even on one of my machines. Any rate, I wouldn't expect to have any trouble with it normally.


I think trying another browser is not a bad idea. Opera would be the first candidate.
You could also try this one:
[http://www.elinks.cz/]("http://www.elinks.cz/") That should run even if you are booted into a command line only environment. The interesting thing about that would be to exclude some fault in the GUI.

A hardware fault as such is also possible. The thing is, you say you are seeing the same behaviour on both a cable and a wireless connection. You also say a different machine is connecting without a problem to the same router. That all seems to exclude most possibilities for a hardware fault. You should, of course, do the simple tests like swapping out the ethernet cable, plugging in to a different port on the router, and so on. I suspect you wont find anything, though.

Another thing to try is booting into the live environment to see how it behaves there. That is the "try ubuntu without installing" option on the cd or USB you installed from. Try at least the cable connection from there to see if it works properly or not. If so, you have a clear indicator that something is not right with your install.

---

### Post by 0rod on 2013-01-28
Thanks again for your time and effort Michael,  I think I might have nailed it; I have installed a browser called rekonq that i found in the Ubuntu software shop and so far (I'm still testing it) there hasn't been a hang-up.  I was reluctant to blame Firefox because I have used it for ages and am happy with it.  It doesn't appear to have any problems on my Windows machine at all but if I seriously think about when the problems started ('coz it hasn't always done this), it may have been after an update on the linux machine.

Cheers
Rod

---

