---
title: "What should I expect from WIFI?"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Plumtreed on 2008-09-21
I have never encountered 'wifi' so I really don't know what to expect! I am using Hardy and have no problems with my network or connections. When away from home I use a notebook and my mobile phone as a modem. I run the usual Networkmanager 0.6.6 and GnomePPP for the mobile.

I have been in 'wifi' areas but I guess I don't really know even what to do to access the facility. Do I need more software or is there a button to press in order to 'scan for wifi'. Perhaps it will just find me! My notebook is wifi enabled but it is intended for Vista and there is a light and button that has to do with 'wifi'but that is for Windows.

I have read that Networkmanager 0.7.0 promises to do all these things seamlessly. It may be part of the new Ubuntu release. Is there a way of getting it now?

---

### Post by phidia on 2008-09-21
We need to know your hardware specs specifically your wireless card.
Open a terminal and enter > lshw -C network paste the output of that command here.

---

### Post by Redptc on 2008-09-21
You will probably find that any networks will be located by networkmanager and GnomePPP.

---

### Post by Plumtreed on 2008-09-21
Thanks Phidia, here are the results;

 *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:41:ff:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:11:7f:82
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

---

### Post by steveneddy on 2008-09-21
Usually when I enter an establishment with WIFI, the network manager shows me all of the bars and if there is a password for the service I just ask the staff.

McDonald's fast food restaurant has WIFI and it sends you to a website to sign with various hotspot vendors, AT&T included.

I have AT&T DSL at home, so I just use my regular AT&T user name and password.

---

### Post by MasterNetra on 2008-09-21
I myself use a Broadcom (not by choice mind you) I also don't see all the wireless that windows usually does. I also only connect at only a portion of the available bandwidth. (ex. 5Mb/s out of a 50Mb/s...10 if i'm really lucky. even if i am next to source.) I suspect its a driver thing and hopefully it will be taken care of in Intrepid when released. At least Wired works perfectly.

---

### Post by Plumtreed on 2008-09-22
Thanks for the replies and I see as the answer that Networkmanager should indicate the availability of a 'wifi' network. 

I'll have to go to Starbucks for a coffee and a trial-out!

---

### Post by RavUn on 2008-09-22
I have the same card you have.  You should be able to see the wireless networks just fine when going to network manager.  I was able to see them all but could only connect to open access points (wireless networks that don't require passwords).  My home wireless uses WPA and I could never connect.

I followed these instructions and it's been working fine ever since:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

