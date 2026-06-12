---
title: "The mechanism of remembering the brightness of the monitor"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by tamir2 on 2014-03-31
Why  Ubuntu will not make the mechanism of remembering the brightness of the  monitor? What is the reason? And how to bring this desire to  developers?

---

### Post by PartisanEntity on 2014-03-31
Hi there, which version of Ubuntu are you using ? And could you please also tell us a little more about your hardware?

---

### Post by tamir2 on 2014-03-31
Using Ubuntu 14.04, laptop, AMD A6-4400M+AMD HD 7670m, Sagate 500Gb
tr@lp:~$  inxi -v5
System:    Host: lp Kernel: 3.13.0-20-generic x86_64 (64 bit, gcc: 4.8.2) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: SAMSUNG product: 355V4C/356V4C/3445VC/3545VC version: P09AAN.031.CP
           Mobo: SAMSUNG model: NP355V5X-S01RU version: BOARD 00 Bios: American Megatrends version: P09AAN date: 07/04/2013
CPU:       Dual core AMD A6-4400M APU with Radeon HD Graphics (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 10780.6 
           Clock Speeds: 1: 2400.00 MHz 2: 1400.00 MHz
Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Trinity [Radeon HD 7520G] bus-ID: 00:01.0 
           Card-2: Advanced Micro Devices [AMD/ATI] Thames [Radeon HD 7500M/7600M Series] bus-ID: 01:00.0 
           X.Org: 1.15.0 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1366x768@60.1hz 
           GLX Renderer: Gallium 0.4 on AMD ARUBA GLX Version: 3.0 Mesa 10.1.0 Direct Rendering: Yes
Audio:     Card-1: Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel bus-ID: 00:14.2 
           Card-2: Advanced Micro Devices [AMD/ATI] Trinity HDMI Audio Controller driver: snd_hda_intel bus-ID: 00:01.1 
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-20-generic
Network:   Card-1: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k bus-ID: 03:00.0
           IF: wlan0 state: down mac: e8:03:9a:fd:4b:7e
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: d000 bus-ID: 02:00.0
           IF: eth0 state: down mac: b8:88:e3:5f:b8:06
Drives:    HDD Total Size: 1500.3GB (49.7% used) 1: id: /dev/sda model: ST500LM012_HN size: 500.1GB temp: 43C 
           2: USB id: /dev/sdc model: My_Passport_074A size: 1000.2GB temp: 0C 
           Optical: /dev/sr0 model: N/A rev: N/A dev-links: cdrom
Partition: ID: / size: 15G used: 4.8G (34%) fs: ext4 dev: /dev/sda5 
           label: N/A uuid: dbd54438-a01c-4b39-ac04-fe36d66bfa2a
           ID: /home size: 440G used: 17G (4%) fs: ext4 dev: /dev/sda6 
           label: N/A uuid: fdcc39e4-f84d-4d32-991f-0d3d3d24d5de
           ID: swap-1 size: 4.29GB used: 0.00GB (0%) fs: swap dev: /dev/sda1 
           label: N/A uuid: e91b4d2b-f860-44d3-b3c2-88504ce6c6d8
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 49.1C mobo: N/A gpu: 47.0,-128.0 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 194 Uptime: 1:58 Memory: 2608.3/3725.2MB Runlevel: 2 Gcc sys: 4.8.2 
           Client: Shell (bash 4.3.0) inxi: 1.9.17 
tr@lp:~$

---

### Post by PartisanEntity on 2014-03-31
It says you are using Ubuntu 14.04. That is still in Beta, and the final version has not been released yet. I would strongly suggest you wait until 14.04 has been released and then use that to set up a live system. While not much may change at this point, I still think it would be wasted energy to invest time and effort in setting up a Beta version.

---

### Post by tamir2 on 2014-03-31
On 12.04 and 13.10 the same thing I thought might be to ask the  developers to begin thinking in this direction, since many people  complain that there is no such mechanism "out of the box".

---

### Post by PartisanEntity on 2014-03-31
That's true. If you search the forum you will see that others have raised the issue here and found solutions that worked:
[http://ubuntuforums.org/showthread.php?t=1503813](http://ubuntuforums.org/showthread.php?t=1503813)

---

### Post by tamir2 on 2014-03-31
[**[COLOR=#C61919][B]PartisanEntity**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=192328")
Thanks for the link, but it's all "the crutches", I would like to make  everything work right after installation system ("out of the box"). For  example, in Kubuntu such mechanism exists for a long time, why not to do  the like in Ubuntu? how to convey this message to the developers?

---

### Post by Elfy on 2014-03-31
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

Mailing list

---

### Post by tamir2 on 2014-03-31
**[[B][COLOR=#990303][B]Elfy**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=610428")[/B]
Thank you, in General, the question is solved)

---

