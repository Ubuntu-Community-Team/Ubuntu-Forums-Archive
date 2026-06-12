---
title: "Wireless Issues on an asus 900"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by kaspar_silas on 2008-09-30
Hey all,

I just installed the lovely ubuntu eee on my asus 900. Everything was going splendidly at home. Even the wireless  connected to the BT homehub no problem (it was a hex password). 

However I took this into work and so far have totally failed to get it to connect to the wireless network. Whilst I can see the network I cannot work out how to connect. 

I eventually found the router and it's an Apple AirPort extreme. I tested it on an XP laptop. Merely clicking the network and entering the passphrase done the job. 

Under the ubuntu system selecting the network gives a pop up with lots of options. I have no idea of the passphrase type so I went with the defaults but it just tried for about a minute then popped up again.

Anyone got any clues, hints or even the right questions to ask. O don't ask me to change the router settings as I can't do that. 

Thanks for any help

---

### Post by kaspar_silas on 2008-09-30
Okay, some further information. I reinstalled the default Xandros distribution. Then I retried the wireless and it connected straight away when I selected WEP as the password type.

So just in case it was a ubuntu eee problem I installed normal ubuntu and still the flaming thing still doesn't work. I'm now going back to ubuntu eee and praying someone else can sort this as im totally baffled

---

### Post by superprash2003 on 2008-09-30
in your terminal type lshw -C network and post output

---

### Post by kaspar_silas on 2008-09-30
Thanks for the reply. Sorry I couldn't answer earlier I just left work. Typing "sudo lshw -C network" gave:

```
  *-network
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: 00:22:15:22:e3:d0
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.0.5 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wifi0
       version: 01
       serial: 00:15:af:b7:62:a6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

---

### Post by superprash2003 on 2008-10-01
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

### Post by kaspar_silas on 2008-10-01
Cheers for that thread link I totally missed it. 

I will start going through the many many solutions lol.

---

