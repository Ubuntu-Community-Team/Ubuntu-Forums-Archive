---
title: "Unity very slow after a use"
date: 2016-02-03
forum: New to Ubuntu
---

### Post by hilbert_van_pelt on 2016-02-03
hi all,

I just installed ubuntu 14.04 on a machine and I am having some issues with unity.
When I boot the machine I have no problems and everything work smoothly. But after a certain time the machine becomes very sluugish to react, like it is swapping, which it isn't. 
I have 2 NVS 295 nvidia graphics cards and a intel xeon processor, so enough computing power.

I have tried both the nouveau driver and the nvidia driver and both seem the to be slow. I have also run with both swap on and off and the problem still persists. 
I am not 100 percent sure but it look like to be related to firefox, since if I do not boot firefox it seems to remain smooth, but I can be imagining this. 

I am out of idea's on what to try, does anybody have an other idea of what to try?

Cheers

---

### Post by v3.xx on 2016-02-03
Hi hilbert

Please post your complete system specs.  Open a terminal and enter:

```
inxi -b
```

Also you can monitor processes in terminal with the command:

```
top
```

and your ram with:

```
free -m
```

---

### Post by HermanAB on 2016-02-03
It doesn't help guessing and trying things - poking around in the dark - that is the Microsoft way.

Run 'top' and 'ntop' and see what is going on.

---

### Post by hilbert_van_pelt on 2016-02-03
he all, thanks for the replies.

I know that poking around in the dark is the microsoft way, but if i don't know what the problem is and all the obvious solutions don't work i don't know what else to do.

Inxi -b gives:
```
System:    Host: hilbertpc Kernel: 3.19.0-49-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Hewlett-Packard product: HP Z600 Workstation
           Mobo: Hewlett-Packard model: 0B54h version: D Bios: Hewlett-Packard version: 786G4 v03.57 date: 07/15/2013
CPU(s):    2 Hexa core Intel Xeon CPU X5650s (-HT-MCP-SMP-) clocked at 2661.00 MHz 
Graphics:  Card-1: NVIDIA G98 [Quadro NVS 295] 
           Card-2: NVIDIA G98 [Quadro NVS 295] 
           X.Org: 1.17.1 drivers: nvidia,nouveau (unloaded: fbdev,vesa) Resolution: 1680x1050@60.0hz, 1920x1080@60.0hz 
           GLX Renderer: Quadro NVS 295/PCIe/SSE2 GLX Version: 3.3.0 NVIDIA 340.96
Network:   Card-1: Broadcom NetXtreme BCM5764M Gigabit Ethernet PCIe driver: tg3 
           Card-2: Broadcom NetXtreme BCM5761 Gigabit Ethernet PCIe driver: tg3 
Drives:    HDD Total Size: 2160.4GB (18.2% used)
Info:      Processes: 317 Uptime: 23:03 Memory: 5885.1/24092.5MB Client: Shell (bash) inxi: 1.9.17
```

running top i get
```

top - 09:28:52 up 23:09,  6 users,  load average: 14.13, 14.71, 13.81
Tasks: 312 total,   8 running, 304 sleeping,   0 stopped,   0 zombie
%Cpu(s): 39.7 us, 30.7 sy,  0.0 ni, 29.1 id,  0.0 wa,  0.0 hi,  0.5 si,  0.0 st
KiB Mem:  24670728 total,  8285344 used, 16385384 free,   420012 buffers
KiB Swap:        0 total,        0 used,        0 free.  1986788 cached Mem
```



And with free -m I get the following:
```

             total       used       free     shared    buffers     cached
Mem:         24092       8110      15982        174        410       1940
-/+ buffers/cache:       5759      18332
Swap:            0          0          0
```

If you can spot the problem I am all ears

---

