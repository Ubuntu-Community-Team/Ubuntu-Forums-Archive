---
title: "splash screen freeze at start up"
date: 2018-03-19
forum: New to Ubuntu
---

### Post by dalwk on 2018-03-19
Hi I just installed Ubuntu 17.10 in my laptop. When I reboot my laptop it just stops at splash screen. I tried several methods I found on the forum it still didn't work. 

Here's what I got from boot repair [http://paste.ubuntu.com/p/SFxqGrWwdK/](http://paste.ubuntu.com/p/SFxqGrWwdK/)

---

### Post by dalwk on 2018-03-19
screenshot of the spec, I tried changing it to the open source graphic driver it still didn't work

---

### Post by ajgreeny on 2018-03-19
I am not sure how you tried to add the screenshot image to post #2 but it did not work, just showing a lot of alphanumeric garbage, so I removed it.

Please save a screenshot to your hard drive then add it to your post using the paperclip in the toolbar and navigating to the saved image.
Even better, install inxi if you do not have it and then show us the output of ```
inxi -F
``` in terminal.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

It may also be worth running the **Boot-info script** which you can find details of in **Boot-Repair** in my signature below.
Do not at this stage run the default repair but simply show us the pastebin link you are given for the output of the script.

---

### Post by dalwk on 2018-03-19
Hi, here's the output from boot-info [http://paste.ubuntu.com/p/NGympRdjKt/](http://paste.ubuntu.com/p/NGympRdjKt/)

Also the the output from inxi

```
 
System:    Host: amnesia Kernel: 4.13.0-37-generic x86_64 bits: 64
           Desktop: Gnome 3.26.2 Distro: Ubuntu 17.10
Machine:   Device: portable System: Dell product: Inspiron 11-3162 v: 1.0.3 serial: N/A
           Mobo: Dell model: 0FCNP5 v: A00 serial: N/A
           UEFI: Dell v: 1.0.3 date: 01/21/2016
Battery    BAT0: charge: 12.9 Wh 57.4% condition: 22.4/32.0 Wh (70%)
CPU:       Quad core Intel Pentium N3700 (-MCP-) cache: 1024 KB
           clock speeds: max: 2400 MHz 1: 1600 MHz 2: 1600 MHz 3: 1600 MHz
           4: 1600 MHz
Graphics:  Card: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
           Display Server: wayland (X.Org 1.19.5 ) driver: i915
           Resolution: 1366x768@59.98hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 405 (Braswell)
           version: 4.5 Mesa 17.2.8
Audio:     Card Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Def. Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.13.0-37-generic
Network:   Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k
           IF: wlp1s0 state: up mac: 44:1c:a8:32:5f:59
           Card-2: Atheros
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 500.1GB (1.8% used)
           ID-1: /dev/sda model: TOSHIBA_MQ01ABF0 size: 500.1GB
Partition: ID-1: / size: 453G used: 4.7G (2%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 705M used: 145M (23%) fs: ext4 dev: /dev/sda2
           ID-3: swap-1 size: 4.19GB used: 0.00GB (0%)
           fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 65.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 275 Uptime: 20 min Memory: 2437.4/3843.7MB
           Client: Shell (bash) inxi: 2.3.37 


```

---

