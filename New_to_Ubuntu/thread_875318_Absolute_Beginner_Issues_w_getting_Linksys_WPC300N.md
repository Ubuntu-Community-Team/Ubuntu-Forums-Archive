---
title: "Absolute Beginner Issues w/ getting Linksys WPC300N wireless card"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by mnemonik on 2008-07-30
Hi everyone! Future thanks for any help!

My stuff:

*Dell Inspiron 6000 laptop w/ ubuntu 8.04

*Linksys WPC300N wireless card

My issues:

I cannot figure out how to get Ubuntu to recognize my wireless card, or get me on the internet. From what I have been able to gather I need to install ndiswrapper (I have so far failed) and it will compile the drivers...? I have the driver for windows and my understanding is that I need inf files?

Please keep in mind I AM AN ABSOLUTE NEW BEGINNER @ UBUNTU/LINUX! I only just figured out where to type these commands like sudo this or that! Please don't hate I'm trying to learn, but very not used to typing commands that I don't understand. STEP BY STEP, SIMPLE HELP IS MUCH APPRECIATED!!!

---

### Post by mnemonik on 2008-07-30
last time i had problems this forum was such a great help... hwat happened? :(

---

### Post by superprash2003 on 2008-07-30
in your terminal type lshw -C network and post output here

---

### Post by mnemonik on 2008-07-31
mnemonik@mnemonik-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:e7:e0:e8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:c5:0b:4a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network UNCLAIMED
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       configuration: latency=0
mnemonik@mnemonik-laptop:~$

---

### Post by mnemonik on 2008-07-31
From what I can tell its picking up my ethernet and built in wireless (which has been bunk for sometime, its a common issue on dell laptops) but not the linksys wireless card. Am I right?

---

### Post by mnemonik on 2008-07-31
I managed to install ndiswrapper, its utilities, and ndisGTK, by following this: [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)

But i get stuck at this part here:
#

Open a Terminal (Applications | Accessories | Terminal), type lspci and press the return/enter key.
#

Look through the output of the lspci command for an entry for your wireless card.
#

Once you have identified your card, note down the contents of the first column, which should look like 0000:00:0c.0.
#

Now, type lspci -n into the Terminal and press return.
#

Find the PCI ID for your device. Your device will be referred to in the output of the command by the identifier which you just made a note of, e.g. 0000:00:0c.0. The PCI (chipset) ID will be in the third column of the output and will be in the form 104c:8400.

I can't find my wireless card after typing lspci or lsusb (even though its not a usb adapter, i figured i would try it)

---

### Post by superprash2003 on 2008-08-01
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by mnemonik on 2008-08-01
> **superprash2003 said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The guide says that it is for feisty fawn, will it still work for hardy? It also says it depends on a wired connection being present, which I don't have. Is there an easy workaround? I'm really new at this, really specific step by step instruction would be nice. thank you!

---

### Post by superprash2003 on 2008-08-01
yes it would work for hardy.. are you unable to connect a LAN cable to your router and get wired internet access?

---

### Post by cpenni on 2008-09-01
I'm having the same problems as the others with linksys wpc300 card. under configuration: it says latency=0 and nothing else.
i can connect to a wired lan but no wireless listed under network settings. this is ubuntu 8.04 thanks for any help.

---

