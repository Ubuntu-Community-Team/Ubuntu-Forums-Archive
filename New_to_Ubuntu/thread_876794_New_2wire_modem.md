---
title: "New 2wire modem"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Habaneroman on 2008-08-01
Just installed new modem with isp provider and set it up with my desktop and set my wireless up with my laptop (In Vista-I dual boot with Ubuntu) but i didnt set it up with ubuntu, and I am lost my wireless will not work with Ubuntu   Please Help

---

### Post by superprash2003 on 2008-08-01
please post your iwconfig output.. also type lshw -C network in the terminal and post output

---

### Post by silenthunter747 on 2008-08-01
I don't know if I'm having the same problems as Habaneroman, but I also have a 2wire modem (Homeportal 1700HW) that won't let me connect to the wireless network with Ubuntu. The modem will actually reset itself every time I attempt connect. Ethernet works OK and I can connect fine with Vista. 

I found this page which indicated it was something wrong with the hardware. If that's the case we may be out of luck until 2wire releases new firmware.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222793)

ifconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

lshw -C network
```

  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:16:d3:3e:9a:4a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=192.168.1.5 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:36:4f:6f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g


```

---

### Post by iacobus on 2008-08-01
Bump.  Same problem, with intel 4965agn and 2Wire 1000HW.

.:iacobus:.

---

### Post by Gaudentius on 2008-08-02
Same prob' here:

New Dell 1525N w/Hardy Heron pre-installed

2Wire 1000HW

Lifetime windoze user, complete n00b with Ubuntu

Hopefully someone'll know somethin'.

Thx

GD

---

### Post by anewguy on 2008-08-02
Okay, the dumb question to all of you first:

Did you, via ndiswrapper, fwcutter, or via a built-in, install the driver for your wireless card?

Then:

Who, if any of you, can see wireless networks available when you click on network manager?

Then:

If it holds true to your models as it did to mine from ATT DSL, remember that be default the encryption is 64-bit hex WEP.  The default length on the network manager connect screen is 128-bits, so you need to change it to 64-bit on the drop down selection.  Be sure it is set WEP and hex.  Also, IF it is true for your models as it was for mine, the default WEP code is on the label of the 2WIRE modem/router itself.

---

### Post by Gaudentius on 2008-08-02
Wireless works fine for me.  I'm hooked up at a coffee shop as I type this.  It's just the 2Wire gateway/router that is giving me problems.  It'll crash everytime I try to connect to it.

GD

---

### Post by anewguy on 2008-08-03
> **Gaudentius said:**
> Wireless works fine for me.  I'm hooked up at a coffee shop as I type this.  It's just the 2Wire gateway/router that is giving me problems.  It'll crash everytime I try to connect to it.

GD

Have you tried hard wired to the router and disable WEP, etc., and then try to connect?

---

### Post by silenthunter747 on 2008-08-03
> **anewguy said:**
> Have you tried hard wired to the router and disable WEP, etc., and then try to connect?

Ethernet works without any issues, and I just tried to disable WEP with the same results. It didn't ask me for a key but the router reset anyway.

---

### Post by anewguy on 2008-08-04
I'm not sure what to make of this - does anyone else have any ideas?

Since I didn't have that model, and since I don't know what your router is, forgive me for asking another dumb question:

Does your wireless card to "n" or just "b/g"?

Does your router support "n"?

---

### Post by iacobus on 2008-08-04
> **anewguy said:**
> I'm not sure what to make of this - does anyone else have any ideas?

Since I didn't have that model, and since I don't know what your router is, forgive me for asking another dumb question:

Does your wireless card to "n" or just "b/g"?

Does your router support "n"?

My router is an ATT DSL router, and I have tried both types of WEP encryption, leaving it open, and WPA.  I have an intel 4965 AGN wireless card.  That card is supported out of the box by hardy, and I can see networks in the list whenever I scan for available networks.  I can connect to other routers and get internet just fine, and I can connect to my 2wire via ethernet just fine.  I can also connect to the 2wire router on the same computer in my windows OS.  I think that answers all your questions... oh, my router is a 2Wire 1000HW.

.:iacobus:.

---

### Post by Gaudentius on 2008-08-13
> **anewguy said:**
> Have you tried hard wired to the router and disable WEP, etc., and then try to connect?

Disabled WEP: no work-y

No need for hard connection since it's the wireless I'd like.  The 1000HW has been working on an XP machine for years.  It just doesn't like my Hardy'd 1525N.

GD

---

