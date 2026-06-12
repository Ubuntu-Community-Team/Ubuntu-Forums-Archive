---
title: "WG111v3 wi-fi connection issue"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by AEsirson on 2012-11-09
Hello,
I currently cannot connect to the internet with my USB wifi adapter.
It's an Netgear WG111v3
Ubuntu says it's connected and I have an IP address, but I can't even ping the gateway.
It works fine on windows.
Searching on google has led me to believe it's a driver issue, but I am not able to install it.

Some stuff I think might be important:
ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 00:26:f2:b7:e4:b1  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::226:f2ff:feb7:e4b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:152175 (152.1 KB)  TX bytes:25124 (25.1 KB)

```
lsusb:
```
Bus 002 Device 005: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
```

Thanks for your advice

---

### Post by daslinkard on 2012-11-09
This [link]("http://myfossness.blogspot.com/2010/05/how-to-get-rtl8187b-working-in-ubuntu.html") may help you as it seems to have a solid work around.  Check it out and let me know if it works for you.

---

### Post by AEsirson on 2012-11-10
No it did not help, after the installation of the WinXP driver using ndisgtk I get "FATAL: Module ndiswrapper not found."
When I reboot the interface wlan0 disappears.
Could it be because of [this]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/1023645")?

---

### Post by Bucky Ball on 2012-11-10
Ndiswrapper is WELL superseded for this card and many others. _Avoid!!!_ Now you have it installed you are going to have issues getting the correct driver installed unless you uninstall and do some blacklisting. Not a great start.

There is TONS of info and howtos available for getting this card working. Have a dig through this:

[http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=+WG111v3+ubuntu&ql=](http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=+WG111v3+ubuntu&ql=)

First off, you should do an update via a ethernet cable. See if you are offered the correct driver (which probably won't install as you have the ndiswrapper stuff in the way) and check 'Additional Drivers'. 

To all users: *_dig deep before going anywhere near ndiswrapper.  _*As mentioned, it is no longer used for the majority of cards ... and that means 95+ percent. The last major problem was with Broadcom cards but since the STA and B43 drivers arrived, ndiswrapper is rarely seen and is pretty much obsolete, at least in Ubuntu. ;)

PS: The link you were provided with appears to be for a totally different card: A Realtek RTL8187B. Have no idea why this was suggested as your card is not only a different model, but a totally different make! Netgear ... This might help:

[http://ubuntuforums.org/showthread.php?t=732827](http://ubuntuforums.org/showthread.php?t=732827)

Also, could you open a terminal (Applications>Accessories>Terminal) and post here the results of this command:
```

sudo lshw -C network
```Cheers. It appears from a couple of the links I've looked at the driver may have been in the kernel since 2.6.** I'll assume you're using 12.10? If so you might like to give 12.04 LTS a whirl. Much stabler at the moment and a better ride for a newcomer to learn the Ubuntu ropes.

---

### Post by newb85 on 2012-11-10
> **Bucky Ball said:**
> First off, you should do an update via a wireless cable. 

Perhaps you meant *Ethernet* cable?  ;)

---

### Post by Bucky Ball on 2012-11-10
> **newb85 said:**
> Perhaps you meant *Ethernet* cable?  ;)

Indeed. Post edited. Thanks for that, just got up! ;)

---

### Post by newb85 on 2012-11-10
I understand.  I've lately been noticing the adverse affects of posting between waking up and getting my coffee.

---

### Post by AEsirson on 2012-11-10
Ok I'll give 12.04 a try since it seems I need to reinstall the OS to get rid of ndiswrapper anyway.

I had installed all available updates using the ethernet cable, but it still didn't work.

Here is the result of "sudo lshw -C network" just in case it's useful somehow:
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 00:25:22:cd:54:f7
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.2.105 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.4
       logical name: wlan0
       serial: 00:26:f2:b7:e4:b1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.5.0-17-generic firmware=N/A ip=192.168.2.101 link=yes multicast=yes wireless=IEEE 802.11bg

```

And as you said there is tons of infos available, but most are from 2010 and before, and quite confusing (to me at least;))

Many thanks for your help I'll post again after I've installed 12.04

---

### Post by AEsirson on 2012-11-10
Yes it worked once I installed 12.04.
Thank you guys very much!!

---

### Post by Bucky Ball on 2012-11-11
Great news! Should work out of the box in 12.10 eventually, too. Eventually. ;)

---

