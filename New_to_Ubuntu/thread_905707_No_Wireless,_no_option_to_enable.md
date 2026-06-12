---
title: "No Wireless, no option to enable"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-08-30
Yeah as it says, I have no wireless option to enable and I also don't have a wireless connection. Also on a side note... apparently there's no longer any support for my ATI Graphics card... b/c when I say enable it tells me that it doesn't exist.

---

### Post by stalkingwolf on 2008-08-31
you may have to go the ndiswrapper route to install a driver
for your wifi adapter.  What kind is it?  Are we talking desktop
or laptop?

You might try envy for your ATI card.  I hear that is the trick for nvida and ati cards.

---

### Post by tangibleorange on 2008-08-31
> **133794m3r said:**
> Yeah as it says, I have no wireless option to enable and I also don't have a wireless connection. Also on a side note... apparently there's no longer any support for my ATI Graphics card... b/c when I say enable it tells me that it doesn't exist.

for the wireless, could you post the output of:

```
iwconfig
sudo iwlist scan
lshw -C network
```

---

### Post by 133794m3r on 2008-08-31
this is old now.... I used the fr whatever..... and it's all good now....

---

### Post by lanceh13 on 2008-09-17
I'm going to hijack this thread...hope you don't mind...here is my code 

```

lance@lance-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lance@lance-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lance@lance-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:13:d4:22:a4:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.105 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes


```

---

