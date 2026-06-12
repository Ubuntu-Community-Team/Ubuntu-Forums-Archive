---
title: "screen get frozen, but mouse moves what to do"
date: 2016-03-11
forum: New to Ubuntu
---

### Post by raadyhere on 2016-03-11
Ubuntu 14
Hi, 
I am a rare user for ubuntu . I have installed ubuntu 15.10
I have encountered a strange problem. I have two monitors. I have been using one monitor for web browsing(chrome) , and while I use suddenly the screen gets frozen. 
I am able to move the mouse but I cannot move out of the second/first screen (stays in the screen where I am using the mouse pointer) but not able to close or open any thing. I have browsed for closing non responsive windows by pressing alt+F2 , but even that doesnt work.
i have force stop my computer by hard press of power button to restart.

My question
1. I am familiar with windows press Alt+ctrl+del to go for task manager for closing an application. if so what is similar to that we do in ubuntu if something is not responding or safely close ubuntu ?
2. Is it the problem of my installing browser ? I downloaded 64 bit .deb file of chrome and installed ! When I downloaded ubuntu it recomended to download the 64 bit version of ubuntu and thats what i installed, so i installed 64bit .deb file of ubuntu instead of installing it from the software center. 

Please post any suggestions. 


Thanks
Raady

---

### Post by kc1di on 2016-03-11
Hi Raddy and Welcome to Ubuntu,
I'm not sure I can help with this one, but a little more info on your system may help. 
it you could go to a terminal and type this command and post the output here it would be a start.```
inxi -Fzx
```

---

### Post by raadyhere on 2016-03-11
KC1, thanks for your quick response, sorry for the my delayed reply.

Though I have reinstalled ubuntu problem still persists.  

I am posting the configuration 


 

System:    Host: raady-ESlab Kernel: 4.2.0-27-generic x86_64 (64 bit, gcc: 4.8.2) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: ASUS product: All Series
           Mobo: ASUSTeK model: B85M-G version: Rev X.0x Bios: American Megatrends version: 0703 date: 10/30/2013
CPU:       Quad core Intel Core i5-4670 CPU (-MCP-) cache: 6144 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 27197.8 
           Clock Speeds: 1: 2964.906 MHz 2: 2243.468 MHz 3: 2253.828 MHz 4: 3409.164 MHz
Graphics:  Card: NVIDIA GK106 [GeForce GTX 660] bus-ID: 01:00.0 
           X.Org: 1.17.2 drivers: nouveau (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Gallium 0.4 on NVE6 GLX Version: 3.0 Mesa 11.0.2 Direct Rendering: Yes
Audio:     Card-1: Intel 8 Series/C220 Series High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Card-2: NVIDIA GK106 HDMI Audio Controller driver: snd_hda_intel bus-ID: 01:00.1 
           Card-3: Logitech Webcam C270 driver: USB Audio usb-ID: 001-004 
           Sound: Advanced Linux Sound Architecture ver: k4.2.0-27-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: d000 bus-ID: 03:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1256.3GB (0.4% used) 1: id: /dev/sda model: Samsung_SSD_840 size: 256.1GB temp: 0C 
           2: id: /dev/sdb model: WDC_WD10EZEX size: 1000.2GB temp: 32C 
Partition: ID: / size: 36G used: 4.2G (13%) fs: ext4 ID: swap-1 size: 4.10GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C gpu: 34.0 
           Fan Speeds (in rpm): cpu: 0 
Info:      Processes: 201 Uptime: 8 min Memory: 883.3/7922.7MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17

---

### Post by kc1di on 2016-03-12
One thing I see you have Nvidia Graphics Card those can sometimes cause problems with the default Nouveau Driver. 
you may need, if you haven't already done so, to install the Nvidia driver for your card.  
You can do that by going to software center > Additional drivers tab.  Allow it a few minutes to check you machine and it should offer you the correct driver for
your card.  Good Luck.

---

