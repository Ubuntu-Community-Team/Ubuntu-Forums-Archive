---
title: "Can't turn on wireless"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by pgouldburn on 2008-05-02
I'm new to ubuntu and just installed it today. Since installing i cannot turn on my wireless on my laptop. Can anyone help me?

---

### Post by llamakc on 2008-05-02
Yes, after you give details. Right now nobody knows what kind of computer you have, what sort of wireless card or chipset you have, or what you have tried so far.

Answer those and somebody should be along.

---

### Post by Tatty on 2008-05-02
By "turn on wireless" do you mean a light that indicates that your wireless card is on, or do you just mean you cannot connect to anything wirelessly?

Can you give details of your wirelss card and how far you have already gotten in troubleshooting this issue.

---

### Post by pgouldburn on 2008-05-02
Well, now i'm having trouble just trying to find out what wireless card i have. I have a Compaq V5000 with AMD Turion 64. And yeah, i'm just trying to get the blue light on.

---

### Post by NewDisciple on 2008-05-03
Try running:

lspci

in your terminal and post it here.

---

### Post by Ayuthia on 2008-05-03
Just an addition to NewDisciple's request, can you post lspci -nn instead?  It will give us you chipset id.  Some cards have the same name, but they have different chips.

---

### Post by pgouldburn on 2008-05-03
results from lspci -nn

00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
adam@adam-laptop:~$ 


lspci result
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Thank you very much.

---

### Post by pgouldburn on 2008-05-03
Now i've got the blue light on but i can't see any wireless networks to connect to. I have one set up at my place and there are several around but i can't see them.

---

### Post by NewDisciple on 2008-05-03
These two links should help.

[https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/14605](https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/14605)

   	
[http://www.linuxforums.org/forum/wireless-internet/105260-bcm-4318-native-drivers.html](http://www.linuxforums.org/forum/wireless-internet/105260-bcm-4318-native-drivers.html)

---

### Post by fkamp on 2008-05-03
Hi,

I have an HP Pavillion dv6000. I recently upgraded to 8.04. Sometime after the upgrade I noticed that the blue light for the wireless connection was not on. I can still connect and surf but it seems to be slower. Here is what lspci -nn has to say about the wireless hardware.

05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)

Device Manager reports that it is PRO/Wireless 3945ABG Network Connection.

When I first installed Ubuntu (I believe 7.04), I got a warning message about using proprietary drivers for the wireless. Now after the upgrade, there are no proprietary drivers installed.

Could it be that there was a change in the driver in that it doesn't 
utilize the connection light anymore?

Thanks for your time

fkamp

---

### Post by fkamp on 2008-05-03
Solved!

> **chili555 said:**
> Mine works fine, including the LED, with:```
sudo apt-get install linux-backports-modules-hardy-generic
```

Many thanks to chili555 !

---

### Post by fkamp on 2008-05-03
> **chili555 said:**
> Mine works fine, including the LED, with:```
sudo apt-get install linux-backports-modules-hardy-generic
```

Thanks to chili555 my led works and the connection is improved!!!!

---

### Post by pgouldburn on 2008-05-13
This is what helped mine. 

[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/]("http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/")

---

### Post by rpwdh on 2008-05-13
I had the same problem with my Broadcom 43xx.

I hooked up a hard wired connection to the router and then ran System Update and it installed the wireless drivers as well as a bunch of other stuff.

Hopefully it will be as sinple for you!

---

