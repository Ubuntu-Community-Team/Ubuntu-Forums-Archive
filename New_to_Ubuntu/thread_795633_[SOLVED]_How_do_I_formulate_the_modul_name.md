---
title: "[SOLVED] How do I formulate the modul name?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Tuning_In on 2008-05-15
Hi!

I have installed Linux Mint on my mothers laptop. The laptop is an old 
Fujitsu Siemens Amilo Pro V2000. 

I'm trying to get the wireless network up during boot but with no luck.
I have tried to follow the same procedure as described in [this thread]("http://ubuntuforums.org/showthread.php?t=101989&highlight=amilo+pro+v2000"). I can connect to the internet doing the "sudo modprobe fsam7400 radio=1" command, but I cannot connect automaticly after boot.

In Mr_Smiley's post he says that you can "add the module name you want to load automatically at boot". This may be a dumb question but how do I formulate the module name? I have tried eth1 and ipw2200 but with no luck

If this is relevant I get this output doing 
sudo lshw:
 ```
*-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 6
                bus info: pci@0000:02:06.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:90:58:01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=xxxxxxx latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

```

Thanks in advance:)

---

### Post by Tuning_In on 2008-05-15
Found [this guide]("http://odzangba.wordpress.com/2007/05/15/intel-corporation-prowireless-2200bg-amilo-pro-v2000-ubuntu/") and it's working now:)

---

