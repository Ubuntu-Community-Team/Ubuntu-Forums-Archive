---
title: "airmon-ng I can't kill few conflicting processes 11.04"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by nullpenguin on 2011-11-02
Hi to everybody,
I'm beginner on Ubuntu. I'd test my home wifi network. Someone suggest me to use Aircrack-ng tools witch can download from Ubuntu software center. I try use it
with 3com usb 3CRUSB10075 adapter on COMPAQ R4000 with 11.04 Ubuntu release. I follow few tutorials and read some articles, but I've got this problems when I followed the procedure.

screen0
====================================================
root@nullpenguin-laptop:/home/milton/Scaricati/aircrack-op/software/rt2570# airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
556    avahi-daemon
557    avahi-daemon
562    NetworkManager
2195    wpa_supplicant
2197    dhclient
Process with PID 2197 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan1        Broadcom    b43 - [phy0]
wlan0        ZyDAS 1211    zd1211rw - [phy2]
                (monitor mode enabled on mon2)
mon0        ZyDAS 1211    zd1211rw - [phy2]
mon1        ZyDAS 1211    zd1211rw - [phy2]
===================================================

Main question: There is someone who would suggest me how I can resolve my problems? Is RT2570 USB Ralink adapter the correct adapter witch I should use?
thanks

---

### Post by fractalman on 2011-11-02
You would probably be better off getting a copy of backtrack5.   Although the tools are available in the main ubuntu repositories its highly probable you will break your natty install, I've done that twice now with natty.  Backtrack 5 is just a different linux kernel but its designed specifically for penetration testing

[http://www.backtrack-linux.org/backtrack/backtrack-5-release/](http://www.backtrack-linux.org/backtrack/backtrack-5-release/)

i get a similar error message to yours but it's never really given me any major issues with airmon so i just ignored it, lol

as you are new to ubuntu please be aware that members are not allowed to discuss hacking on this forum, if you want to know more about cracking wifi you should try the backtrack forums really,

:D

---

### Post by nothingspecial on 2011-11-02
We don't support aircrack-ng here.

Closed.

---

