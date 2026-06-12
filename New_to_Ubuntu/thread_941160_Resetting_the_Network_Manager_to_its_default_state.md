---
title: "Resetting the Network Manager to its default state"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by shabs on 2008-10-07
Hi,
I've just installed 8.04 (from the CD that I had burned in early April/May '08 ) and my wireless worked fine. But then as soon as I updated my system it doesn't pick up any wireless networks. I've strangely had this exact problem when I updated from 7.10 to 8.04 earlier. Then I assumed it was a problem with my hardware but now I'm pretty sure its some update for the network manager thats screwing things up. Is it possible to set the network manager to defaults, to the state that it was in when I installed it from the CD? Or can I browse the CD to reinstall just the network manager?

I've pasted the output of lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Thanks for your help!

---

### Post by victorbrca on 2008-10-11
What kind of wireless adapter do you have (PCI, built-in, USB..)?

Can you see the adapter when using "ifconfig -a"?


Vic.

---

### Post by shabs on 2008-10-13
> **victorbrca said:**
> What kind of wireless adapter do you have (PCI, built-in, USB..)?

Can you see the adapter when using "ifconfig -a"?


Vic.

Hi Vic
ifconfig -a does not list my wireless adapter. It lists out the various interfaces, my h/w address, etc. Wouldnt the output of lspci list that?

---

### Post by victorbrca on 2008-10-13
> **shabs said:**
> Hi Vic
ifconfig -a does not list my wireless adapter. It lists out the various interfaces, my h/w address, etc. Wouldnt the output of lspci list that?

Only if it's a PCI adapter.

---

### Post by shabs on 2008-10-14
Hey Vic, 
I have a built-in card. I'm pasting the output of: sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:00:00:00:00:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=xxx.xx.xxx.xx latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:00:00:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Does this tell you more? I'm connected via a wired connection right now.

---

### Post by victorbrca on 2008-10-14
I'll try to help the best I can. My knowledge on network adapters is not as "sharp" as I would like it to be... 

What happens if you issue the command:

```
sudo ifconfig wlan0 up
```

```
ifconfig
```


Vic.

---

### Post by shabs on 2008-10-14
I appreciate it vic. Well ifconfig lists this out:
ifconfig
eth0      Link encap:Ethernet  HWaddr xxx  
          inet addr: xxx  Bcast: xxx  Mask:255.255.252.0
          inet6 addr: xxx Scope:Site
          inet6 addr: xxx Scope:Global
          inet6 addr: xxx Scope:Global
          inet6 addr: xxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48925495 (46.6 MB)  TX bytes:2178217 (2.0 MB)
          Interrupt:17 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71298 (69.6 KB)  TX bytes:71298 (69.6 KB)

wlan0     Link encap:Ethernet  HWaddr xxx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr xxx
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I'm not entirely sure what "sudo ifconfig wlan0 up" does but when I tried it returned without any errors. How does the output of ifconfig help?

---

### Post by victorbrca on 2008-10-14
The command "sudo ifconfig wlan0 up" will enable your adapter, which looks like it did:

> wlan0 Link encap:Ethernet HWaddr xxx
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

Can you see any available wireless networks on the wireless applet at your panel?

[IMG]https://wiki.thayer.dartmouth.edu/download/attachments/10256864/F8_NMAppletSelectWirelessNet.png[/IMG]


If not, try issuing the following command:

```
sudo iwlist scanning
```

---

### Post by shabs on 2008-10-14
Maybe I should have added more details, my mistake. I usually see the wireless networks. I can even connect to them, but after a few minutes the signal will go to zero and then if I click on the network manager icon it will say no wireless networks found. After a while I will be able to see the networks again but then the cycle continues. Before updating my installation it was working fine. 
Heres the output of sudo iwlist scanning:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

Thanks again.

---

### Post by bodhi.zazen on 2008-10-14
Not to get too far off topic, but ...

I had a number of problems with network manager in 8.04, and I struggled for several weeks, almost a month, I re-wrote so many config files and made boot scripts ...

At the end of the day the problem was with network manager.

I changed to wicd and all has been well :)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

wicd is easy to install, and it is easy to revert if needed.

Note: wicd does not work for everyone, but you may wish to take it for a spin.

---

### Post by shabs on 2008-10-14
Hi bodhi.zazhen,
Before I did a clean install of 8.04 I had updated 7.10 to 8.04. Thats when the problems started. I've tried wicd and madwifi with similar problems.

---

### Post by bodhi.zazen on 2008-10-14
> **shabs said:**
> hi bodhi.zazhen,
before i did a clean install of 8.04 i had updated 7.10 to 8.04. Thats when the problems started. I've tried wicd and madwifi with similar problems.

ouch !!!

---

### Post by shabs on 2008-10-15
> **bodhi.zazen said:**
> ouch !!!

So can I revert back to the older network manager version thats used in 7.10?

---

