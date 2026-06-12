---
title: "Lubuntu- No games will start."
date: 2016-10-26
forum: New to Ubuntu
---

### Post by ator60 on 2016-10-26
I just installed Lubuntu 16.10, and setting it up. When I click on Openarena it flashes a symbol on the screen, then nothing. The same with Sauerbraten, & Foobillard. I have installed the Nvidia driver for my graphics board. Here are my specs:

doofus@doofus-MS-7693:~$ inxi -F
System:    Host: doofus-MS-7693 Kernel: 4.8.0-26-generic x86_64 (64 bit)
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 16.10
Machine:   Mobo: MSI model: 970A-G46 (MS-7693) v: 2.0
           BIOS: American Megatrends v: V2.6 date: 10/08/2013
CPU:       Quad core AMD FX-8120 Eight-Core (-HT-MCP-) cache: 8192 KB 
           clock speeds: max: 3100 MHz 1: 1400 MHz 2: 1400 MHz 3: 1400 MHz
           4: 1400 MHz 5: 1400 MHz 6: 1900 MHz 7: 1400 MHz 8: 2800 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: N/A GLX Version: N/A
Audio:     Card-1 NVIDIA High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.8.0-26-generic
Network:   Card-1: ADMtek NC100 Network Everywhere Fast Ethernet 10/100
           driver: tulip
           IF: enp3s6 state: down mac: 00:04:5a:74:44:04
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full
           mac: 44:8a:5b:5d:99:89
Drives:    HDD Total Size: 500.1GB (2.8% used)
           ID-1: /dev/sda model: ST3500413AS size: 500.1GB
Partition: ID-1: / size: 91G used: 5.4G (7%) fs: ext4 dev: /dev/sda7
           ID-2: swap-1 size: 8.53GB used: 0.00GB (0%) fs: swap dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 22.9C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 217 Uptime: 1:02 Memory: 745.0/7932.7MB
           Client: Shell (bash) inxi: 2.3.1 
doofus@doofus-MS-7693:~$

---

### Post by mastablasta on 2016-10-27
run it from terminal and see what kind of errors you get. you can post result here. use the code tag (the # icon in "Go advanced" mode)

---

### Post by oldos2er on 2016-10-27
> Display Server: X.Org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa) says you're using the nouveau drivers. You should install the Nvidia drivers using the Additional Drivers tool.

---

