---
title: "the cycles of unwanted updates"
date: 2016-10-05
forum: Recurring Discussions
---

### Post by nigeldodd-gmail on 2016-10-05
For many years I was enthusiastic about updating to the latest Ubuntu. Then I got a Chromebase. Despite being a computer professional, the Chromebase does 98% of all I want. I can't scan, print, use a midi sequencer or music scoring software or process raw images from my camera.

When I return to Ubuntu for these occasional needs I am frustrated by the arcane nature of it all: the long boot times, the necessity to check the disk BEFORE you can log in instead of after you've finished, that even with long term OS installations you have to go through the worrying and time consuming process of updates every few years and that the Chrome browser becomes unsupported if you don't. 

Having experienced the 10 sec boot time and automatic updates of Chrome OS I really feel that Ubuntu has become bloated and overly complex over the years. There is virtue in simplicity. 

Therapy over!

---

### Post by cariboo on 2016-10-07
I'm not sure what type of hardware you have that takes a long time to boot, but my two year old system usually boots in under 10 seconds:

```
cariboo@skynet:~$ inxi -b
System:    Host: skynet Kernel: 4.8.0-17-generic x86_64 (64 bit)
           Console: tty 15 Distro: Ubuntu 16.10
Machine:   Mobo: ASUSTeK model: M5A97 R2.0 v: Rev 1.xx
           UEFI: American Megatrends v: 2201 date: 12/10/2013
CPU:       Quad core AMD FX-8350 Eight-Core (-HT-MCP-)
           speed/max: 1400/4000 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: N/A drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           tty size: 80x24 Advanced Data: N/A out of X
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 1240.3GB (30.7% used)
Info:      Processes: 300 Uptime: 10 days Memory: 3782.6/15942.2MB
           Init: systemd runlevel: 5 Client: Shell (bash) inxi: 2.3.1 
```

I just updated the kernel so boot time is a little bit slower than normal:

```
cariboo@skynet:~$ systemd-analyze
Startup finished in 198us (firmware) + 206us (loader) + 2.796s (kernel) + 9.362s (userspace) = 12.159s
```

---

### Post by monkeybrain20122 on 2016-10-07
It depends on your hardware. On my Toshiba Satellite Ubuntu 16.04 boots in 3 secs. :) I have never seen such fast boot. It came with Win8, the boot was fast, but not THAT fast. On an old hp pavilion (5 yrs?) and a six year old Dell  boot time was longer, about 15 ~ 20 secs, not that bad either. I have gone through many different laptops, never really have a complaint about boot time. 25 secs max.

---

