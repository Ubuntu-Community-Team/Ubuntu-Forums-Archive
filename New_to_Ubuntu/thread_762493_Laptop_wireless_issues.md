---
title: "Laptop wireless issues"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by dwp0980 on 2008-04-22
Hi,

I have Gutsy installed successfully (I think) on my PC (64bit version) and on my laptop (x86).  I'm having problems with my wireless on my laptop.

The laptop is an Advent 7109A, and from what I can tell from searching specifications on the net, the wireless adapter is a Ralink RT2500.  I know there's an open bug in Gutsy around the RT2x00 adapters, and I've been trying to get it to work properly using the various HOW2s on this forum, but without success.

Symptoms are - 

*  Slow speeds (max of 6Mbits) even when right next to the router.  I know the router/adapter are capable of more, as I could get 48Mbits in Windows.
*  Seemingly random disconnects. I think it's related to doing something specific on the internet, but I can't seem to see a pattern.  When it disconnects, I have to reboot the router to get the wireless back working.

Anyway, I thought I'd go back to basics.

How do I find out what driver is being used for the wireless?  The HOW2s talk about blacklisting rt2500pci, but I don't think this is being used.  There's nothing that looks like a wireless entry in the output of _lspci_ and if I do

```
lsmod | grep rt
```

I don't get anything related to rt2500.  There are some rt2x00 entries, but I can't seem to blacklist them.

Any help/guidance greatly received.  I thought of trying Hardy, but it appears that the bug hasn't been fixed in that yet.

---

### Post by mikeyphi on 2008-04-22
Hi there and welcome!

Open a terminal and enter:
ifconfig
iwconfig

Post the results.

---

### Post by dwp0980 on 2008-04-22
Hi, thanks for responding.

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:03:0D:55:94:B0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xcc00 

wlan0     Link encap:Ethernet  HWaddr 00:13:D3:7E:35:0B  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe7e:350b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8009907 (7.6 MB)  TX bytes:458133 (447.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-7E-35-0B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"O2wireless2B7540"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:D0:ED:AF:A4   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by mikeyphi on 2008-04-23
Sorry to take so long to get back - you have a wireless connection, as you thought.
Try to work through this guide: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

especially from section 5

In theory your card should work 'out of the box' at least the driver (ra2500) is in Ubuntu, it's just that the chipset in your card might need something else.

If you continue to have problems the best next step is to use ndiswrapper with the windows driver.

---

### Post by dwp0980 on 2008-04-24
Great, thanks.  I got it working at a better speed (still not at 54Mbs).  Following those steps made me realise that it was on the USB, not PCI, and it didn't need the rt2500, it needed rt73 from the serialmonkey site.

---

