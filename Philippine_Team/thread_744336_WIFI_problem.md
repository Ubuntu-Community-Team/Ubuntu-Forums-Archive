---
title: "WIFI problem"
date: 2008-04-03
forum: Philippine Team
---

### Post by ayanph on 2008-04-03
Got myself a Linksys WRT54G broadband router... installed it and followed the directions and got it to work with the two SE P990i phones at home and the PSP but when I tried using it with my MSI Laptop running Ubuntu... it was detected but I can't seem to connect to it!

Here's what I'm doing so far...

1. I install the wifi tools for ubuntu

sudo apt-get install wireless-tools

2. Tried identifying what card I have

lspci

and got

04:09.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

3. I tried checking with the wifi tools

iwconfig

lo no wireless extensions.

eth0 no wireless extensions.

ra1 RT61 Wireless ESSID:"DeatoWIFI" Nickname:""
Mode:Managed Frequency:2.462 GHz Access Point: 00:1E:E5:48:47:77
Bit Rate=54 Mb/s
RTS thr:off Fragment thr:off
Link Quality=100/100 Signal level:-38 dBm Noise level:-79 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ppp0 no wireless extensions.

I learned two things...

- That the wireless card on my laptop is using RT61 chipset driver
- That it is detecting the AP but I just need to make sure that the driver is properly installed.

Any suggestions guys?

---

### Post by dodimar on 2008-04-03
Sir, some post I na nakita ko. Katulad ng chipset ng wifi nyo...

[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

---

