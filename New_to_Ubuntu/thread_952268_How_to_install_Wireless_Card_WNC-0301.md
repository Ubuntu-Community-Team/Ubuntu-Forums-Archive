---
title: "How to install Wireless Card WNC-0301"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by jsmkbunch2000 on 2008-10-18
I am absolutely new to Ubuntu/Linux.  I justed installed Ubuntu for first time on an old PC.  I installed as a complete install and did not keep the old Windows XP OS.  The wired works OK on the Network as I am using it to access the internet now, however, when I open the Network Manager, I don't see an option to view Wireless Connections.  Only appears to have Wired and Point to Point.

I read up a little in forums on attempting to install the wireless card, but get no where when attempting any of the suggestions.  Please help.  Here is a copy of the lspci -nn:

00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 12)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 12)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 12)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 12)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 12)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 12)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 12)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 SE] [1002:5964] (rev 01)
01:00.1 Display controller [0380]: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) [1002:5d44] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
02:0d.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)

---

### Post by rael_the_sand_man on 2008-10-19
ok so the last pci device listed on your lspci list would be your wireless card. However you wont really need any of the information listed there unless you dont have the original drivers that came with the card. If you do then good. First, connect to you wired internet and use synaptic package manager to download ndiswrapper-utils onto your computer. Open console and check to make sure that ndiswrapper is installed by running it or trying to view its man pages. After that your going to want to get the drivers for your wireless card and copy them to a folder on your computer there should be at least a .inf file and possible one or more .sys files. Then using the command "cd" in the console move to that folder and run the command **ndiswrapper -i "drivername".inf** then check to make sure that the driver installed works by running ndiswrapper -l. The output should read something like **driver installed : hardware present driver present** it may possible mention an alternate driver which you will want to blacklist. If thats your output then that means ndiswrapper recognizes the driver and the hardware and beleives it can drive the hardware properly. then make sure that ndisrapper is loaded by typing sudo modprobe ndiswrapper. after all that your wirless card should show up in your configuration menu. if you run into any problems check this sticky out [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by DJ Scribblinni on 2008-10-19
Here's a guide to using ndiswrapper, which you'll need to do with your card. [http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847")

If you don't have access to drivers, or they may be outdated, check out this link [http://global.level1.com/technical.php?Id=16&Type=All&SearchName=WNC-0301]("http://global.level1.com/technical.php?Id=16&Type=All&SearchName=WNC-0301")

If by chance you still have issues, I also recommend taking a glance at this thread here which dealt with a similar card to yours.
[http://ubuntuforums.org/showthread.php?t=712935]("http://ubuntuforums.org/showthread.php?t=712935")

---

### Post by oldsoundguy on 2008-10-19
how I did it:

Shut down the computer.
Put D-Link DWL 520G card into slot. (15 bucks on eBay)
Turned the computer back on. 
Went to the system> administration> network tools>
Plugged WEP password into the required place.
Opened browser and went on line.

Sure a lot easier when you have a card that works out of the box.

---

### Post by jsmkbunch2000 on 2008-10-19
Ok, this worked as far as I can tell.  Now how do I use the Wireless Network?  I use a D-Link DI-514 Router.  Not sure how to point to the wireless now and connect.

---

