---
title: "Crashes"
date: 2018-12-05
forum: New to Ubuntu
---

### Post by ray9 on 2018-12-05
Hello.  I just installed Ubuntu 18.04 1 LTS.  I have crashes when right clicking on the  Firebird icon "Add new window".  The box that comes up and won't go back down and seems to freeze everything.  Also, Facebook Messenger is crashing in the same way but it doesn't freeze the entire system.  How can I fix this?

Thanks

---

### Post by Autodave on 2018-12-05
Can you give us some specs on your machine?  Have you installed any video driver?  If so, what one and where did you get it from?

---

### Post by ray9 on 2018-12-05
Thanks for the reply.  I have a HP Pavillion G7 Notebook with a 245 Gig SSD, AMD A8-4500m apu with  Radeon hd graphics x 4, AMD Aruba.

---

### Post by NM5TF on 2018-12-07
@Ray9.....

please post the output of

```
inxi -F
```

use code tags to make the output more readable.....

select the adv reply button & paste the output between the # icons

tommy

---

### Post by ray9 on 2018-12-08
I don't know what "code tags" are.

```
HP-Pavilion-g7-Notebook-PC:~$ inxi -F
System:    Host: ray-HP-Pavilion-g7-Notebook-PC Kernel: 4.15.0-42-generic x86_64
           bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: Hewlett-Packard product: HP Pavilion g7 Notebook PC v: 088A120000305910000620100 serial: N/A
           Mobo: Hewlett-Packard model: 184B v: 57.35 serial: N/A
           UEFI: Insyde v: F.27 date: 04/12/2013
Battery    BAT0: charge: 47.2 Wh 100.0% condition: 47.2/47.2 Wh (100%)
CPU:       Quad core AMD A8-4500M APU with Radeon HD Graphics (-MCP-) 
           cache: 8192 KB
           clock speeds: max: 1900 MHz 1: 1590 MHz 2: 1592 MHz 3: 1656 MHz
           4: 1658 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Trinity [Radeon HD 7640G]
           Display Server: x11 (X.Org 1.19.6 ) driver: radeon
           Resolution: 1600x900@60.19hz
           OpenGL: renderer: AMD ARUBA (DRM 2.50.0 / 4.15.0-42-generic, LLVM 6.0.0)
           version: 4.3 Mesa 18.0.5
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Trinity HDMI Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-42-generic
Network:   Card-1: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k
           IF: wlo1 state: up mac: 2c:d0:5a:eb:16:b1
           Card-2: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
           driver: r8169
           IF: eno1 state: down mac: 74:46:a0:79:76:b1
Drives:    HDD Total Size: 250.1GB (5.5% used)
           ID-1: /dev/sda model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 228G used: 13G (6%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 61.0C mobo: N/A gpu: 59.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 259 Uptime: 33 min Memory: 2077.5/7443.7MB
           Client: Shell (bash) inxi: 2.3.56
```

---

### Post by wildmanne39 on 2018-12-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by NM5TF on 2018-12-09
[QUOTE=ray9;13822264]I don't know what "code tags" are.

@Ray9.....

1 more time....

[I][U][B][COLOR="#FF0000"]use code tags to make the output more readable.....

select the adv reply button & paste the output between the # icons[/COLOR][/B][/U][/I]

you might find some help with your problem here  [http://https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux]("http://https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux")

I assume you meant [COLOR="#FF0000"]**Firefox**[/COLOR] rather than [COLOR="#FF0000"]**Firebird**[/COLOR]

good luck

tommy

---

