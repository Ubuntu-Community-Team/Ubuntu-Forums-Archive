---
title: "TP-Link TL-WN727N can't use wireless"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by Anime4000 on 2012-01-25
recently I just buy TL-WN727N USB wireless, because my internal wireless "Broadcom Corporation BCM43225 802.11b/g/n (rev 01)" driver not found, so I had to buy. Once I plug and wait 1 minute seem nothing, I had run terminal it is installed or not:
```
root@nx:~/Desktop/RT5370# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

here my usb list:
```
root@nx:~/Desktop/RT5370# lsusb
Bus 002 Device 004: ID 0489:e010 Foxconn / Hon Hai 
Bus 002 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:c052 Logitech, Inc. 
Bus 001 Device 004: ID 05e3:0718 Genesys Logic, Inc. IDE/SATA Adapter
Bus 001 Device 003: ID 04fc:2801 Sunplus Technology Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

ok, I found that my wireless use RT5370 chisets, so I download and run ```
make
make install
modprobe rt5370sta
```

at "make install" output:
```
root@nx:~/Desktop/RT5370# make install
make -C /root/Desktop/RT5370/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/root/Desktop/RT5370/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /root/Desktop/RT5370/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.39.4/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.39.4/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.39.4
make[1]: Leaving directory `/root/Desktop/RT5370/os/linux'
```

at "modprobe" I got this error:
```
root@nx:~/Desktop/RT5370# modprobe rt5370sta
FATAL: Error inserting rt5370sta (/lib/modules/2.6.39.4/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

now my 2 wireless not working :( 
I had to use LAN cable to order working online :(

---

### Post by Anime4000 on 2012-01-26
anyone? I spend 1 day to find solution, now both internal and usb wireless not work,

---

### Post by Anime4000 on 2012-01-26
Since no one replay, I keep find solution, then I discover my self, my TL-WN727N are Ver: 3.0, newest chipset (RT5370) and it compatible with driver rt2800usb via Linux Wireless (compact-wireless)

My USB hardware
```
root@nx:~/Desktop/RT5370# lsusb
Bus 002 Device 004: ID 0489:e010 Foxconn / Hon Hai 
Bus 002 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:c052 Logitech, Inc. 
Bus 001 Device 004: ID 05e3:0718 Genesys Logic, Inc. IDE/SATA Adapter
Bus 001 Device 003: ID 04fc:2801 Sunplus Technology Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

At Linux Wireless page, ID 148f:5370 dose not exist in list, but driver compatible with previous TL-WN727N Version.

TP-Link might not sell and older version TL-WN727N, so this might useful what I experience.

What I did:
I download latest compact wireless at: [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

Extract and open Terminal/Console
```
root@nx:~# cd Downloads/compact-wireless-3.3-rc1-2
root@nx:~Downloads/compact-wireless-3.3-rc1-2# ./scripts/driver-select rt2x00
```

then I run this on terminal
```
make
make install
modprobe rt2800usb
```

In my experience using this compact wireless much far better then use Ralink driver, once I modprobe rt5370sta I can't even connect wifi then I check what driver are use via airmon-ng, what I see it use RT2600 PCI driver, so I think Ralink might make mistake.

---

