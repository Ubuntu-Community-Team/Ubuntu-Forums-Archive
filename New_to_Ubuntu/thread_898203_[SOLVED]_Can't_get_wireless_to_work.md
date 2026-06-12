---
title: "[SOLVED] Can't get wireless to work"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by misswham on 2008-08-23
I have a laptop that wont pic up signal to my linksys router.  It works fine when I booted with XP but not in Ubuntu.  I would cut the wireless button to green and it would find the signal everytime, but not with Ubuntu.  It says it is a wireless 802.11g, mobile amd sempron 2800+

Can You Help?

---

### Post by balagosa on 2008-08-23
just to let us know what drivers are needed for your Wireless, please post the outcome of **lspci**

---

### Post by misswham on 2008-08-23
I am lost.  I dont know what u mean.  How do I know where to find what drivers  are needed?  I am new at this.

---

### Post by porchrat on 2008-08-23
please copy and paste this into your console so that we know what wireless card you are running

```
sudo lshw -C network
```

Then copy and paste what the console prints out into a post here on the forum.

(you can find the console under Applications --> Accessories --> Terminal)

---

### Post by misswham on 2008-08-24
this is what came up

*-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wmaster0
       version: 01
       serial: 00:11:09:0b:15:55
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:26:5c:0a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.15.102 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

---

### Post by david sousa on 2008-08-24
Well you can use Windows wireless drivers like me.

First type lspci at the console to know you wireless card.

The last line of the output says: "Network controller: blah blah" ---> blah blah is your type of wireless card.

And [Here]("https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html") you have this instructions to get it working! 

good luck ;)

---

### Post by wyattno26 on 2008-08-24
Hello,I want to know the ubuntu8.0.4 can contact to the wireless network
builded by windows vista directly? it can list the  wireless networks correctly ,but the signal is always 0 %!
thank you!

---

### Post by porchrat on 2008-08-24
your wireless card is a RT2500.

I found a link with the linux drivers for it here:

[http://www.ralinktech.com/ralink/data/RT2500-Linux-STA-1.4.6.6.tar.gz]("http://www.ralinktech.com/ralink/data/RT2500-Linux-STA-1.4.6.6.tar.gz")

However before you download and install that see if you can see a wireless connection under System --> administration --> Network

Also see if you can see a wireless device (you'll see a device called eth0, another called lo and another which should be your wireless device) when you type this into the console:

```
ifconfig
```

(wouldn't hurt to copy and paste the output from that command here on the forum either)

---

### Post by misswham on 2008-08-24
I got it working. I really dont know what I did but it did work. Thanks again so much.

---

### Post by david sousa on 2008-08-24
keep enjoying ;)

---

