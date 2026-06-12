---
title: "belkin wireless usb stick help"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by endrswrd on 2008-10-25
Using ndiswrapper i was able to install the drivers for the stick. But when i plug it in. It lights up, but doesn't work, and it make my ethernet connection no longer works either. so anytime i plug it in. It pretty much makes my computer internetless

---

### Post by melojo on 2008-10-25
open a terminal and type 
```
lshw -C network
```
post the output

---

### Post by endrswrd on 2008-10-25
it doesnt produce any output but i cant exactly plug in the usb stick because when i do my whole OS becomes very weird and doesnt operate correctly. My computer doesnt even shut down the same way if i plug it in. Even if i take it out. it still behaves odd

---

### Post by eolson on 2008-10-25
uninstall the drivers and see what happens.   My Belkin USB stick works without any external drivers.

---

### Post by endrswrd on 2008-10-25
nope nothing. Im in the process of using serial monkeys rt73 drivers. but no success so far.

---

### Post by C.S.Cameron on 2008-10-26
I have 3 Belkin F5D7050 wireless USB, they all work out of the box.
I just plug them in and select the network.

---

### Post by 11hjpphty76lkjj on 2008-10-26
My F5D7050 was working (Intrepid) but after the last update it's not working and in the syslog I'm getting:

```

Oct 26 08:58:42 coreprime kernel: [  441.206717] usb-storage: waiting for device to settle before scanning
Oct 26 08:58:44 coreprime NetworkManager: <info>  (wlan1): device state change: 1 -> 2 
Oct 26 08:58:44 coreprime NetworkManager: <info>  (wlan1): bringing up device. 
Oct 26 08:58:44 coreprime kernel: [  443.604613] firmware: requesting zd1211/zd1211b_ub
Oct 26 08:58:44 coreprime kernel: [  443.608615] usb 1-2.1: Could not load firmware file zd1211/zd1211b_ub. Error number -2
Oct 26 08:58:44 coreprime kernel: [  443.608633] zd1211rw 1-2.1:1.0: couldn't load firmware. Error number -2
Oct 26 08:58:44 coreprime firmware_helper[6549]: main: error loading '/lib/firmware/zd1211/zd1211b_ub' for device '/class/firmware/1-2.1' with driver 'usb'
Oct 26 08:58:45 coreprime NetworkManager: <WARN>  nm_device_hw_bring_up(): (wlan1): device not up after timeout! 
Oct 26 08:58:45 coreprime NetworkManager: <info>  (wlan1): deactivating device (reason: 2). 
Oct 26 08:58:45 coreprime kernel: [  443.627701] firmware: requesting zd1211/zd1211b_ub
Oct 26 08:58:45 coreprime NetworkManager: <info>  (wlan1): device state change: 2 -> 3 
Oct 26 08:58:45 coreprime firmware_helper[6552]: main: error loading '/lib/firmware/zd1211/zd1211b_ub' for device '/class/firmware/1-2.1' with driver 'usb'
Oct 26 08:58:45 coreprime kernel: [  443.635962] usb 1-2.1: Could not load firmware file zd1211/zd1211b_ub. Error number -2
Oct 26 08:58:45 coreprime kernel: [  443.635980] zd1211rw 1-2.1:1.0: couldn't load firmware. Error number -2
Oct 26 08:58:45 coreprime NetworkManager: <info>  (wlan1): supplicant interface state change: 1 -> 2. 
Oct 26 08:58:47 coreprime kernel: [  446.205328] usb-storage: device scan complete

```

```

lsusb

...
Bus 001 Device 018: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter
...


```

Ideas?

Aaron

---

### Post by 11hjpphty76lkjj on 2008-10-26
```

aaron@coreprime:~$ sudo lshw -C network 
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:3a:2b:33:b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.102 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:f8:ae:9e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:17:3f:4f:b9:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by C.S.Cameron on 2008-10-26
Mine seem to be working fine with 8.10 so far, (knock on wood).
Have you tried it booting from the Live CD?

---

### Post by Kevbert on 2008-10-26
Please take a look at these two links. If the [[COLOR="Red"]first one[/COLOR]]("http://ph.ubuntuforums.com/showthread.php?t=743299") doesn't work try the [[COLOR="Red"]second[/COLOR]]("http://ph.ubuntuforums.com/showthread.php?t=792158") (Atheros wireless can be a bit of a problem with Ubuntu).

---

