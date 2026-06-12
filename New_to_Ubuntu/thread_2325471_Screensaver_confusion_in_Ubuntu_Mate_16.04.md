---
title: "Screensaver confusion in Ubuntu Mate 16.04"
date: 2016-05-22
forum: New to Ubuntu
---

### Post by sprocket10 on 2016-05-22
Ok.  New-ish to Ubuntu (MATE) at 16.04.  I'm muddling through setting things up.  

```
Desktop config:
System:    Host: joseph-desktop Kernel: 4.4.0-22-generic x86_64 (64 bit)
           Desktop: MATE 1.12.1  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASRock model: Z77 Extreme4
           Bios: American Megatrends v: P2.90 date: 07/11/2013
CPU:       Quad core Intel Core i5-3570K (-MCP-) cache: 6144 KB 
           clock speeds: max: 3800 MHz 1: 1599 MHz 2: 1599 MHz 3: 2129 MHz
           4: 1602 MHz
Graphics:  Card-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
           Card-2: Advanced Micro Devices [AMD/ATI] Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP]
           Display Server: X.Org 1.18.3 drivers: ati,radeon,intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD PITCAIRN (DRM 2.43.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.2.0
Audio:     Card-1 Intel 7 Series/C210 Series Family High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
           driver: snd_hda_intel
           Card-3 Logitech G430 Surround Sound Gaming Headset
           driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.4.0-22-generic
Network:   Card-1: Realtek RTL8192CE PCIe Wireless Network Adapter
           driver: rtl8192ce
           IF: wlp2s0 state: down mac: 10:bf:48:4a:ef:5d
           Card-2: Broadcom NetLink BCM57781 Gigabit Ethernet PCIe driver: tg3
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full
           mac: d0:50:99:86:b6:57
Drives:    HDD Total Size: 6757.4GB (36.7% used)
           ID-1: /dev/sda model: Crucial_CT500MX2 size: 500.1GB
           ID-2: /dev/sdb model: M4 size: 256.1GB
           ID-3: /dev/sdc model: ST3000DM001 size: 3000.6GB
           ID-4: /dev/sdd model: ST3000DM001 size: 3000.6GB
Partition: ID-1: / size: 443G used: 7.7G (2%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 17.06GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 265 Uptime: 4:27 Memory: 2338.1/15933.6MB
           Client: Shell (bash) inxi: 2.2.35 
```



I'm having difficulty with the lock-screen, screensaver.  I've noticed that my screens go to sleep after a few minutes, even though I've set the Power Mgmt Preferences: "put computer to sleep when inactive for: never" and "put display to sleep when inactive for: never".  Under the LightDM GTK+ Greeter, I set the "timeout until the screen blanks" to "Never".  Yet it still "sleeps" or "power saves", etc.  Wiggling the mouse will return me straight to the desktop.  It does not log me out or ask for password to log back in.  I just continue where I left off.  I've also noticed the lock screen shortcut listed under Control Center -> Keyboard Shortcuts doesn't work.  The default was Super+L, which only opened the main menu for me.  I changed it to Ctrl+Alt+L, and I get an error: "couldn't execute command: xscreensaver-command -lock.  verify that this is a valid command".  Even going through the main menu and selecting "lock screen" does nothing.  I've read that MATE uses mate-screensaver, not xscreensaver by default.  I would really like my screen to never turn off or sleep or anything unless I use the lock screen hotkey or select 'lock screen' via the menu.  It feels like mate-screensaver is incomplete.  My googling hasn't yielded any useful results (yet).  I also tried looking in the dconf-editor program, but I'm not really sure where to start modifying things.  

Any advice?

---

### Post by wildmanne39 on 2016-05-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by buzzingrobot on 2016-05-23
Try disabling the Screensaver entirely via its panel in MATE's Control Panel.  Believe there are two checkboxes that are "on" by default.

---

