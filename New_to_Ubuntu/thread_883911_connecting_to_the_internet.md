---
title: "connecting to the internet"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by jimistephen on 2008-08-08
hello, 
  i just put ubuntu hardy on my laptop and now i can not connect to the internet either through the Ethernet port or the wireless card. I've been searching around for two days looking for a way to get either one to connect but i can't find any thing. could somebody please help...

---

### Post by raul_ on 2008-08-08
Could you give some more details? What cards are you using, what exactly is the problem, and maybe post the output of 'ifconfig'

---

### Post by jimistephen on 2008-08-08
sure, i'm sorry

if config
eth0 link encap:Ethernet  HWaddr 00:1b:24:3a:37:d4
UP RUNNING BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
RX packets:2308 errors:0 dropped:0 overruns:0 frame:0
TX packets:115 ettors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuilen:1000
RX bytis:106732 (104.2 kb) TX bytes: 11582 (11.3 kb)
Interrupt: 16

Eth0:avahi Link encap:ethernet HWaddr 00:1b:24:3a:37:d4
inet addr:169.254.6.18 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNIN MULTICAST MTU:1500 Metric:1
interrupt:16

lo  link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1586 errors:0 dropped:0 overruns:0 frame:0
TX packers:1586 errors:0 dropped:0 overruns:0 carrier:0
collision:0 txqueuelen:0
Rx bytes:80050 (78.1 KB) Tx bytes:80050 (78.1 KB)


that's all it says and that was hooked up to my Motorola surfboard 5101 cable modem, which usually runs into a linksys wireless router mod. WRT54G V8.2 the Ethernet is the on board port in the computer which is an Acer 3680 the wireless card is a Broadcom BCM94311MCG that sits in an pci mini slot directly under the access panel in my laptop. there is a switch on the front of my laptop that used to turn the card on and off when the computer still had vista on it, and now it wont turn it on.

---

### Post by raul_ on 2008-08-08
Well, the wireless card is clearly not working. You'll have to search for 'Broadcom' in the forums, I think you'll find some instructions to get your card working. As for the ethernet, my guess is that it's misconfigured. I think you'll have to set up the correct IP and/or DNS settings, but I reckon that I'm no networking guru :(

You could try to do that with networkmanager (i think it comes with Ubuntu by default), using the icon that appears in the system tray. If there's no icon, try running 'nm-applet'

---

### Post by jimistephen on 2008-08-08
ok stupid question
where would i find the ip and the dns, mainly the dns

---

### Post by raul_ on 2008-08-08
If you have a working connection in your house, or maybe in XP(?) you could copy the settings, otherwise, chck with your ISP, or with the papers they gave you

---

### Post by jimistephen on 2008-08-08
ok, now i tried a manual config of the network and it asked for a wpa password, but i don't have one, and it wont let me go on

---

### Post by okey666 on 2008-08-08
wpa is wireless network security. You may have set it, or it may be written on your wireless router. Or you may be able to access the configuration pages of your router from another computer. Look in the routers instruction manual.

---

### Post by st33med on 2008-08-08
Hello. Could you post the output of this:
```
lspci | grep Ethernet
lspci | grep Network
```

---

### Post by jimistephen on 2008-08-08
sure
 lspci | grep Ethernet is
02:00.0 Ethernet controller: Marvell Technology Group Ltd. PCI-E Fast Ethernet Controll (rev14)

lspci | grep Network is
03:00.0 Network controller: Broadcom Corporation BCM74311MCG wlan mini-pci (rev01)

also i did a iwconfig which came back as
lo no wireless extensions.
eth0 no wireless extensions.
wmaster0 no wireless extensioins
wlan0 IEEE 802.11g ESSID "linksys"
Mode: managed Channel:0 access point: not-associated
Tx-power=0 dBm
Retry min limit:7 RTS thr:off Fragment thr=2346 B
Link uality:0 Signal level:0 noise level:0 
Rx invalid nwid: Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 invalid misc:0 Missed beacon:0

---

### Post by st33med on 2008-08-08
I can help with the wireless card. [Go here]("http://ubuntuforums.org/showthread.php?t=760568") for help with your Broadcom card.

As for your Ethernet, I can't really help there. Sorry!

---

### Post by jimistephen on 2008-08-09
okay, i've been working on this for a while, and i went to the link that st33med said, my only problem is that i downloaded the driver for it on a windows machine and it made me unzip before i could put it on a flash drive so ubuntu says cannot find or open r151518.exe, r151518.exe.zip or r 151519.exe.ZIP, and it's on a flash drive not a cd so what should i put in command line instead of cd???

---

