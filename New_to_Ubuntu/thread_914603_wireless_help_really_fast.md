---
title: "wireless help really fast"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by corevette on 2008-09-09
i just installed ubuntu on my new box and the only wireless card i have is a usb adapter (d-link wua-1340)
it recognizes wireless networks, but once you try and connect, neither circle is filled in in the network applet in the panel.
if i try and connect to my unencrypted wireless network, all it does is turn off the internet to everyone in the house
i'm running ubuntu 8.04 hardy heron
any help?
i have done no configuration to the card at all...all defaults out of the box

---

### Post by pytheas22 on 2008-09-09
That's strange behavior and sounds like a problem with the wireless driver (quite a serious problem if it's breaking the router somehow).  Please open a terminal (Applications>Accessories menu), run this command and post the output here:
```

lsusb
```

With that information we can tell you how to install a better driver.

---

### Post by corevette on 2008-09-09
```
corey@corey-server:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 07d1:3c04 D-Link System
Bus 001 Device 002: ID 2525:8911
Bus 001 Device 001: ID 0000:0000
```

---

### Post by corevette on 2008-09-09
let me put the situation in a different perspective.
i have 3 computers with ubuntu hardy that connect to our 2Wire HomePortal SW,
1) is a desktop with a pci Netgear WG311T wireless card and works perfectly with the router.
2) the other two (a d-link wua-1340 and some wireless adapter built into a toshiba satellite notebook) are able to scan for wireless networks, but when they try to connect to our 2wire homeportal, the homeportal loses internet functionality and everyone loses internet in the house.
is it the router? all other mac/pc's/my desktop with WG311t work fine

---

### Post by bobnutfield on 2008-09-09
In reading other forums about this wireless chipset, Linux attempts to use the RT73 module, but it does not work and others have resorted to using ndiswrapper which apparently does work,  Are you using ndiswrapper?  You might give that a shot.

---

### Post by pytheas22 on 2008-09-09
As the poster above says, your card has an rt73 chipset.  There are two versions of drivers for it, and the ones that ship with Ubuntu are newer and not always stable.  It might help to switch to the older but more reliable legacy drivers.  You can do that by running these commands:

```
sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
apt-get install build-essential
wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
tar -xzvf rt73*
cd rt73*
cd Module
make
make install
```

Now reboot and see if the wireless works better.  If not, please post the output of:
```

lshw -C Network
iwconfig
```

---

### Post by corevette on 2008-09-10
> **pytheas22 said:**
> As the poster above says, your card has an rt73 chipset.  There are two versions of drivers for it, and the ones that ship with Ubuntu are newer and not always stable.  It might help to switch to the older but more reliable legacy drivers.  You can do that by running these commands:

```
sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
apt-get install build-essential
wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
tar -xzvf rt73*
cd rt73*
cd Module
make
make install
```

Now reboot and see if the wireless works better.  If not, please post the output of:
```

lshw -C Network
iwconfig
```

here's the output of iwconfig:
```
wlan0
RT73 WLAN ESSID:"FarWireless"
Mode:Managed Frequency=2.437 GHz Access Point: 00:D0:9E:E9:44:71
Bit Rate=11 Mb/s
RTS thr:off Fragment thr:off
Link Quality=79/100 Signal level:-60 dBm Noise level:-99 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid msc:0 Missed beacon 0
```

i see the same results (internet turns off for everyone in the house momentarily)

---

### Post by corevette on 2008-09-10
> **bobnutfield said:**
> In reading other forums about this wireless chipset, Linux attempts to use the RT73 module, but it does not work and others have resorted to using ndiswrapper which apparently does work,  Are you using ndiswrapper?  You might give that a shot.

and no..i have not/never tried ndiswrapper before...but i know what it is

---

### Post by pytheas22 on 2008-09-10
Sorry it's still not working.  Please post the output of:
```

lsmod | grep rt
lshw -C Network
```

---

### Post by corevette on 2008-09-11
> **pytheas22 said:**
> Sorry it's still not working.  Please post the output of:
```

lsmod | grep rt
lshw -C Network
```

```
corey@corey-server:~$ lsmod | grep rt
rt73                  216320  0 
rt73usb                27136  0 
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                34760  1 intel_agp
usbcore               146028  6 usbhid,rt73,rt73usb,rt2x00usb,uhci_hcd
corey@corey-server:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth1
       version: 00
       serial: 00:09:5b:1a:24:2e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=32 link=no maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:e9:88:77:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
corey@corey-server:~$ 

```

hope this helps :-)

---

### Post by corevette on 2008-09-11
i just tried both my ubuntu and kubuntu 8.04.1 live cd's on my toshiba satellite m105-s3041 and the same thing happens where when i try to connect it just get stuck and doesn't connect and the internet goes down for everyone...so i'm definitely thinking it's my router, but this event only happens when i'm on *ubuntu, but the internet works fine for me with my netgear wg311t pci wireless card on my desktop (not the same as the one with the dlink)

---

### Post by pytheas22 on 2008-09-11
The card is still being driven by the old, more unstable drivers, for some reason (maybe they didn't get blacklisted).  Please try running these commands:

```
sudo modprobe -r rt73usb rt2x00usb rt2x00lib rt73
sudo modprobe rt73
```

Do things work better now?  If not, what is the output of:
```

lsmod | grep rt
```

I do still suspect that the problem is the driver you're using, not your router.

---

### Post by skippuff54 on 2008-09-11
u might also want to try assigning IP addresses in ur router config. sometimes the router will try to assign addresses before the signal gets strong enough, or somethin quirky like that, and the computers end up fightin each other for connectivity.

another less likely issue is that u have to get ur ISP to allow u additional IP addresses...but if all of ur network is behind one IP address assigned to the router that shouldn't matter.

did u try just cuttin the other machines off while u get urs hooked up?

---

### Post by skippuff54 on 2008-09-11
also have u power cycled ur router and modem recently?

---

### Post by corevette on 2008-09-11
> **pytheas22 said:**
> The card is still being driven by the old, more unstable drivers, for some reason (maybe they didn't get blacklisted).  Please try running these commands:

```
sudo modprobe -r rt73usb rt2x00usb rt2x00lib rt73
sudo modprobe rt73
```

Do things work better now?  If not, what is the output of:
```

lsmod | grep rt
```

I do still suspect that the problem is the driver you're using, not your router.

here's the results:

```
corey@corey-server:~$ sudo modprobe -r rt73usb rt2x00usb rt2x00lib rt73 
[sudo] password for corey: 
corey@corey-server:~$ sudo modprobe rt73
corey@corey-server:~$ lsmod | grep rt
rt73                  216320  1 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
agpgart                34760  1 intel_agp
iTCO_vendor_support     4868  1 iTCO_wdt
usbcore               146028  4 rt73,usbhid,uhci_hcd
corey@corey-server:~$ 

```

nothing changed network wise

how do you power clean a router?

---

### Post by skippuff54 on 2008-09-11
> **corevette said:**
> how do you power clean a router?

turn off all your computers, unplug the router, unplug the modem....wait a couple mins, plug the modem back in, wait a couple mins, plug the router back in, wait a couple mins, turn the comp back on.

try turning on just the computer in question first, see if it works by itself without any of the other computers attempting to get an IP address.

also before u turn on the other computers, do in terminal ```
sudo ifconfig
``` and ```
sudo iwconfig
```

to test your network interfaces and wireless interfaces, respectively

also look in /etc/network/interfaces to make sure ur wireless interface is listed. use a text editor or do in terminal ```
sudo nano /etc/network/interfaces
```

another file to check is /etc/resolv.conf, that tells ur network services where to look for DNS nameservers

---

