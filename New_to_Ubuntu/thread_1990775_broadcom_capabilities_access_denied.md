---
title: "broadcom capabilities access denied?"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by odrin on 2012-05-29
when I use the  
 
lspci -vnn -d 14e4:

it returns


Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 40000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: wl, ssb

Im assuming part of why i can't get my wireless card to work is under capabilities it says <access denied>

any help, please?

---

### Post by williejones on 2012-05-29
Try to load the b43 driver

```
sudo apt-get update
sudo apt-get firmware-b43-installer 
sudo modprobe b43
```

---

### Post by TBABill on 2012-05-29
```
sudo apt-get purge bcmwl-kernel-source
```Then ```
sudo modprobe -r wl
```Then ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Then ```
sudo modprobe b43
```Wait a few moments and try to connect again.

---

### Post by odrin on 2012-05-29
thank you, i think purging the old bcmwl did the trick

---

### Post by TBABill on 2012-05-30
Outstanding. Could you click up in the thread tools to mark the thread solved? That helps others when searching for a solution to a problem and seeing [SOLVED] provides a level of confidence that the solution provided actually works for that specific problem.
 
Best regards...

---

