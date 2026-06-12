---
title: "wifi connection detected + occasionally not effective"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by al.adab on 2012-02-04
hello,

I'm on Xubuntu 11.10. Occasionally, both Firefox and Chrome show a blank/no connection available page after booting the pc, though the wifi manager shows that a connection has been established.

The problem is solved by re-booting the pc. I tried a couple of times to wait a few minutes before re-booting to see if things get back in place, but they don't. 

It's not a major issue, though it'd be great if there were a solution. I tried to google it, etc, but only found someone who has a similar problem (ie, the connection stops working minutes after connecting). 

If it's of any help, I'm on a ThinkPad T42 and this is my *lspci*

:[I]~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)[/I]

Thank you

---

### Post by Bodsda on 2012-02-04
> **al.adab said:**
> hello,

I'm on Xubuntu 11.10. Occasionally, both Firefox and Chrome show a blank/no connection available page after booting the pc, though the wifi manager shows that a connection has been established.

The problem is solved by re-booting the pc. I tried a couple of times to wait a few minutes before re-booting to see if things get back in place, but they don't. 

It's not a major issue, though it'd be great if there were a solution. I tried to google it, etc, but only found someone who has a similar problem (ie, the connection stops working minutes after connecting). 


Thank you

Hi,

When your browser wont connect, can you successfully ping [www.google.com]("http://www.google.com") or its IP address?

Bodsda

---

### Post by al.adab on 2012-02-04
would you do by typing *ping google.com* on terminal? I've never tried. Will have to wait till it happens again...

---

### Post by Mahkoe on 2012-02-04
I have this problem too. I've been looking for a permanent solution, but, for now I have a short-term solution;
```
sudo iwconfig wlan0 txpower off
sudo iwconfig wlan0 txpower on
```
This turns off and turns back on your wireless hardware. This solves the problem until it appears again... but it should save you a lot of frustration until we can track this problem down.

---

### Post by al.adab on 2012-02-04
thanks Mahkoe! I'll definitely use your solution - hopefully a fix is found soon :)

---

