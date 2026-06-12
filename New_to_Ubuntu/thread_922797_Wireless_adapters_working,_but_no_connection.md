---
title: "Wireless adapters working, but no connection?"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Parhelion on 2008-09-17
So, I'm about a new as they come to this, and I hope you guys can bare with me while I try to pick things up.  That said, on to the problem...

I've been trying for a couple of days to get wireless to work with my ubuntu 8.04 laptop.  I've even tried different adapters, to no avail.  I have a Linksys WUSB100, and Linksys WUSB54GC, and a Linksys WPC54G.  I would prefer to have the WPC54G working, since it's physically smaller, but getting anything to work would be a blessing.

When I put in the WPC54G and WUSB100 adapters, they light up (showing both a link and power is going to them).  In the network tab on the top bar of my screen, however, it shows two "networks" such as:

Wireless Network (Unknown Unknown)
Wireless Network (Unknown Unknown)

It won't allow me to select any of these networks to use, however, and will not let me connect to the internet.  

I've tried installing drivers, but either I havn't done that correctly or it isn't the problem (I suspect it has more to do with the 'unknown' status of the networks).

---

### Post by Sealbhach on 2008-09-17
Try this command and see what it does:
```

sudo dhclient wlan0

```

.

---

### Post by Parhelion on 2008-09-18
Typing that in gets the following:


wmaster1:  unknown hardware address type 801
wmaster0:  unknown hardware address type 801
SI0CSIFFLAGS:  No such file or directory
SI0CSIFFLAGS:  No such file or directory
wmaster1:  unknown hardware address type 801
wmaster0:  unknown hardware address type 801
Listening on LPF/wlan0/00:90:4b:ea:0c:7e
Sending on   LPF/wlan0/00:90:4b:ea:0c:7e
Sending on   Socket/fallback
receive_packet failed on wlan0:  Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet:  Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
send_packet:  Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
send_packet:  Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Sealbhach on 2008-09-18
Did you install windows drivers using ndiswrapper?

If so, check if any of these steps here works:

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)


.

---

### Post by Parhelion on 2008-09-18
Alrighty...

I went through that entire document and my poor wireless connection still doesn't work (in fact, at one point, it stopped picking up the "Unknown" networks altogether).  

I did notice something when I did "lshw -C Network"; for the wireless interfaces 'wlan0' and 'wlan1', the only two things seemingly capable of wireless, both of these are marked as 'DISABLED' (rather than UNCLAIMED).  I'm not sure if this is the root of my problem, since blacklisting ssb didn't solve my problems.


*-network:0  DISABLED
   description:  Wireless interface
   physical id:  1
   logical name: wlan0
   serial:       00:98:4b:ea:0c:7e
   capabilities: ethernet physical wireless
   configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

*-network:1  DISABLED
   description:  Wireless interface
   physical id:  2
   logical name: wlan1
   serial:       00:0f:66:3c:8e:94
   capabilities: ethernet physical wireless
   configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


I don't even know if those are related -- the other outputs that came before that seemed more like what the document was talking about, but again, the blacklisting didn't seem to help any.

---

### Post by bobnutfield on 2008-09-18
If you are using ndiswrapper, and I am assuming you are if you went through posted tutorial, have you verified that the drivers are loaded and the device is present:

> sudo ndiswrapper -l

If so, please post the results.

---

### Post by Parhelion on 2008-09-18
lsbcmnds:  driver installed
    device (14E4:4320) present (alternate driver: ssb)

---

### Post by bobnutfield on 2008-09-18
Try these commands:

> sudo ifconfig wlan0 up
> sudo iwconfig wlan0 essid <the name of your network>
> sudo iwconfig wlan0 key <your encryption key if you use one>
> dhclient wlan0

If it give you an IP address you are good to go.  If not post back.

---

### Post by Parhelion on 2008-10-03
Got this resolved, after two weeks of meddling that included 3 ubuntu installs and the discover that Fedora truly does suck (in that it flips out on my laptop).

For anyone perusing the threads with similar problems, I got the Broadcom 4306 (which was my old Linksys PCI card mentioned in the OP) to work after:

1.)  Installing Ubuntu 8.10   (which apparently has greater wireless support)

2.)  Installing the package "bcm43xx-fwcutter" and ndiswrapper and following blacklisting instructions found in this thread, posting by pytheas22:  [http://ubuntuforums.org/showthread.php?t=935259](http://ubuntuforums.org/showthread.php?t=935259)

3.)  Restarting.

I must say I am very pleased.

---

