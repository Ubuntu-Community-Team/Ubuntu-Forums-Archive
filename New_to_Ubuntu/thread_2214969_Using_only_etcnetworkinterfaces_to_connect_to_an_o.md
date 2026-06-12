---
title: "Using only /etc/network/interfaces to connect to an open, hidden wireless network"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by frank41 on 2014-04-04
I use Ubuntu on my laptop and have a list of wireless networks I need to connect to in my /etc/network/interfaces file.  I just comment out everything except the one I need to connect to at that time.  I have a new place I am currently needing to connect to.  It is an open wireless network, but the ssid is hidden (not broadcasted).  I am unable to connect to this network using the following:

# Open Network Wifi
wireless-essid "COMMANDOS"
wireless-mode managed

From my searches, all I can find is the following:

wpa-scan_ssid 1

but this isn't working, as I think it only works with wpa_supplicant.conf.

How can I do this without having to use wpa_supplicant.conf?

---

### Post by Kris_Spencer on 2014-04-04
Try adding:

HIDDEN=yes

---

### Post by frank41 on 2014-04-04
When I add that line to /etc/network/interfaces I get:

/etc/network/interfaces:37: option with empty value
ifup: couldn't read interfaces file "/etc/network/interfaces"

---

### Post by Kris_Spencer on 2014-04-05
Ah, we may be refering to two different things that can be found in the /etc/network directory. I was thinking you were working with a network profile used with something like the netctl network manager. So that file would read like this:

CONNECTION='wireless'
DESCRIPTION='An open wireless connection'
INTERFACE='wlan0'
SECURITY='none'
ESSID='TheSSIDhere'
IP='dhcp'
HIDDEN=yes

Sorry for the confusion.

---

### Post by frank41 on 2014-04-05
So I guess what nobody is saying is that I can't use /etc/network/interfaces to connect to an open hidden network?

---

### Post by steeldriver on 2014-04-05
Maybe I'm misunderstanding but if you are specifying the SSID it shouldn't matter whether it is hidden or not? What is the actual error message when you try to connect (should be something in dmesg)?

If this is a desktop installation is there any particular reason you are using the networking service (/etc/network/interfaces) instead of network-manager (via the nm-applet / nm-connection editor GUI)?

---

### Post by frank41 on 2014-04-06
I don't exactly get an error, it just doesn't connect.

shecky@rebecca:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client 4.2.2
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/f1:f1:f1:f1:f1:f1
Sending on   LPF/wlan0/f1:f1:f1:f1:f1:f1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
shecky@rebecca:~$

the only thing in dmesg is:

[ 3729.319987] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by steeldriver on 2014-04-06
Well the fact that it's broadcasting DHCPDISCOVERs suggests it's got at least as far as associating with an access point - have you confirmed that it's the one (with the hidden SSID) that you are trying to connect to? There should be something in the dmesg log indicating (by MAC) the AP it's associated to

```
dmesg | grep wlan0
```

If it's associating to the correct SSID then the problem is downstream of that (i.e. that it's simply not getting a DHCPOFFER from the hidden network).

---

### Post by frank41 on 2014-04-06
> **steeldriver said:**
> Well the fact that it's broadcasting DHCPDISCOVERs suggests it's got at least as far as associating with an access point - 

I don't know if that's true, because if I try to use an access point that doesn't exist I still get the same results.  So I don't think it IS associating with an access point.

---

