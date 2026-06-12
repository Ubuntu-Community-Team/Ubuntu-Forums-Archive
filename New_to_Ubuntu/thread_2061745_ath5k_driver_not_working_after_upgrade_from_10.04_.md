---
title: "ath5k driver not working after upgrade from 10.04 to 12.04"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by benolding on 2012-09-23
Hi - this is my first post on these forums; I'm afraid I've run out of new keywords to search on google.

I've been running 10.04 LTS 32 bit on an old Dell Dimension 4100.  I have a DLink wireless card in it.

The wireless card basically worked out of the box when I installed 10.04 on it.  I am not using NetworkManager, nor am I using any desktop utilities (it's all from the terminal).

I recently upgraded to 12.04 LTS 32 bit.  Everything on the system seems fine, except the wireless card is "unclaimed," so I can't use it.

> sudo lshw -C network
  ```
*-network:0 UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: c
       bus info: pci@0000:02:0c.0
       version: 41
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
       resources: memory:ff9d0000-ff9dffff
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: d
       bus info: pci@0000:02:0d.0
       logical name: eth0
       version: 78
       serial: 00:01:03:22:c3:0f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=10.0.1.2 latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 ioport:dc00(size=128) memory:ff9ef800-ff9ef87f memory:ff9a0000-ff9bffff
```


Here are the results of dmesg:

> dmesg |grep ath
```
[   12.762601] ath5k 0000:02:0c.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   12.762740] ath5k 0000:02:0c.0: registered as 'phy0'
[   12.767203] ath5k phy0: POST Failed !!!
[   12.892446] ath5k 0000:02:0c.0: PCI INT A disabled
[   12.892483] ath5k: probe of 0000:02:0c.0 failed with error -11

```

Any theories on why the card no longer works?  I've read suggestions about madwifi, but that seems like the wrong path to go down, given that the card worked absolutely fine with ath5k.  

Based on some threads I read, I've tried adding "nohwcrypt=1" to the ath5k config, but there was no change.  I believe this is because the system cannot make use of the wireless card (there is no "wlan0" on the system), rather than the ath5k driver being misconfigured.  However, I'm really outside my depth here, and I'm concerned I'm just making stuff up at this point.

The driver is clearly being loaded:
>  lsmod |grep ath
```
ath5k                 145127  0
ath                    19387  1 ath5k
mac80211              436455  1 ath5k
cfg80211              178679  3 ath5k,ath,mac80211
```


Any suggestions much appreciated at this point.

---

### Post by TheMTtakeover on 2012-09-23
Could you try a fresh install?

---

### Post by benolding on 2012-09-23
I do appreciate your willingness to reply, but I'm a little shocked this is the first suggestion.  Is this really the preferred approach to Ubuntu system administration?  I am completely new to these forums.  Wiping my system in an attempt to solve a driver issue seems like it should be the suggestion of last resort.

---

### Post by einonm on 2012-09-23
Yes, wiping the system is indeed a last resort!

Another thing that may be quite helpful to know is the state of any wireless kill switches - so could you run the command 'rfkill list' and post the output?

---

### Post by benolding on 2012-09-23
Sure - I should have emphasized this in the original post: there is no wlan0 on the system - the wireless pci card is "unclaimed."

So, when I run the rfkill command, I get zero output:

> rfkill list```


```

Similarly, if I run ifconfig, there is no wlan0:

> ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:01:03:22:c3:0f
          inet addr:10.0.1.2  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:3ff:fe22:c30f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55182 errors:0 dropped:0 overruns:41 frame:0
          TX packets:32201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:35255166 (35.2 MB)  TX bytes:2317551 (2.3 MB)
          Interrupt:11 Base address:0x800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:36328 (36.3 KB)  TX bytes:36328 (36.3 KB)

```

---

### Post by benolding on 2012-09-23
Ok, I figured it out.  In retrospect, this was a small problem I turned into a bigger one through my inexperience.  I will document what happened in case this is helpful to someone in the future.

First, I believe I have learned that when a PCI card goes "unclaimed" this is not a driver problem, but rather a BIOS problem.  I had previously found a thread that suggested modifying /etc/default/grub in order to solve a BIOS problem.  I modified one of the lines and - in doing so - I believe *created* a BIOS problem for myself.  In fact, while indeed I had this problem at the start of the thread, it was a complication of my own making from my previous efforts to solve the real underlying problem.

Undoing the change (returning the line to read simply GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", then running sudo update-grub) caused the wireless card to be claimed by the driver.  Of course, it still didn't work, but at least I was back to where I started at following the upgrade (I believe).

> dmesg |grep ath
```
   20.942047] ath5k 0000:02:0c.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   20.942201] ath5k 0000:02:0c.0: registered as 'phy0'
[   21.966411] ath: EEPROM regdomain: 0x10
[   21.966423] ath: EEPROM indicates we should expect a direct regpair map
[   21.966434] ath: Country alpha2 being used: CO
[   21.966440] ath: Regpair used: 0x10
[   22.157219] ath5k phy0: Atheros AR5212 chip found (MAC: 0x56, PHY: 0x41)
[   22.157234] ath5k phy0: RF2112B 2GHz radio found (0x46)

```

The wireless card was now found, but it still was not connecting to the router.

I noticed a suggestion from Chili555 on another thread to run:
> ps aux | grep -i network
to see if NetworkManager was running.

Indeed, it was.  So here then, I believe, is why my wireless card stopped working after the upgrade: in my original configuration under 10.04 I had disabled NetworkManager and was manually configuring the wireless card through /etc/network/interfaces.  Following the upgrade to 12.04, NetworkManager started running again.

I removed NetworkManager from my system using sudo aptitude remove network-manager (a little extreme maybe - probably should have just disabled it - but I was annoyed at myself for not thinking of this earlier.)  Now I was back to using the manual configuration approach to running my wireless card.

Rebooted, and everything works again.  Rebooted again to double check.  Then rebooted a third time... yeah, it seems stable.

Thanks for the two people above willing to respond to my thread, and if there's anyone who reads this after, I really hope you can avoid wiping your whole system just to get a wireless card working.  I was really nervous there for a moment I might actually talk myself into doing that.

---

### Post by steeldriver on 2012-09-23
Hmm... that's odd, I have an ath5k device running on 12.04 here and I don't remember having to do anything to get it working - can you check the PCI ID for your device using lspci -nn? something like

```
lspci -nn | grep Atheros
```Also I wonder if for some reason udev isn't picking it up? do you see a matching entry for the device in the persistent-net-rules file?

```
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by benolding on 2012-09-23
Thanks for the reply, but I figured it out.  See post above yours - I think we posted close to the same time.

---

