---
title: "broadcom wireless card"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by William S on 2008-11-08
can anyone please give me a step by step guide to get this thingy working in 8.10? I have tried to get it working every single version since 7.04, and no version have made it work. I can activate wireless, but I cant see any wireless networks. 
Anyone know what to do get it real working I mean you can see wireless networks without any problem. And it is with both the driver from hardware drivers and the bcm3xx-fwcutter firmwire thing (or what it is called) And I am on a HP laptop.

---

### Post by pHreaksYcle on 2008-11-08
Search these forums and/or google for your laptop name + ubuntu + wireless and it should turn up. HP has been a PITA for laptop wireless for idk how long, someone should have the solution already.

---

### Post by Sealbhach on 2008-11-08
Which Broadcom card is it? If you don't know then do:

```
lshw -C network
```

in the terminal. That way we will be able to help you better.


.

---

### Post by William S on 2008-11-08
Hello: 
```
    description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:75:97:67
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes
```

T

---

### Post by Sealbhach on 2008-11-08
Hi, try these commands here:
```

sudo modprobe -r b43 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart
```

For information on waht they mean, you will need to carefully read this thread here and the following pages:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=963978&page=7](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=963978&page=7)

Hope it works. If not, somebody is sure to have a solution.


.

---

### Post by William S on 2008-11-08
Thanks it worked. :)

---

