---
title: "Problem with wireless UBUNTU 12.04"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by Zudey on 2012-07-08
[SIZE="3"]Hi guys!![/SIZE] ):P
I have a Problem with Ubuntu, Im new on this forums so I decided register, because I need Help, 

[SIZE="3"]**I installed for first time Ubuntu in a laptop, but I have problems with the wireless connection, I only can connect to the web by wired connection. I really need your help!! PLEASE**[/SIZE]

Details:
[LIST]
[*]OS UBUNTU 12.04
[*]Intel Centrino DUO
[/LIST]

---

### Post by mapes12 on 2012-07-08
Go Applications>Terminal and type ```
sudo lshw -C network
```and post the output back here.

---

### Post by Zudey on 2012-07-08
Here is:


> [B][COLOR="Red"]schenk@schenk-PC:~$ sudo lshw -C network
[sudo] password for schenk: 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:2b:60:89
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.2.0-26-generic-pae firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:d2100000-d2100fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:cf:6b:b7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:d2200000-d2200fff memory:80500000-8051ffff

[/COLOR][/B]

---

### Post by ubudog on 2012-07-08
Try this, as obtained from chili555 [here]("http://ubuntuforums.org/showthread.php?t=1748677"):

```
sudo modprobe iwl3945
dmesg | grep iwl
lspci -nn | grep -i wireless
```

Then:
```
sudo su
echo iwl3945 >> /etc/modules
exit
```

---

### Post by NikTh on 2012-07-08
Open a terminal and write this command 
```
rfkill list all
```
post the output here inside [CODE] brackets , by clicking the # symbol at the top of message pane.

---

### Post by Zudey on 2012-07-08
THIS IS FOR [SIZE="4"][COLOR="Red"]UBUDOG[/COLOR][/SIZE]


[COLOR="Blue"]schenk@schenk-PC:~$ sudo modprobe iwl3945
schenk@schenk-PC:~$ 
schenk@schenk-PC:~$ dmesg | grep iwl
[   15.128993] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   15.128996] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   15.129063] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.129078] iwl3945 0000:02:00.0: setting latency timer to 64
[   15.192279] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   15.192283] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   15.192439] iwl3945 0000:02:00.0: irq 45 for MSI/MSI-X
[   15.237153] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   16.477571] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
[   16.477710] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   16.889333] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   16.889495] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
schenk@schenk-PC:~$ 
schenk@schenk-PC:~$ lspci -nn | grep -i wireless
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
schenk@schenk-PC:~$[/COLOR] 










AND THIS IS FOR [SIZE="4"][COLOR="Red"]NikTh[/COLOR][/SIZE]


```
schenk@schenk-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by ubudog on 2012-07-08
Did you run this?

```
sudo su
echo iwl3945 >> /etc/modules
exit
```

After that, reboot, and see if your wireless works.  :)

---

### Post by NikTh on 2012-07-09
> **Zudey said:**
> 
[COLOR=Blue]
```
[   16.889333] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   16.889495] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
```[/COLOR][COLOR=Blue]

[COLOR=Black]If ubudog's solution don't work , try to search for a switch , like Fn+F10 or something or check the Bios for unlock WiFi. 
This is an old knowing bug , but i thought was solved. 

Well  a workaround i found , but i am not sure if works , its this... 

1) change network manager to wicd 
OR
2) From _[Chilli555]("http://ubuntuforums.org/showthread.php?t=820297") _run these commands and see if WiFi works .. 
[/COLOR][/COLOR]```

sudo rmmod -f iwl3945 
sudo modprobe iwl3945 disable_hw_scan=1
```

---

### Post by Zudey on 2012-07-09
oh oh!! In System Settings/Network, the wireless option disappeared :( Now I dont have wireless option 

[COLOR=Red]WITH UBUDOG OPTION NOTHING HAPPENED AN WITH NIKTH THE WIRELESS OPTION DISAPPEARED [/COLOR]

---

