---
title: "dropped connections"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by vegan1 on 2011-11-29
Hi,

   I use Ubuntu 11.04. I have had a lot of dropped connections, with both wired and wireless. I use Windows 7, and the connection doesn't seem to drop, so I don't think it is a problem with the router. It mostly happens during downloads.

   Is there a way to fix the problem? Do I need to give any hardware information?

---

### Post by bluexrider on 2011-11-29
This information may help. There is no one answer to fit all the different configurations.

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by vegan1 on 2011-11-29
Thanks bluexrider,

       I started reading the page on wifidocs. I found the network tools dialog box? Are some of the tabs going to be important for testing the strength of the connection? Also, how do I figure out the eth0 connection?

       My connection works, it just drops unexpectedly. So, does that give somebody an indication of how to search for the root of the problem?

---

### Post by vegan1 on 2011-11-29
Could the problems with the dropped connection be resulting from an encryption scheme, where Windows automatically does something but Linux doesn't? If so, is it part of the automatic firewall settings? I didn't configure a firewall, but there might be one automatically in place.

---

### Post by bluexrider on 2011-11-30
Its unlikely to have a hardwire connection fail as in dropping connections. This usually occurs using wireless. But nothing should be surprising. 

I would suggest diagnostic on the wired connection first. 

Is win7 and ubuntu on the same machine. They use the same hardware?

run this in terminal:

sudo lshw -c network

repost info please

---

### Post by vegan1 on 2011-11-30
Thanks Bluexrider,

How do I put all the code down below in a special box? Win7 and Ubuntu are on the same hard drive as a dual-boot. The dropped connection with the hard wire was on my laptop, though. The following information is on my desktop.

I learned how to disable the firewall, which may not be such a good idea, through the link you sent me and did that. I haven't had any dropped connections since then, but it hasn't been enough time to see if it will permanently fix the problem.

If there was something seriously wrong with the wireless card driver, then I would imagine that the wireless connection wouldn't work at all. I think it might have something to do with the firewall settings or the encryption, though that is just my intuition.

Could you send me some Ubuntu specific information on adjusting the firewall, please?

```
 *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 90:00:4e:22:1f:ba
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-13-generic firmware=N/A ip=192.168.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:e3:0e:cf
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:febe0000-febfffff
```

---

### Post by vegan1 on 2011-11-30
How do I put all the code down below in a special box?

Please, disregard this request. The code wrap worked.

---

### Post by bluexrider on 2011-11-30
> **vegan1 said:**
> Thanks Bluexrider,

How do I put all the code down below in a special box? Win7 and Ubuntu are on the same hard drive as a dual-boot. The dropped connection with the hard wire was on my laptop, though. [COLOR=Red]The following information is on my desktop.[/COLOR]

I learned how to disable the firewall, which may not be such a good idea, through the link you sent me and did that. I haven't had any dropped connections since then, but it hasn't been enough time to see if it will permanently fix the problem.

If there was something seriously wrong with the wireless card driver, then I would imagine that the wireless connection wouldn't work at all. I think it might have something to do with the firewall settings or the encryption, though that is just my intuition.

Could you send me some Ubuntu specific information on adjusting the firewall, please?


are we working on 2 machines or 1
desktop or laptop

thanks for posting the code result

There are several issues with the Realtek PCI card and Linux drivers that I know of and the 
AR928X have issues too. So 

First thing is to make sure we are up to date

sudo apt-get update && sudo apt get dist-upgrade

Then we diag from there

---

### Post by vegan1 on 2011-11-30
Bluexrider,

    Is it necessary to do a distro upgrade? I never got used to whatever Ubuntu is using for 11.10. I don't know if I can use it. I don't think there is a fallback mode for Gnome 2. I would rather keep on using 11.04.

    I just did some research and I read that distro upgrades are prone to failure, either the upgrade process doesn't work right or the new distro doesn't work right. I would have to back up all my data, which I haven't done yet, in case of a failure.

---

### Post by vegan1 on 2011-11-30
Bluexrider,

     Actually, with my connectivity problems, I think the distro upgrade would be almost sure to fail. I hear it takes quite a while to download all those files, even with a fast connection.

---

