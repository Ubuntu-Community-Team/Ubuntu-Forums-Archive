---
title: "Wireles Internet Dropping?!"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by caiphn on 2008-11-12
Hello;

I installed Ubuntu 8.10 today. I am using a USB wireless adaptor which Ubuntu detected right away. I am connecting to the router in my home, and everything works fine, in the top right beside the date the bars representing the wireless network appear and everything seems to work fine... until... I start browsing around the Internet or start downloading media-plug ins, etc. and it slows and slows and slows and then stops. In the top right it says it disconnects and the icon disappears, and the light on my USB wireless adaptor disappears. When I restart it works fine, for 10 minutes or so. Other machines in the home work fine, the USB adaptor works fine on other machines. Other USB devices (I am running a external HD and a wireless video game controller adaptor) seem to be working without a problem on the machine in question. Any ideas?! :(

---

### Post by pastalavista on 2008-11-12
Are you sure you have the latest driver for your device? Post the output of:
```
lshw -C network
```

Then make sure all your repositories (software sources) are selected in Synaptic Package Manager]and run

```
sudo apt-get update
```

that is, if you can keep your connection long enough

---

### Post by caiphn on 2008-11-12
echo@echo-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 12
       serial: 00:15:58:bb:79:78
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:d1:32:82:fa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.64 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: ca:e9:27:dc:93:9f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I'm assuming this is what we're concerned with here:

*-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:d1:32:82:fa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.64 multicast=yes wireless=IEEE 802.11bg

What does this show us about the drivers? Also for repositories I had source as all, is that what needs to occur? I'm doing the updates right now, but I'm guessing it will eventually crap out before they finish. Ok, it did. Do I just keep trying?

---

### Post by caiphn on 2008-11-12
It keeps dropping.. how do I restart it, or do I have to restart the computer each time? I don't know if it's even worth it to keep trying to do the updates as I'm not sure if it keeps a part of the update or not.

---

### Post by caiphn on 2008-11-13
Bump! Please, anyone? I've been doing this for the last 10 hours, I feel insane!:KS

---

### Post by Gausian on 2008-11-13
use the following commands to restart your wifi driver...

stop
```
sudo modprobe -r iwl4965
```

then restart
```
sudo modprobe iwl4965
```

replace "iwl4965" with your driver.

you can also try
```
sudo /etc/init.d/networking restart
```

hope this helps you

---

### Post by nhasian on 2008-11-13
actually i have the iwl4965 intel wifi adaptor that's built into my laptop.  occasionally the wireless internet is dropped.  I dont know why, but I can easily get it back by right clicking on he wifi manager on the top right of the menu bar and removing the checkbox from *enable wireless* I wait about 10 seconds and then put the checkbox back on to re-enable it so it starts working again.

---

### Post by caiphn on 2008-11-13
> **nhasian said:**
> actually i have the iwl4965 intel wifi adaptor that's built into my laptop.  occasionally the wireless internet is dropped.  I dont know why, but I can easily get it back by right clicking on he wifi manager on the top right of the menu bar and removing the checkbox from *enable wireless* I wait about 10 seconds and then put the checkbox back on to re-enable it so it starts working again.

Wifi manager disappears, and this is like clockwork, every 5-10 minutes.

---

### Post by caiphn on 2008-11-13
> **Gausian said:**
> use the following commands to restart your wifi driver...

stop
```
sudo modprobe -r iwl4965
```

then restart
```
sudo modprobe iwl4965
```

replace "iwl4965" with your driver.

you can also try
```
sudo /etc/init.d/networking restart
```

hope this helps you


I haven't used Ubuntu in some time, where do I get a list of what the drivers are named so I know what to put in modprobe?

---

### Post by caiphn on 2008-11-13
How do I find out what driver my usb wireless adaptor is using? Thank-you!

---

