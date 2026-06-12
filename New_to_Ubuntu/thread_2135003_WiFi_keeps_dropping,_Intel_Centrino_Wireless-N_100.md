---
title: "WiFi keeps dropping, Intel Centrino Wireless-N 1000"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by supratroopa on 2013-04-12
I've been using Ubuntu 12.10 for several months now, and a problem I've had since the beginning is that the WiFi keeps dropping the connection.
Every 7-10 minutes or so, the WiFi will disconnect from the network for about 5 seconds, and then automatically reconnect. It runs on a Lenovo Edge E520 laptop, if that helps.

Thanks!

---

### Post by mag1strate on 2013-04-12
What kind of wifi card does it use? According to the lenovo page, it could be any one of these:

-Intel® Centrino® Advanced-N + WiMAX ABGN
-Intel® Centrino® Wireless-N 1000
-ThinkPad b/g/n (Realtek) (1x1 GN)
-ThinkPad a/b/g/n (Broadcom) (2x2 AGN)

Once we figure this out, we can narrow down the search to fix the problem :D

---

### Post by supratroopa on 2013-04-12
Cool. I also looked at that page for clarification with regards to what WiFi device I had, but I don't know which one it is. Is there any way to find out?

---

### Post by rrich1974 on 2013-04-13
the output of a command named "lspci" will really help us to figure it out. 
terminal --> lspci

---

### Post by supratroopa on 2013-04-13
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07)
08:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

```

---

### Post by sandyd on 2013-04-13
probably
[https://bugs.launchpad.net/bugs/836250](https://bugs.launchpad.net/bugs/836250)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/939218](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/939218)

---

### Post by docJ on 2013-04-13
I have no business at all giving advice about Ubuntu, I will leave it to the highly capable hands here, but a fundamental question nags me: 
Do you have another wifi device at home? Does it also loose connectivity when Ubuntu does?
If so, you obviously don't want to mess around with Ubuntu; It could just be your router requiring an electrical reset.

---

### Post by supratroopa on 2013-04-13
Yeah, no problem on those devices. Doesn't even disconnect intermittently on my Windows 7 partition on the same laptop.

---

### Post by zrdc28 on 2013-04-13
Reinstall network-manager will probably solve your problem, go to synaptic and do a reinstall.

---

### Post by rrich1974 on 2013-04-14
you also can try to edit the connection by ignoring ipv6.

---

### Post by supratroopa on 2013-04-14
How do I get into synaptic?

---

### Post by rrich1974 on 2013-04-14
why do you want to get there? you dont need to get into synaptic to edit the connection. 
just click on network manager and edit connection or open terminal and write "nm-connection-editor"

---

### Post by mag1strate on 2013-04-14
There are known issues in ubuntu with that specific wireless card. Thank you for editing the title, it really does help.

I found these that apparently solved the problem that you are having:
[http://ubuntuforums.org/showthread.php?t=1941350](http://ubuntuforums.org/showthread.php?t=1941350)
[http://ubuntuforums.org/showthread.php?t=2122379](http://ubuntuforums.org/showthread.php?t=2122379)

---

### Post by supratroopa on 2013-04-14
Thanks for the reply! It seems that both those issues were fixed by replacing the iwlwifi driver with the one for kernel version 2.6.30.xx, instead of the default 3.2+ drivers. Ubuntu 12.10 runs on kernel 3.5.x.

---

