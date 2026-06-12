---
title: "Wireless Connection Issues"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Inxi on 2008-11-28
I am not sure how long am I going to have issues with this.

My wireless is a bit unstable. Once in a while it breaks off. So, Ubuntu starts nagging me. It brings up a window and asks me to input my WEP key. It asks this over and over and over again until the connection becomes stable again, so I really don't know if the connection is good or not without inputting the WEP key over and over.

Sometimes, though, it doesn't do that. When the connection breaks, it says "Your wireless connection has been disabled" or something. When I click on the icon, it shows a list of wireless networks in my area. One of them is the network I need to connect to. But sometimes it's not there. So then I have to do "Connect to Hidden Wireless Network". That works if the connection is fine. Doesn't work if the connection is still broken, and I have to redo it multiple times...

Sometimes it does something even weirder than that.

I visited the settings page and setup my connection with the WEP key and all and I don't know how to keep this from happening. It's very annoying.

---

### Post by Michael.Godawski on 2008-11-28
What version of Ubuntu are you using? What is your wlan card?

Please post the results of these commands:

```
sudo lshw -C network
iwconfig
```

---

### Post by Inxi on 2008-11-28
Ubuntu 8.10
Edimax 802.11g 

 ```
*-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 22
       serial: 00:1a:4d:40:28:d3
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wmaster0
       version: 00
       serial: 00:0e:2e:e3:43:53
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.11.2 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:6f:b6:87:9a:d7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"001601AD0CE2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:01:AD:0C:E3   
          Bit Rate=54 Mb/s   Tx-Power=9 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=93/100  Signal level:-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by maestrobwh1 on 2008-11-28
I have a similar issue with a ralink wireless adapter.  It just seems to "break off" as you put it.  I don't use a security key.  I have a 75 to 100% connection and am 15 feet from the router.

It actually still shows a connection, the internet just dies and hangs.  I can terminate and reestablish a connection and it works.

No other device in my house shows this glitch and I have 4 wireless laptops/computers.

Ralink driver is compiled from the latest one from the site.

Ubuntu Hardy Ralink RT2860

[B]EDIT

Doing 

sudo iwconfig ra0 rate 11M 

made it stable.  Unfortunately the manually compiled driver does not seem to support auto bitrate.  I might be wrong, but higher bitrates are usually more susceptible to interference and such?  Since I only use wireless for net surfing and not file transfers, the 11M seems to be fine.  It is actually faster than the 54M rate.  Go figure.[/B]

---

