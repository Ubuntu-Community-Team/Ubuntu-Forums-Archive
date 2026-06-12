---
title: "Lenovo Y560 with i7 and ATI Madison [Mobility Radeon HD 5730 / 6570M] very loud"
date: 2018-05-30
forum: New to Ubuntu
---

### Post by richardericharde on 2018-05-30
Hi at all,

I'&#7743; happy to became an ubuntu User but unfortunately the settings seem not to be right. 
The Fan of my Laptop is running at very high speed, the Temperature is in between 65..82 degrees C and I just cleaned my Laptop to prevent overheating.

richard@elRicharde-Ubuntu:~$ sudo update-pciids #optional command, requires internet
[sudo] Passwort für richard: 
Downloaded daily snapshot dated 2018-05-25 03:15:01
richard@elRicharde-Ubuntu:~$ lspci -nn | grep -E 'VGA|Display'
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5730 / 6570M] [1002:68c0]


[HTML]richard@elRicharde-Ubuntu:~$ inxi -Fz
System:    Host: elRicharde-Ubuntu Kernel: 4.15.0-22-generic x86_64 bits: 64 Desktop: Gnome 3.28.1
           Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: LENOVO product: IdeaPad Y560 v: Rev 1.0 serial: N/A
           Mobo: Lenovo model: KL3 v: Rev 1.0 serial: N/A BIOS: LENOVO v: 30CN71WW date: 01/28/2011
CPU:       Quad core Intel Core i7 Q 720 (-MT-MCP-) cache: 6144 KB
           clock speeds: max: 1600 MHz 1: 1734 MHz 2: 1899 MHz 3: 1966 MHz 4: 1998 MHz 5: 1779 MHz
           6: 2046 MHz 7: 1930 MHz 8: 1741 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Madison [Mobility Radeon HD 5730 / 6570M]
           Display Server: x11 (X.Org 1.19.6 ) drivers: fbdev,ati (unloaded: modesetting,vesa,radeon)
           Resolution: 1024x768@76.00hz
           OpenGL: renderer: llvmpipe (LLVM 6.0, 128 bits) version: 3.3 Mesa 18.0.0-rc5
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series]
           driver: snd_hda_intel
           Card-2 Intel 5 Series/3400 Series High Def. Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-22-generic
Network:   Card-1: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) driver: ath9k
           IF: wlp5s0 state: up mac: <filter>
           Card-2: Broadcom Limited NetLink BCM57780 Gigabit Ethernet PCIe driver: tg3
           IF: enp9s0 state: down mac: <filter>
Drives:    HDD Total Size: 120.0GB (6.7% used)
           ID-1: /dev/sda model: Corsair_Force_3 size: 120.0GB
Partition: ID-1: / size: 110G used: 7.6G (8%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 77.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 263 Uptime: 53 min Memory: 3170.2/7909.3MB Client: Shell (bash) inxi: 2.3.56 
[/HTML]

There is typical Newbee Questions here:

- what could be the reason? (Under Win it runs quietly)
- how to figure out the reason
- how to fix it

Would be great to here from anybody soon, as I would like to stick with ubuntu.

BEst regards
Richarde

---

### Post by ragstosacs on 2019-04-23
Are you still happy? I've seen so many people with the same issue (eg. : [https://ubuntuforums.org/showthread.php?t=2355643](https://ubuntuforums.org/showthread.php?t=2355643) this guy has the same problem on the same device like two of us and he just doesn't know it yet) it hasn't been resolved in any case of course. Among your *unloaded* drivers you have- 
```
modesetting,vesa,radeon
``` and in addition to that I have ```
amdgpu
``` just to let me know that there's really no hope
If you look up "fbdev" "ati" "76Hz" you'll find many other poor souls struggling with their amd drivers
and I was able to find your post many times by looking up the details of my device but now I can't even
find your post via any search engine it's a good thing I had saved a link for it last year just to
see if eventually someone would try and help but of course now I can only use it for bitching about this 
mess that we're in. The older drivers used to work. I know that because I've tried a really old version
of "Slax" and it uses some old generic opensource drivers and it wasn't even able to recognize my card precisely
because it had been identified as radeon 5000 series but I could change the resolution to whatever
using ```
xrandr
``` and everything ran like it would with functional drivers. We could've switched to Ubuntu 14.04 and 
used proprietary drivers because it was the last supported version for fglrx but it has reached
end of life in April and now we can't get security updates which are very necessary I've been told.
I have been using another device with an Intel GPU on a live session so I have missed many security 
updates on that for a few years now one and nothing has happened as far as I can tell but I can't risk it 
with this Lenovo y560 because I wanted to fix it for someone else. I think it's the newer drivers or kernel
or something about the newer versions that messes everything up. I'm either looking at this unchanging
aspect ratio  with a lot of unloaded drivers just like I do in windows or the screen goes blank.
I've tried entering [HTML]radeon.dpm=1[/HTML]
```
xforcevesa
``` ```
radeon.modeset
``` in front of or instead of quiet splash and I've updated the kernel
to 5.09 and it hasn't made a difference.

---

### Post by wildmanne39 on 2019-04-23
Hello and welcome to the forum ragstosacs, please start your own thread for support instead of posting in someone elese's that way you can both get the help you need and it does not create confusion for those involved.

Thanks!

Old Thread Closed!

---

