---
title: "Recent slow downs / trouble troubleshooting"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by jspidle on 2013-06-20
Probably my larger problem is that I'm not sure where to look. But recently, my system has been running really slow. In particular, the system frequently locks up when moving to different workspaces using a keyboard shortcut, or editing audio using Audacity or opening Clementine. I run a very powerful computer and it has always blazed with Ubuntu, so I'm not sure what's going on. I haven't made any recent hardware changes (Core i7 2700k 3.5 GHz, 8GB RAM, Radeon 4580 graphics) and aside from the standard updates, the most recent software installed is Spotify, Calibre, Google Music Manager, Netflix Desktop and UberWriter. I thought of removing these but it just seems like they shouldn't be the issue. Like I said, Ubuntu ran like a dream when I first installed it.

Here's some info. If anyone has any ideas, I'd greatly appreciate it. Thanks.

[U][B]KERNEL
[/B][/U]Linux thekiosk 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

_**HARDWARE**_
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1c.6 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 7 (rev c4)
00:1c.7 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV770 [Radeon HD 4850]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV770 HDMI Audio [Radeon HD 4850/4870]
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
05:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
06:00.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
07:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
08:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller

_**RUNNING PROCESSES (with Audacity running, since this is when it seems to lock up the most)**_
```

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND                                                                                                                                  
20432 panoptic  20   0  623m  37m  23m S   8.0  0.5   1:00.47 gnome-system-mo                                                                                                                          
 1305 root      20   0  284m  78m  31m S   3.3  1.0   1:19.09 Xorg                                                                                                                                     
 2827 panoptic  20   0 1537m  60m  26m S   3.0  0.8   0:44.92 audacity                                                                                                                                 
 1940 panoptic  20   0  705m  34m  17m S   2.0  0.4   0:00.96 guake                                                                                                                                    
 1911 panoptic  20   0 1545m 131m  38m S   1.7  1.7   0:55.92 compiz                                                                                                                                   
 3859 panoptic  20   0  986m  78m  21m S   1.0  1.0   0:04.10 chrome                                                                                                                                   
 2824 panoptic  20   0  870m  45m  15m S   0.7  0.6   0:12.48 transmission-gt                                                                                                                          
   10 root      20   0     0    0    0 S   0.3  0.0   0:04.18 rcu_sched                                                                                                                                
  283 root      20   0     0    0    0 S   0.3  0.0   0:03.55 kworker/u:6                                                                                                                              
 1925 panoptic  20   0 1302m  49m  20m S   0.3  0.6   0:01.95 variety                                                                                                                                  
 1941 panoptic  20   0  887m  35m  13m S   0.3  0.4   0:08.48 autokey-gtk                                                                                                                              
 2391 panoptic  20   0  347m  14m  10m S   0.3  0.2   0:01.00 gtk-window-deco                                                                                                                          
 2814 panoptic  20   0 1019m 181m  54m S   0.3  2.3   1:10.28 chrome    

```

---

### Post by acimi66 on 2013-06-20
Did you upgrade versions recently?

---

### Post by jspidle on 2013-06-21
I did a clean install of 13.04, which ran fine for a few weeks.

---

