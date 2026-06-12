---
title: "Internet speed slows dramatically after just a few minutes of use [Ubuntu 14.04]"
date: 2016-03-21
forum: New to Ubuntu
---

### Post by Ryan_Kidd on 2016-03-21
I've recently dual booted Ubuntu 14.04 with Windows 10. Initially on Ubuntu, it will run perfect with a download of ~40MB/S. After around 5 minutes, it slows down to ~2MB/S with a sporadic on/off connection which can dip as low as 10KB/S. This continues until I reboot the laptop, where it will run for another few minutes and then slow. 

This issue is prevalent regardless of browser used or WiFi network connected to. 
There are no issues on the Windows 10 partition, which maintains a steady ~40MB/S.

If helpful, running the command: 
```
[COLOR=#000000]*sudo lshw -C network*[/COLOR]

```

gives the output: 

*-network               
       description: Wireless interface
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 03
       serial: ac:d1:b8:c0:94:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.15 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:f7200000-f7207fff memory:f7000000-f71fffff

---

### Post by DuckHook on 2016-03-22
Welcome to the forums, Ryan.

My info gets more out of date as I get older, but FWIW you have a Broadcom WIFI chipset that is often problematic when it comes to Linux. Broadcom doesn't release their HW specs to the Linux community, so there is no real open source driver for their chips. Most drivers are a Frankenstein's monster consisting of partial open source code bound to a binary firmware blob from Broadcom. The result is often predictably wonky. In your case, the STA driver that you have installed is entirely proprietary, so no idea what is happening in the guts of the driver.

[This]("http://ubuntuforums.org/showthread.php?t=2283001&page=1") thread might help. When it comes to Broadcom, anything posted by *chili555* is worth reading. In particular, you may want to look at signal strength/quality just like the OP of aforementioned thread did.

As something of an aside: I have a number of old laptops all of which used the Broadcom chips. Out of sheer cussedness, I used to wrestle with them after every upgrade. It finally dawned on me that I could replace the bloody Broadcom chip with an Atheros, or something else that was properly supported, and all of my problems would go away. That's what I've done, and I now largely avoid the Broadcom garbage. For less than $20, a cheap solution to my headaches.

---

### Post by kurt18947 on 2016-03-25
> **DuckHook said:**
> Welcome to the forums, Ryan.

...................................
As something of an aside: I have a number of old laptops all of which used the Broadcom chips. Out of sheer cussedness, I used to wrestle with them after every upgrade. It finally dawned on me that I could replace the bloody Broadcom chip with an Atheros, or something else that was properly supported, and all of my problems would go away. That's what I've done, and I now largely avoid the Broadcom garbage. For less than $20, a cheap solution to my headaches.

Unless the manufacturer whitelists the wifi adapters that its BIOS supports. Lenovo Thinkpad, I'm looking at you.

---

### Post by Geoffrey_Arndt on 2016-03-25
If nothing else forthcoming . . . . this is a known solution (Panda is Ubuntu friendly) (prices from $10 to $25 usd or so):      [http://www.pandawireless.com/](http://www.pandawireless.com/)

---

