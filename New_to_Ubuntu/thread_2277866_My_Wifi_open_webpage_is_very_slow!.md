---
title: "My Wifi open webpage is very slow!"
date: 2015-05-12
forum: New to Ubuntu
---

### Post by jacky7 on 2015-05-12
my wireless network card is BCM57780&#65292;Computer is Lenovo Y460N ; I tried to install wireless driver. but Ethernet network is extremely fast.why?

---

### Post by Holger_Gehrke on 2015-05-12
> **jacky7 said:**
> my wireless network card is BCM57780&#65292;

No, it isn't. The Broadcom 57780 is a wired Ethernet NIC. To find all network interfaces, use 
```

sudo lshw -class network -sanitize

```
in a terminal. (the '-sanitize' option removes serial numbers, MAC and IP addresses, so the output is ready for posting on forums without giving out more personal information than absolutely necessary). If nothing comes up as 'Wireless interface', you've got a device for which no driver is included.

---

### Post by jacky7 on 2015-05-12
[sudo] password for jack: 
```
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000 [Condor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: [REMOVED]
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-37-generic firmware=39.31.5.1 build 35138 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:44 memory:f9b00000-f9b01fff
  *-network
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 01
       serial: [REMOVED]
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=half firmware=sb v2.07 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 memory:f9a00000-f9a0ffff
```



but webpage slow!!:-#

---

### Post by wildmanne39 on 2015-05-12
Please copy and paste the following commands one line at a time for accuracy:
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Make sure your wired connection is disabled when trying to connect with wifi,
That command should improve the speed a lot.
Reboot

---

### Post by wildmanne39 on 2015-05-12
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by jacky7 on 2015-05-12
> **Wild Man said:**
> Please copy and paste the following commands one line at a time for accuracy:
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Make sure your wired connection is disabled when trying to connect with wifi,
That command should improve the speed a lot.
Reboot


[COLOR=#333333][FONT=tahoma]Thanks for your help!![/FONT][/COLOR]

---

### Post by wildmanne39 on 2015-05-12
Did it fix your issue?

---

### Post by jacky7 on 2015-05-12
> **Wild Man said:**
> Did it fix your issue?

Not yet tested, first thank you. go back tried .

---

### Post by jacky7 on 2015-05-13
> **Wild Man said:**
> Did it fix your issue?

```

jack@Jack:~$ echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi.conf
[sudo] password for jack: 
options iwlwifi 11n_disable=8
jack@Jack:~$ sudo modprobe -rfv iwlwifi
modprobe: FATAL: Module iwlwifi is in use.
jack@Jack:~$ sudo modprobe -v iwlwifi

```

But speed isn't slow.

---

### Post by wildmanne39 on 2015-05-13
Okay, come back if that changes and we will run that command another way.
Thanks

---

### Post by jacky7 on 2015-05-13
> **Wild Man said:**
> Okay, come back if that changes and we will run that command another way.
Thanks

Thanks.

---

