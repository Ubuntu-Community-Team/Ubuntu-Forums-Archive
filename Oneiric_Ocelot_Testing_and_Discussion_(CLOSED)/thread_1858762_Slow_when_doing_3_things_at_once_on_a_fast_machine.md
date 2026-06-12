---
title: "Slow when doing 3 things at once on a fast machine"
date: 2011-10-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zedwards on 2011-10-13
I have a Sager NP8130 and Beta 2 with updates installed. I was copying files from an external USB 3 drive while importing photos to Shotwell from my pictures directory and one would think I was trying to make it save the world as Firefox, System monitor would freeze on me and Banshee wouldn't even start up. Now those 2 processes are done it's fine, but am wondering if there are any red flags with my setup and this version of Ubuntu that I should be concerned about? I REALLY don't want to use windows any more but so far things have been quite buggy. (linux user since 1999)

My setup is Sager NP8130  Intel® Core™ i7-2630QM | 8GB DDR3 SDRAM | Blu-ray Burner/DVD Super-Multi Drive | 750GB 7200rpm SATA 300 Hard Drive | Nvidia GeForce GTX 560M 

lspci: 
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 1251 (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0bee (rev a1)
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
03:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
03:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller

```

Anything

---

### Post by effenberg0x0 on 2011-10-13
I keep things open for 2-3 days, sometimes more, until I finally end up rebooting to apply an update, etc. My desktop has 8 viewports, most of them dedicated to specific apps that are opened 24/7. 

I have Eclipse and Gimp each on an exclusive viewport. 2 or 3 terminals plus gedit with 1 to 5 tabs in an exclusive viewport too. Another viewport exclusive to Firefox, which generally has 10-20 tabs opened/pinned. Thunderbird has it's exclusive place too. VirtualBox running a Win 7 Professional 64-bit has a viewport (The VM has 12GB of RAM and uses 6 cores with 90% Cap with 2d/3d Accel). And Clementine is always opened and generally is playing mp3s. 

Since I use preload with aggressive settings and no swapping (swappiness=0), my RAM usage is of about 1,5GB to 2GB plus 12GB (static) to the VM. My CPU cores are far from being stressed, running on "ondemand" governor at 40°C and no more than 10% to 30% on Core 0. And it's a less powerful CPU than yours (Phenom II X6 110T BE).

So, what you report, in my opinion, can only be caused by some Application or Hardware that, in that moment, was undergoing problems. There's a very big number of thing that could be related. 

Unfortunately, there's not much one can do without some hint. Ideally, we would have liked to see your var/log/dmesg or /var/log/syslog from the time when the failure was happening. 

You can browse to your /var/log directory and view the logs using gedit. Maybe if you search these files looking at the time when you first noticed the slowdown, you can easily spot some error / warning or unusual message in your logs. That would be a huge help.

Regards,
Effenberg

---

