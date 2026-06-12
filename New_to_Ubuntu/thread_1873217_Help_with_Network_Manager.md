---
title: "Help with Network Manager"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by vasa1 on 2011-11-01
Ubuntu 11.10
Internet connection is via "cable" without any modem or router at my end
Computer is Dell Inspiron 1545 laptop

When I [s]start my PC[/s] login, network manager (NM) tries to establish a internet connection. It may not be successful immediately and pic in row 1 appears briefly on the screen but NM keeps trying until it makes a connection and then pic in row 2 appears briefly.

If I click on the NM icon in the top right, I'll get a dropdown indicating which of my DSL connections is active. (I have just the one ISP). It's DSL 4 in the example in the pic on the left in row 3.

Now, if I choose to disconnect, the dropdown changes to the pic on the right (in row 3). At any time later, I can click on the NM icon and then click on any connection from the dropdown to start an internet session. No problem so far.

However, if the connection drops by itself (which is not rare), on a very few occasions, NM re-establishes a connection. Most of the time NM doesn't try to re-establish a connection and when I click on the NM icon to restart the internet session, I see the pic in row 4. None of my connections are visible. I work around this by opening a terminal and running "sudo service network-manager restart". Only after this, does NM start trying to establish a connection and I see the full dropdown shown on the left in row 3.

Is there something I can do to get NM not to stop and be required to be restarted when the disconnection is "involuntary"?

I don't recall having this problem in 11.04 and it has started only after I upgraded to 11.10. If it matters, it was an in situ upgrade on line and not a "clean/fresh install".

Edit: this is related to this thread: [http://ubuntuforums.org/showthread.php?t=1861127](http://ubuntuforums.org/showthread.php?t=1861127)

---

### Post by rimibchatterjee on 2011-11-01
I also have this problem. i have a DSL network connection and if it shuts down of its own accord, the whole link disappears from my network manager menu. I can see it if I open edit connections, but I can't restart it or activate it in any way. I managed to restore this by restarting the system. but there must be a better way to get connectivity back after an outage

---

### Post by vasa1 on 2011-11-01
> **rimibchatterjee said:**
> I also have this problem. i have a DSL network connection and if it shuts down of its own accord, the whole link disappears from my network manager menu. I can see it if I open edit connections, but I can't restart it or activate it in any way. I managed to restore this by restarting the system. but there must be a better way to get connectivity back after an outage

Hi, fellow sufferer!
As I mentioned, I'm working around it by having to open a terminal and running "sudo service network-manager restart". This avoids the need for a re-login (or reboot). I feel it shouldn't happen but it does :(

---

### Post by vasa1 on 2011-11-02
I came across this:
[http://domesticatedonion.net/eng/2011/10/24/ubuntu-11-10-network-management/](http://domesticatedonion.net/eng/2011/10/24/ubuntu-11-10-network-management/)

I'm trying it. Let's see!

---

### Post by vasa1 on 2011-11-03
^^^ That doesn't seem to make a difference. I still have to restart network manager via the terminal.

---

### Post by cbowman57 on 2011-11-06
When you look at the setting for your active connection is the checkbox for Available to All Users toggled on?

---

### Post by vasa1 on 2011-11-06
> **cbowman57 said:**
> When you look at the setting for your active connection is the checkbox for Available to All Users toggled on?

Yes. I have set that for all the connections.

---

### Post by cbowman57 on 2011-11-06
I seem to remember having this problem a year or so ago, my solution was to temporarily switch to wicd until a version of networkmanager came out that worked right.

I couldn't find a definitive fix on the web.

---

### Post by vasa1 on 2011-11-06
> **cbowman57 said:**
> I seem to remember having this problem a year or so ago, my solution was to temporarily switch to wicd until a version of networkmanager came out that worked right.

I couldn't find a definitive fix on the web.

Chuck, thanks for replying :)

It's okay since the problem is not unmanageable. I just thought there maybe an easy fix that I didn't know about. I'm too much of a noob to change to wicd. I'd rather keep what comes with the original install.

---

### Post by cbowman57 on 2011-11-06
It's possible that the problem is the result of something that happened due to the dist-upgrade.

I would probably attempt to purge networkmanager & reinstall it just in case the configuration got messed up in the upgrade process.

If that didn't work I'd create a launcher to run your network service restart. :)

---

### Post by vasa1 on 2011-11-06
> **cbowman57 said:**
> It's possible that the problem is the result of something that happened due to the dist-upgrade.

I would probably attempt to purge networkmanager & reinstall it just in case the configuration got messed up in the upgrade process.

If that didn't work I'd create a launcher to run your network service restart. :)

That it could be due to the upgrade is very likely since I noticed it only after upgrading to 11.10.

If I purge it, how can I reinstall since I imagine I won't have a net connection then? <<< newbie alert!!!

As for creating a launcher, the restart requires my password: I use ```
sudo service network-manager restart
``` from the terminal prompt. Would a launcher be significantly more efficient? My net connection does drop but not that frequently.

---

### Post by cbowman57 on 2011-11-06
It would eliminate a lot of typing, the simple method is to use alacarte (Main Menu editor) and create an entry something like this:  [ATTACH]206512[/ATTACH]

You may also be able to use gksu, in that case you want just "Application", not the "Application in Terminal" as in my example.

Creating your own launchers for your common tasks can be pretty convenient.

---

### Post by bluexrider on 2011-11-27
OK, question?

Main Menu> Preferences> Network Connections>  

Under Wired Tab
     WHAT SHOWS?
     HOW MANY?

Under  DSL Tab
     WHAT SHOWS?
     HOW MANY?

Does this correspond to how many NIC's you have if not whats the difference?



Then in Terminal:

sudo lshw -class network

print results and post

---

### Post by vasa1 on 2011-11-28
> **bluexrider said:**
> OK, question?
Main Menu> Preferences> Network Connections>  
Under Wired Tab
     WHAT SHOWS?
     HOW MANY?
Under  DSL Tab
     WHAT SHOWS?
     HOW MANY?
Does this correspond to how many NIC's you have if not whats the difference?

Then in Terminal:
sudo lshw -class network
print results and post

0. I'm on Ubuntu 11.10 Unity 3D mode.
1. Where do I get "Main Menu"? Typing Main Menu in the dash opens **alacarte** which doesn't show me "Preferences" right away.
Anyway, I click on the Network Manager indicator and then on Edit Connections ...
Under "Wired" tab, I have just auto eth0 which I haven't set up since when I tried it at the very outset (while testing the LiveCD), it didn't connect me.
Under DSL tab, I have four connections basically to the same ISP but with differing IP addresses.
I don't know what you mean by "NIC's".

```
aes@aes-Inspiron-1545:~$ sudo lshw -class network
  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:8d:7a:c3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:2d:24:31
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
aes@aes-Inspiron-1545:~$ 

```

Make any sense?

---

### Post by bluexrider on 2011-11-28
What doesn't make sense is the number of connections you have under DSL.

So.....is your DSL (DHCP) or STATIC?

makes a difference in the way you set your network

also under Alt+F2 run this:
gksu gedit /etc/resolv.conf

---

### Post by vasa1 on 2011-11-28
> **bluexrider said:**
> What doesn't make sense is the number of connections you have under DSL.

So.....is your DSL (DHCP) or STATIC?

makes a difference in the way you set your network

also under Alt+F2 run this:
gksu gedit /etc/resolv.conf

They're all DHCP.

```

aes@aes-Inspiron-1545:~$ gksu gedit /etc/resolv.conf
# Generated by NetworkManager
nameserver 115.69.240.12
nameserver 115.69.240.11
```

The number of DSL connections is totally my doing. I can keep just one if you feel that'll help!

---

### Post by bluexrider on 2011-11-28
it would be better if we were working with only one.

---

### Post by vasa1 on 2011-11-28
> **bluexrider said:**
> it would be better if we were working with only one.

Done!

---

### Post by bluexrider on 2011-11-28
from terminal run: pppoeconf

follow the prompts 

then reboot

I'll check tomorrow see where we are at.

[COLOR=Red]RECHECKED POST. NO ADDITIONAL LISTING FOR QUESTIONS. LEAVING THREAD.[/COLOR]

---

