---
title: "Network Trouble in Xubuntu 12.04"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by Controll on 2012-07-09
I installed Xubuntu 12.04 and got a notification to install updates.

After updates, Xubuntu takes quite a bit of time before the login screen saying "Waiting for network configuration... Waiting up to 60 more seconds for network configuration...Booting system without full network configuration"

Once in the OS, the icon for my wireless is missing from the panel, despite trying to add it to the panel.

Wired networking doesn't work either.

Any help is appreciated, I've been lost with linux since I installed.

---

### Post by mapes12 on 2012-07-10
Go Applications>Terminal and type ```
sudo lshw -C network
``` and post the output back here.

---

### Post by Bucky Ball on 2012-07-10
> **mapes12 said:**
> go applications>terminal and type ```
sudo lshw -c network
``` and post the output back here.

+1.

---

### Post by Controll on 2012-07-10
> **mapes12 said:**
> Go Applications>Terminal and type ```
sudo lshw -C network
``` and post the output back here.

*-network DISABLED      
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:a8:e9:6a
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:ee000000-ee01ffff ioport:3000(size=32)
  *-network DISABLED
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:2a:24:7d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:edf00000-edf0ffff

---

### Post by arieonline on 2012-07-10
try run this command

```
sudo service network-manager restart
```

---

### Post by Bucky Ball on 2012-07-10
You might also want to give MadWifi a go rather than Network Manager. It is specifically for Atheros cards. ;)

You'll need to get online with a cable to install, though, so that is problematic.

---

### Post by Controll on 2012-07-10
> **Bucky Ball said:**
> You might also want to give MadWifi a go rather than Network Manager. It is specifically for Atheros cards. ;)

You'll need to get online with a cable to install, though, so that is problematic.

I can get online from my desktop, xubuntu is on my thinkpad. I will take a look at madwifi

> **arieonline said:**
> try run this command

```
sudo service network-manager restart
```

This fixes my issue only temporarily, when I restart everything disables again, and my network info is still missing from the indicator plugin.

---

### Post by Bucky Ball on 2012-07-11
Ah, in that case, have you tried:

Settings>Xfce4 Settings Manager>Sessions and Startup>Make sure 'Network Manager' is ticked so it starts at boot. Should be in the list there.

> 'Network Manager (Control your network connections)';)

The promising thing is it works when you run Controll's command (nice one). BTW: IMHO xfce4 rocks!

---

### Post by wildmanne39 on 2012-07-11
Hi, have a look here.
[http://ubuntuforums.org/showthread.php?t=1981219](http://ubuntuforums.org/showthread.php?t=1981219)
[http://www.google.com/search?q=Waiting+for+network+configuration...+Waiting+up+to+60+more+seconds+for+network+configuration.&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs](http://www.google.com/search?q=Waiting+for+network+configuration...+Waiting+up+to+60+more+seconds+for+network+configuration.&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs)
Thanks

---

### Post by Controll on 2012-07-11
> **wildmanne39 said:**
> Hi, have a look here.
[http://ubuntuforums.org/showthread.php?t=1981219](http://ubuntuforums.org/showthread.php?t=1981219)
[http://www.google.com/search?q=Waiting+for+network+configuration...+Waiting+up+to+60+more+seconds+for+network+configuration.&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs](http://www.google.com/search?q=Waiting+for+network+configuration...+Waiting+up+to+60+more+seconds+for+network+configuration.&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs)
Thanks

Thank you, but this was unable to solve my issue.

> **Bucky Ball said:**
> Ah, in that case, have you tried:

Settings>Xfce4 Settings Manager>Sessions and Startup>Make sure  'Network Manager' is ticked so it starts at boot. Should be in the list  there.

I couldn't find a tick box for Network Manager under sessions and startup. I was thinking maybe I had to add it to the list?

---

### Post by arieonline on 2012-07-12
> **Controll said:**
> This fixes my issue only temporarily, when I restart everything disables again, and my network info is still missing from the indicator plugin.
i used xubuntu too, and to i make that command to run every login on xfce

---

### Post by Bucky Ball on 2012-07-12
In 12.04 LTS I notice it is just 'Network' for the taskbar applet, not 'Network Manager'.

---

### Post by Controll on 2012-07-14
I can't find anything regarding "Network" in the session and startup :/

---

### Post by LADmaticCA on 2012-07-14
Post the output of 
```

cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by Controll on 2012-07-15
> **LADmaticCA said:**
> Post the output of 
```

cat /etc/NetworkManager/NetworkManager.conf
```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

---

### Post by Controll on 2012-07-17
Any help at all? :(

---

### Post by LADmaticCA on 2012-07-17
> **Controll said:**
> [main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

Sorry for the late response. Hmm everything looks fine there. Try running:

```
sudo modprobe ath5k

```
See if that gets the wireless working.

---

### Post by Bucky Ball on 2012-07-17
Did you try Madwifi? Not sure if I suggested already but specifically with Atheros cards in mind, if that's what you're running ...

[http://madwifi-project.org/](http://madwifi-project.org/)

---

### Post by Controll on 2012-07-18
> **Bucky Ball said:**
> Did you try Madwifi? Not sure if I suggested already but specifically with Atheros cards in mind, if that's what you're running ...

[http://madwifi-project.org/](http://madwifi-project.org/)

Trying to work out how to get it running right now

---

### Post by Controll on 2012-07-18
> **LADmaticCA said:**
> Sorry for the late response. Hmm everything looks fine there. Try running:

```
sudo modprobe ath5k

```See if that gets the wireless working.

This didn't return anything in the terminal, and after a restart, my networking is still disabled.

---

