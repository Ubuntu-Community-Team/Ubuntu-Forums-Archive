---
title: "Wireless Internet goes weird"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Darkshrimp on 2008-05-14
I've installed ubuntu 6.10 on my laptop. 

I tried it out at my gf's house, and the wireless worked perfectly, i didn't even need to edit any settings and it worked.

once i got home, the net doesn't seem to work. Although the signal strength says 100%, the internet just doesn't work

Right now, google works, i can search for things, but nothing else works, no websites works. and Gaim doesn't work either. 

What's with that ?

---

### Post by prshah on 2008-05-14
> **Darkshrimp said:**
> I've installed ubuntu 6.10 on my laptop. 

I tried it out at my gf's house, and the wireless worked perfectly, i didn't even need to edit any settings and it worked.
once i got home, the net doesn't seem to work. 
Right now, google works, i can search for things, but nothing else works, no websites works. and Gaim doesn't work either. 
What's with that ?

I'd guess a DNS error; google may work since the ip address for it may be cached.

Try restarting the network```
sudo /etc/init.d/networking restart
```

---

### Post by ubunu on 2008-05-14
> **Darkshrimp said:**
> , google works, i can search for things,. 

What's with that ?

Does google return data from a search query?

---

### Post by Michael.Godawski on 2008-05-14
Can you please post the output from these commands:

```
cat /etc/network/interfaces
iwconfig
sudo lshw -C network
```

---

### Post by Darkshrimp on 2008-05-14
**To ubuntu**, yea it return results

-------------------------
**To Michael.Godawski**..
```
andu@andu-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




iface eth1 inet dhcp
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid default

auto eth1
andu@andu-laptop:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:64:D4:58   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-33 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:10

andu@andu-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:e2:02:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.100 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d0001000-d0001fff irq:10
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 10
       serial: 00:40:d0:77:3e:c1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:a100-a1ff iomemory:d0000b00-d0000bff irq:10
andu@andu-laptop:~$ 

```

---

