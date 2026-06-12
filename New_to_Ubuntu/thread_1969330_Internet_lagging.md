---
title: "Internet lagging"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by BeMyManikin on 2012-04-29
I have a dual boot of ubuntu 11.10 64bit and windows 7.
I had to install windows 7 and override the original ubuntu 11.10 set up I had because windows 7 wouldn't install on my hard drive because it wasn't ntfs and windows couldn't install it on there, so I rewrote the whole thing, then installed ubuntu. Ever since I installed it, the internet has been laggy and cutting out with videos and updates. I have tried reinstalling ubuntu to the hard drive and I still have the same problem.
Here is a list of pings I did:
```
   	 	 	 	 	 	   --- google.com ping statistics ---  
 16 packets transmitted, 14 received, 12% packet loss, time 15036ms  
 rtt min/avg/max/mdev = 21.834/25.711/40.186/5.364 ms  
 

 20 packets transmitted, 19 received, 5% packet loss, time 19035ms  
 rtt min/avg/max/mdev = 21.993/26.385/44.263/6.287 ms  
 

 20 packets transmitted, 19 received, 5% packet loss, time 23082ms  
 rtt min/avg/max/mdev = 21.570/25.973/35.060/4.484 ms  
 

 20 packets transmitted, 20 received, 0% packet loss, time 19028ms  
 rtt min/avg/max/mdev = 20.902/24.485/47.741/5.593 ms  
 

 20 packets transmitted, 20 received, 0% packet loss, time 19026ms  
 rtt min/avg/max/mdev = 21.927/24.723/32.005/3.268 ms  
 

 20 packets transmitted, 19 received, 5% packet loss, time 19027ms  
 rtt min/avg/max/mdev = 20.554/25.231/48.545/6.574 ms  
 

 20 packets transmitted, 16 received, 20% packet loss, time 19045ms  
 rtt min/avg/max/mdev = 21.515/28.106/90.123/16.318 ms  
 

 20 packets transmitted, 19 received, 5% packet loss, time 23095ms
 rtt min/avg/max/mdev = 20.573/23.587/31.546/2.673 ms
  
```
Any help much obliged.

---

### Post by souravc83 on 2012-04-30
Can you go to the terminal and type:
```
iwconfig
```
Please paste the results here, and we might have a better idea.
This will tell us about signal strength and such.

---

### Post by BeMyManikin on 2012-04-30
```
lo        no wireless extensions.

eth0      no wireless extensions.
```
it's a desktop. My brother thinks it might be the network drivers. That ubuntu is constantly switching the network drivers from ubuntu drivers to the windows one, and that's why it's cutting in and out on the internet.

---

### Post by souravc83 on 2012-04-30
That pretty much tells me that you had no internet connection (atleast during the time the iwconfig command ran).

Let's find out what driver your card is using.

Can you type the following command:

```
sudo lshw -C network
```

---

### Post by BeMyManikin on 2012-04-30
ok, here's what it says.
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:ca:c1:b7
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:ce00(size=256) memory:fdeff000-fdefffff memory:fdef8000-fdefbfff

```

---

### Post by BeMyManikin on 2012-06-24
> **souravc83 said:**
> That pretty much tells me that you had no internet connection (atleast during the time the iwconfig command ran).

Let's find out what driver your card is using.

Can you type the following command:

```
sudo lshw -C network
```
Yeah, I said it's wired, not wireless. If I remember correctly Iwconfig is for wireless.

---

