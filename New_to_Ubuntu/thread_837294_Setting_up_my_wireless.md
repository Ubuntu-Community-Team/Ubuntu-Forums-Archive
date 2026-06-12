---
title: "Setting up my wireless"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by iption on 2008-06-22
Hi I have a problem setting up my wireless. I have Acer Aspire 5022WLMI with ...
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
...wireless card

When I installed ubuntu (Hardy Heron, 8.04) it said I need b43-fwcutter so I installed it.
Reading:
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)
I also installed bcm43xx-fwcutter , I used b43 to install the drivers.

I couldn't install my original driver bcmwl5.sys, I got:
Sorry, the input file is either wrong or not supported by b43-fwcutter.
This file has an unknown MD5sum 38ca1443660d0f5f06887c6a2e692aeb.

From the same forum I read that the file is probably corrupted. Ok, so I downloaded one from the link and it worked. 

Restarted, not working, what now? Can somebody guide me step by step?

---

### Post by Kevbert on 2008-06-22
Have a look at this [guide]("http://ubuntuforums.org/showthread.php?t=766560").

---

### Post by iption on 2008-06-23
Hmmm that didn't work.

I want to try [http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318]("http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318")
but I don't know what to write "(replacing $ESSID and $KEY with the proper ESSID and key)"

in ```
sudo iwconfig wlan0 essid $ESSID key $KEY sudo ifup wlan0

```

---

### Post by jpyanowski on 2008-06-23
You can't have 2 fwcutter files. Uninstall bcm43xx as bcm43 is newer.

---

### Post by iption on 2008-06-26
Ok, new install, tried b43-fw.. tried ndsiwrapper fom the guide. 
lshw -C network
outputs

```
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wlan0
       version: 02
       serial: 00:14:a4:38:f0:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:e7:06:45
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

```

so I have module=ndiswrapper like the guide says, but I can't connect. I can't even see the networks, neither from the network manager, neither from the iwlist wlan0 scanning.

This is getting tiresome. I read almost everything on this. I'm thinking going back on windows because it seems all that talk of stability is bull... My panel froze two times!! Usb got unmounted after it previewed 5th picture. And the biggest trouble of all is (since everything I need is online, and I can't download big packages through dial-up) I can't download packages from windows because there is no database where you could choose the packages form, you can only try manually, if you are lucky to find the package you want.

I'm asking for the last time for someone to help me. I can give you my gtalk, icq, msn name so someone could guide me through enabling my wireless.

---

### Post by whitethorn on 2008-06-26
I can't really help much, the first time I installed gutsy, I had to use fwcutter to set my wireless and it worked out pretty well.  With hardy I just had to connect with a lan cable and it told me there was a restricted driver and it set itself up.  One thing I noticed is, if I turn off my wireless in windows I can't get it to run in linux.  You might want to boot into xp/vista and check if your wireless is activated.

---

### Post by iption on 2008-06-26
Ubuntu is my only os on this comp.

---

