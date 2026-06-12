---
title: "WiFi not connecting to internet"
date: 2015-05-08
forum: New to Ubuntu
---

### Post by Cheshire_Shroom on 2015-05-08
Hello,

New to Ubuntu. Running 14.04 LTS on an Acer Aspire 5560. After some troubleshooting... I was able to install ubuntu WITHOUT a dualboot option for Windows 7(which came pre-installed.)

I have been browsing the forums for a few days, and can't find anything to fix this issue (I'm also having trouble with ANY USB devices being recognized... something I'll post about later.)

I should go to say that whatever I did to try and trouble shoot my USB issues, now when I lsusb, it returns nothing. Not sure if this is relevant to address my WiFi issues, but it's a new problem. My Wireless card is internal. I know I'm connecting to my router, but can't connect to the internet beyond this.

Please help?

---

### Post by Bucky Ball on 2015-05-09
Welcome. Please open a terminal and:

```
sudo lshw -C network
```

Post the output here. Please post a new thread regarding your USB issues. If you have an internal wireless card I'm not sure tweaking with your USB set up is going to change anything about that.

---

### Post by Bucky Ball on 2015-05-09
Welcome. Please open a terminal and:

```
sudo lshw -C network
```

Post the output here. Are you using an IP served from the router or have you set up a static IP locally (on the machine)?

---

### Post by Cheshire_Shroom on 2015-05-09
*-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 20:6a:8a:71:34:e5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=sb ip=10.0.0.16 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:11 memory:f0000000-f000ffff memory:f0010000-f001ffff memory:b0000000-b00007ff
  *-network
       description: Wireless interface
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 7c:e9:d3:1f:c4:35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=10.42.0.1 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:11 memory:f0100000-f0103fff

---

### Post by Bucky Ball on 2015-05-09
Try the instructions for installing the STA driver and blacklisting any open-source ones top of the page [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29").

Looks like it may be a problem with how you are configuring your connection, though, but see if it's the same after the above.

Once again, are you using an IP served by the router or do you have a static IP set up for your machine?

---

### Post by Cheshire_Shroom on 2015-05-12
*-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 20:6a:8a:71:34:e5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=sb ip=10.0.0.16 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:11 memory:f0000000-f000ffff memory:f0010000-f001ffff memory:b0000000-b00007ff
  *-network
       description: Wireless interface
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 7c:e9:d3:1f:c4:35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:11 memory:f0100000-f0103fff


I am connecting through a router(DHCP)

---

### Post by Cheshire_Shroom on 2015-05-12
Oh sorry, yes I followed the instructions from your link. Using DHCP through the router.

---

### Post by Cheshire_Shroom on 2015-05-12
Here is the output after connecting to the router, but no internet access when I disconnect the cable.
  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 20:6a:8a:71:34:e5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=sb ip=10.0.0.16 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:11 memory:f0000000-f000ffff memory:f0010000-f001ffff memory:b0000000-b00007ff
  *-network
       description: Wireless interface
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 7c:e9:d3:1f:c4:35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:11 memory:f0100000-f0103fff
cheshire@cheshire-Aspire-5560:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:b002 Alcor Micro Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cheshire@cheshire-Aspire-5560:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:b002 Alcor Micro Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cheshire@cheshire-Aspire-5560:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 20:6a:8a:71:34:e5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=sb ip=10.0.0.16 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:11 memory:f0000000-f000ffff memory:f0010000-f001ffff memory:b0000000-b00007ff
  *-network
       description: Wireless interface
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 7c:e9:d3:1f:c4:35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=10.42.0.1 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:11 memory:f0100000-f0103fff

---

### Post by Bucky Ball on 2015-05-12
You may have missed this the first time, but try following the instructions for installing the STA driver and blacklisting any open-source ones top of the page [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29"). It says for 12.04 but will work.

---

### Post by Cheshire_Shroom on 2015-05-14
Yes, I had installed the STA driver per instructions at that page. Since then I've re-installed, followed those instructions a second time, and still have the same issue. Can connect to router, but no internet.

---

### Post by Vladlenin5000 on 2015-05-14
Have you rebooted the router meanwhile? You probably should...

Regarding your USB ports I also answered in your other thread. It shouldn't but it *might* be related.

---

### Post by wildmanne39 on 2015-05-14
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by Cheshire_Shroom on 2015-05-14
I hope this is what you mean, see attached.

---

### Post by wildmanne39 on 2015-05-14
Please go into network manager top right corner of the screen and change ad-hoc to infrastructure then reboot computer.
Let us know if it helps.
Thanks

---

### Post by Cheshire_Shroom on 2015-05-16
I switched to infrastructure and re-booted, but the network didn't save the setting, and had to create a new network. I am able again to connect to the router, but not the internet.
I have re-booted the router at this point.
Somewhere between troubleshooting this issue, and my USB problems, my audio no longer works, either through the speaker or through the headphones.

---

### Post by wildmanne39 on 2015-05-16
Please run and post a new script file now that your network is scanning.
Thanks

---

### Post by Cheshire_Shroom on 2015-05-18
I don't know that the computer was scanning for the ssid, or of thats even a function in ubuntu, or if thats what you meant. I had to manually connect to the wifi each time. Attached new script.

---

### Post by Bucky Ball on 2015-05-19
Without jumping on Wildman's toes, you still have the config set to 'ad-hoc'. You have been asked to change that to 'infrastructure'. Do that and if it doesn't start working, reboot and see if it does.

I'll leave it there for now, with the only other suggestion being that it might pay to set the connection up manually by right clicking network manager and editing the existing connection or creating one with the correct details for your router/access point. Infrastructure, not ad-hoc, and with the correct SSID (unless yours is 'HOME-90D2' which it may well be).

---

### Post by wildmanne39 on 2015-05-19
AD-HOC is still a problem but also the driver you are using has a bug so let's replace it.
```
sudo apt-get remove --purge bcmwl-kernel-source
```
Then download the file below and save it in Downloads:
```
cd ~/Downloads/
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```
Reboot
[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)
Driver found in this post.
[http://ubuntuforums.org/showthread.php?t=2278082&page=2&p=13285215#post13285215](http://ubuntuforums.org/showthread.php?t=2278082&page=2&p=13285215#post13285215)

---

