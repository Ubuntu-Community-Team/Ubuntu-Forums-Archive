---
title: "How to connect to internet?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by freelancer85 on 2008-09-23
OK, here is my problem...
I'm totally new to Linux/Ubuntu. My first step after installing Ubuntu was internet connection.
I don't know how to connect, network device is detected and enabled.
What is my next step?
Is it terminal server client? If it is, what should i type in?
Thank you.

---

### Post by pedro_orange on 2008-09-23
Wired network? Wireless?

Are you connecting straight to a modem? Through a router? 

In the top right hand corner by the clock is a tool called Network Manager that you can use to connect to a network if you have the drivers installed.

---

### Post by freelancer85 on 2008-09-23
> **pedro_orange said:**
> Wired network? Wireless?

Are you connecting straight to a modem? Through a router? 

In the top right hand corner by the clock is a tool called Network Manager that you can use to connect to a network if you have the drivers installed.

Computer is connected over switch to wireless device which is connected to anttenna

---

### Post by pedro_orange on 2008-09-23
Try entering this into the terminal:

```
sudo lshw -C network
```

This will list your network devices.

---

### Post by freelancer85 on 2008-09-23
> **pedro_orange said:**
> Try entering this into the terminal:

```
sudo lshw -C network
```

This will list your network devices.

description: Enthernet interface
product: 79c970 [PCnet32 LANCE]
vendor: Advanced Micro Devices [AMD]
physical id: 0
bus info: pci@000:02:00.0
localname: eth0
version: 10
serial: 00:0c:29:4d:8c:cc
width: 32 bits
clock: 33 Mhz
capabilities: bus_master ethernet physicial logical
configuration: broadcast=yes driver=pcnet32 driverversion=1.33 latency=64
link=yes maxlatency=255 mingnt=6 module=pcnet32 multicast=yes

---

### Post by pedro_orange on 2008-09-23
Enter your password :)

sudo stands for super-user do. It temporarily lets you do super user type activities.

---

### Post by freelancer85 on 2008-09-23
> **pedro_orange said:**
> Enter your password :)

sudo stands for super-user do. It temporarily lets you do super user type activities.

OK here it is :)

description: Enthernet interface
product: 79c970 [PCnet32 LANCE]
vendor: Advanced Micro Devices [AMD]
physical id: 0
bus info: pci@000:02:00.0
localname: eth0
version: 10
serial: 00:0c:29:4d:8c:cc
width: 32 bits
clock: 33 Mhz
capabilities: bus_master ethernet physicial logical
configuration: broadcast=yes driver=pcnet32 driverversion=1.33 latency=64
link=yes maxlatency=255 mingnt=6 module=pcnet32 multicast=yes

---

### Post by superprash2003 on 2008-09-23
you said computer is connected over switch to a wifi device??which means it is connected through LAN to the wifi router right?? not WLAN?

---

### Post by freelancer85 on 2008-09-23
> **superprash2003 said:**
> you said computer is connected over switch to a wifi device??which means it is connected through LAN to the wifi router right?? not WLAN?

That's right, it's not WLAN.

---

### Post by pedro_orange on 2008-09-24
Hmmm...that is a strange setup. 
It seems network is indeed working. To the switch anyway.
Try doing an 

```
ifconfig
```

to see if you've got an IP address. (Presuming its DHCP)

I have not really ever tried having a setup like yours. Perhaps you need to setup some kind of proxy to let the switch know to send your Internet request packets to the wifi device.

---

### Post by freelancer85 on 2008-09-24
> **pedro_orange said:**
> Hmmm...that is a strange setup. 
It seems network is indeed working. To the switch anyway.
Try doing an 

```
ifconfig
```

to see if you've got an IP address. (Presuming its DHCP)

I have not really ever tried having a setup like yours. Perhaps you need to setup some kind of proxy to let the switch know to send your Internet request packets to the wifi device.

OK, i did it. The setup procedure goes over pppoeconf command and that's it.. I've found it in help file.
Thank you.

---

