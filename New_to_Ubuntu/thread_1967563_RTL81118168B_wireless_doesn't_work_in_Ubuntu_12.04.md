---
title: "RTL8111/8168B wireless doesn't work in Ubuntu 12.04"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by vishwasharitsya on 2012-04-28
Hello,

        I've installed Ubuntu 12.04 on my laptop recently and no matter what I do, wifi doesn't work.

Having said that, when i connect it to a network cable, Internet works as well as it can.

I've set up a dual boot system alongside Windows 7 and Wifi runs smoothly in Windows.

Having gone through a lot of forums and threads, I tried applying a couple of patches but nothing seems to be helping.

RTL8111/8168B is the Ethernet Controller of my system.

A little help would be very handy. Thank you.

PS: My laptop model is Lenovo L412

---

### Post by verymadpip on 2012-04-28
Hi there.

What is the model of wireless adaptor in that machine?  I think the RTL8111/8168B is for your wired connection.

You could try typing the following commands into a terminal & looking for something including the word "wireless". 

```
lspci
```

```
lsusb
```

---

### Post by kurt18947 on 2012-04-28
> **vishwasharitsya said:**
> Hello,

        .............

RTL8111/8168B is the Ethernet Controller of my system.

A little help would be very handy. Thank you.

PS: My laptop model is Lenovo L412

The ethernet controller is the wired controller.  The wireless will be called something like network controller.  Is your wireless built into your machine?  If so, it should show up by opening a terminal and typing
```
lspci
```The output should look something like this.  i used 'lsusb' because this machine has a USB WiFi adapter:
```
everyday@r61:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
**Bus 002 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]**

```The bolded line is my wifi adapter. Once we know what wifi chipset your machine uses,  we can help you better.  Common ones are Intel, Atheros, RealTek and Broadcom.

---

### Post by vishwasharitsya on 2012-04-28
Hello,

      Thanks for helping.

Below is the output of the command **lspci**

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
02:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```Looking at the above, I believe it is [B]Intel Corporation Centrino Advanced-N 6200 (rev 35)

[/B]Funny thing is, i'm able to connect to the wireless connections available but the internet isn't working.

---

### Post by roger_1960 on 2012-04-28
Hi

That sounds like the router settings are wrong.  Is it your modem/router?

If you "edit connection" on the dropdown, select your current connection, in IPV4 settings it would normally be set to "automatic DHCP".

What are your normal settings when using windows? It may need to be the same in Ubuntu.

---

### Post by vishwasharitsya on 2012-04-28
Hi Roger,

         The settings are the same as in windows.

I think this is something to do with the driver which i'm not able to figure out.

However, another weird thing is that i'm connected through wifi hotspot from my mobile and posting this.

Totally confused!!!

---

### Post by roger_1960 on 2012-04-28
Hi again

If its working with your phone, the wifi is OK and it is likely to be a router setting.

---

### Post by bj44 on 2012-04-29
I have the same problem and this is an Ubuntu 12.04 issue and not the router. I dual boot with Linux Mint 12 (same router setup and same USB Wireless stick) and it works fine.
Ubuntu simply does not "wake-up" the USB wireless stick during start up **ONLY** (no light blinks on the stick). For me, one way to get it to work is logon to Ubuntu first then plugin the USB wireless stick. Hope that helps.

Regards,

---

### Post by vishwasharitsya on 2012-04-29
Thanks roger_1960 and bj44 for your input.

I finally found out that it's a problem with the router indeed as I was able to connect to the wireless network at work from ubuntu 12.04.

By the way, the router/modem I use is Aztech HW-550-3G in Dubai.

Would be greatly appreciated if any of you have come across this issue before and help me.

Thanks,
Vishwas

---

