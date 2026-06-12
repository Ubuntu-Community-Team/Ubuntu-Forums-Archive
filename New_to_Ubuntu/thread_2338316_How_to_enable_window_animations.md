---
title: "How to enable window animations"
date: 2016-09-26
forum: New to Ubuntu
---

### Post by g.wiebe84 on 2016-09-26
It's good to be back after a long break which was not of my doing. I have now installed Ubuntu 16.04 (I've always come back to Ubuntu even after forays into Arch and Mint) alongside of Windows 10. It's been a bumpy install but not as bad as in years past. 

So, here's the issue which, by searching, seems to be the opposite of most people: how to enable window animations? I have a "vanilla" install of Ubuntu 16.04 with nothing weird going on. I have Unity running as per the standard install. I installed Compiz since I utilize the multiple desktops and the ability to rotate amongst them. The eye candy also helps with preventing boredom and brain fade. I was, after the install (I enabled all software updates to be installed during the USB install) and running Webupd8's things to do after installing 16.04, puzzled as to why I had no window animations. 

As you can see, I don't have a particularly powerful laptop but then it's no slouch either. 

Terminal: inxi -FG
```
System:    Host: glenn-HP-Pavilion-17-Notebook-PC Kernel: 4.4.0-38-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Hewlett-Packard (portable) product: HP Pavilion 17 Notebook PC v: 0883100000305B10000620100
           Mobo: Hewlett-Packard model: 1977 v: 96.33
           Bios: Insyde v: F.23 date: 06/04/2014
CPU:       Dual core Intel Core i5-4200M (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 3100 MHz 1: 2500 MHz 2: 2500 MHz 3: 814 MHz
           4: 2500 MHz
Graphics:  Card: Intel 4th Gen Core Processor Integrated Graphics Controller
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1600x900@60.19hz
           GLX Renderer: Mesa DRI Intel Haswell Mobile
           GLX Version: 3.0 Mesa 11.2.0
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-38-generic
Network:   Card-1: Ralink RT3290 Wireless 802.11n 1T/1R PCIe driver: rt2860
           IF: rename3 state: up mac: 80:56:f2:63:4a:65
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169
           IF: eno1 state: down mac: a0:d3:c1:51:7a:55
Drives:    HDD Total Size: 750.2GB (44.4% used)
           ID-1: /dev/sda model: TOSHIBA_MQ01ABD0 size: 750.2GB
Partition: ID-1: / size: 417G used: 98G (25%) fs: ext4 dev: /dev/sda8
           ID-2: swap-1 size: 6.35GB used: 0.00GB (0%) fs: swap dev: /dev/sda9
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 210 Uptime: 11:13 Memory: 1129.2/5883.1MB
           Client: Shell (bash) inxi: 2.2.35

```
 
Thanks for looking into this.

---

### Post by yetimon_64 on 2016-09-27
Compiz nowadays only comes without all the eyecandy and with only the one set of plugins (compiz-plugins-default) with the default installation. 

To add the animations and other special effects the package "compiz-plugins" can also be added after the initial default install. You can also install compizconfig-settings-manager (the command "ccsm" will activate it from "alt+f2" or terminal) for activating and mangaing the addons. Note some of the effects like fire and the rain effect may not work as well as they used to, a lot of the older effects from older installs no longer exist at all. 

From ccsm you can then easily activate whichever additional plugin you want to work, like windows animations etc. The windows animations are part of "compiz-plugins". If you haven't already added it ...
```
sudo apt-get install compiz-plugins
```
If you want to activate them easily with ccsm ...
```
sudo apt-get install compizconfig-settings-manager
```

Good luck, yeti.

---

### Post by ajgreeny on 2016-09-27
Take care when enabling some of the plugins in compiz as they can give you problems which are totally unexpected; make sure you search out how to return the settings to default in the command line before you start, just in case things go wrong.

I can't really help with details of this as I don't use unity and Ubuntu, Xubuntu being my OS of choice but a quick search suggests that this command should reset Compiz
```
dconf reset -f /org/compiz/
```
and this command should restart Unity```
setsid unity
```

---

### Post by g.wiebe84 on 2016-09-27
Thanks, yetimon, but I already have compiz, the plugins, and the extras installed and enabled.

---

### Post by g.wiebe84 on 2016-09-27
> **ajgreeny said:**
> Take care when enabling some of the plugins in compiz as they can give you problems which are totally unexpected; make sure you search out how to return the settings to default in the command line before you start, just in case things go wrong.

I can't really help with details of this as I don't use unity and Ubuntu, Xubuntu being my OS of choice but a quick search suggests that this command should reset Compiz
```
dconf reset -f /org/compiz/
```
and this command should restart Unity```
setsid unity
```

So after fiddling around for another hour or so, I finally capitulated and entered these terminal commands knowing that all the settings that I'd entered thus far would be gone. I'm now setting compiz up the way I had it or at least attempting to do so. But, the issue of the non-existent animations had been rectified. Thanks!

---

### Post by CantankRus on 2016-09-28
> **g.wiebe84 said:**
> So after fiddling around for another hour or so, I finally capitulated and entered these terminal commands knowing that all the settings that I'd entered thus far would be gone. I'm now setting compiz up the way I had it or at least attempting to do so. But, the issue of the non-existent animations had been rectified. Thanks!
You may know this....
Once compiz is configured the way you like, save your settings using the export button in preferences.
Use the the import button to load your saved .profile config when needed.

---

### Post by ajgreeny on 2016-09-28
Great stuff!

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by g.wiebe84 on 2016-10-11
I was just re-reading this thread and realized that my last post may have been a bit misleading. My initial frustrations were somewhat assuaged after I got compiz sorted and everything working as it should. The issue is that, when compared to past distros, many of the animations that brought me to Linux are now gone and nowhere to be found. Exploding windows, fire (not the mouse fire thing), etc. 

While marking this thread SOLVED would imply that my question has been answered that would be true only in part. My question remains: how can I find (or compile) the compiz animations add-ons of the past?

---

### Post by CantankRus on 2016-10-11
Canonical basically took over the development of compiz and dropped a lot of plugins to focus on unity.
The unsupported compiz-plugins package contains some of these plugins,
but others just don't work anymore with the latest compiz and are not included.
It's not just a matter of compiling...... you would have to fix the broken plugins.

---

### Post by CantankRus on 2016-10-15
Just noticed in my 16.10 install the compiz-plugins package does contain more of the old animations.
I thought they were gone for good.
Don't know how reliable they are but keep in mind 16.10 is only supported for 9 months and at the moment,
for me it is quite buggy.

---

