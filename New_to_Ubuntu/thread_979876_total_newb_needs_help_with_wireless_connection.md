---
title: "total newb needs help with wireless connection"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by andreas85dk on 2008-11-12
Today I installed Ubuntu 8.04 on my laptop. But for the past 4-5 hours I've been struckleling with setting up my wireless connection, which I use for accessing the internet.

My wireless card is Broadcom BCM4318 [AirForce One 54g] 802.11g Wireless LAN. So I went looking for the windows driver and now have bcmwl5.sys and bcmwl5.inf on the desktop. 
I have no idea where to start with the ndiswrapper, I've read that it's included in these new Ubuntu releases, but I can't find it anywhere. 
With my old XP setup, a button on the front on the laptop was lit during start-up, but that doesn't happen with Ubuntu. I guess it's because the card isn't properly installed... HELP!!!


Here's my **iwconfig** return:
[I]lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]


If you need it here's my **lspci** return:

[I]00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)[/I]



I really hope someone out there is able to help a ubuntu beginner. I've searched google, but every post surrounding this subject seems to date back to 2005-06... nothing recent

---

### Post by oilchangeguy on 2008-11-12
What's "struckleling"? Do you mean struggling? While a broadcom adapter can be made to work in linux, it's alot easier to just buy a usb wireless adapter. They will usually work right out of the box.

---

### Post by mapes12 on 2008-11-12
Try this: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I had problems with ndiswrapper and gave up. To solve the problem I bought a replacement wifi PCMCIA card that had native Linux driver support. Only cost me £10 and never looked back.  Have a look at these links:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

Good luck!

---

