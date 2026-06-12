---
title: "Dell D630 and Broadcom 4311"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by rumblesis on 2013-02-18
I am trying to build a Dell D630 on Ubuntu 12.10.  I have it working on two other machines (HP Pavilions) without issue, but I can't get the wireless card to work on the dell.  
 It has a b43 wireless chip (BCM4311) which has i've had issues connecting with. I have tried several fixes and can't get it working.  Thank goodness the wired lan works!!
 i've installed the correct b43 firmware according the archlinux wiki.  
 checking my modules shows this:
 tom@tom-D630:~$ lspci -vnn -d 14e4: 
 09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02) 
     Subsystem: Dell Device [1028:01f9] 
     Flags: bus master, fast devsel, latency 0, IRQ 45 
     Memory at f1ef0000 (64-bit, non-prefetchable) [size=64K] 
     Expansion ROM at <ignored> [disabled] 
     Capabilities: <access denied> 
     Kernel driver in use: tg3 
     Kernel modules: tg3 
  
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) 
     Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007] 
     Flags: bus master, fast devsel, latency 0, IRQ 17 
     Memory at f1ffc000 (32-bit, non-prefetchable) [size=16K] 
     Capabilities: <access denied> 
     Kernel driver in use: b43-pci-bridge 
     Kernel modules: wl, ssb 
 tom@tom-D630:~$ sudo rmmod ssb 
 ERROR: Module ssb is in use by ssb_hcd 
 tom@tom-D630:~$ sudo rmmod b43 ssb bcma 
 ERROR: Module b43 does not exist in /proc/modules 
 ERROR: Module ssb is in use by ssb_hcd 
 ERROR: Module bcma is in use by brcmsmac 
 tom@tom-D630:~$  
 


 tom@tom-D630:~$ lshw -C network 
 WARNING: you should run this program as super-user. 
   *-network                
        description: Network controller 
        product: BCM4311 802.11b/g WLAN 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:0c:00.0 
        version: 01 
        width: 32 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list 
        configuration: driver=b43-pci-bridge latency=0 
        resources: irq:17 memory:f1ffc000-f1ffffff 
   *-network 
        description: Ethernet interface 
        product: NetXtreme BCM5755M Gigabit Ethernet PCI Express 
        vendor: Broadcom Corporation 
        physical id: 0 
        bus info: pci@0000:09:00.0 
        logical name: eth0 
        version: 02 
        serial: 00:1c:23:3c:37:3a 
        size: 1Gbit/s 
        capacity: 1Gbit/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=5755m-v3.29 ip=172.34.56.100 latency=0 multicast=yes port=twisted pair speed=1Gbit/s 
        resources: irq:45 memory:f1ef0000-f1efffff 
 WARNING: output may be incomplete or inaccurate, you should run this program as super-user. 
 


 If I go to the additional drives module, I get this: See attached screenshot

 Using Broadcom 802.11 Linux STA wireless drivers from bcmwl-kernel-source (proprietary)


 Can anyone help me go in the right direction?  
 Brenda

---

### Post by Otto-C on 2013-02-18
Take a look at:

[https://codeghar.wordpress.com/2012/07/12/get-broadcom-bcm4311-working-in-ubuntu-12-04/](https://codeghar.wordpress.com/2012/07/12/get-broadcom-bcm4311-working-in-ubuntu-12-04/)

hth
Otto-C

---

### Post by Hadaka on 2013-02-18
Hi, try this

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree 
sudo modprobe b43
```

you currently have Kernel modules: wl, ssb which are conflicting

---

