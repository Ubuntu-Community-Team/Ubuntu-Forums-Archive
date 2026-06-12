---
title: "Intel Core series power management"
date: 2018-02-22
forum: New to Ubuntu
---

### Post by igor-palica on 2018-02-22
Hi, 
i am new to the ubuntu enviroment. I would like to ask if there isnt any **GUI based** Intel Core power manager, that would let me switch the performance/powersave mode and also let switch active/passive cooling? I am using Core i7 3rd gen. mobile CPU, QM77 chipset on a Dell E6230.

Best regards
Igor.

---

### Post by wildmanne39 on 2018-02-22
*Thread moved to **New to Ubuntu, a more appropriate forum**.*

---

### Post by cruzer001 on 2018-02-22
Hi igor

First tell us what you are running.  Open a terminal (Ctrl + Alt + t) and enter:

```
inxi -b
```

And please post the output.

This may interest you:

[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

---

### Post by igor-palica on 2018-02-22
Hi, this is the output of ixni

```

System:    Host: nh-Latitude-E6230 Kernel: 4.13.0-36-generic x86_64 bits: 64
           Desktop: Xfce 4.12.3 Distro: Ubuntu 17.10
Machine:   Device: laptop System: Dell product: Latitude E6230 v: 01 serial: N/A
           Mobo: Dell model: 0GWYCT v: A00 serial: N/A
           BIOS: Dell v: A16 date: 10/13/2016
Battery    BAT0: charge: 10.1 Wh 26.3% condition: 38.4/48.8 Wh (79%)
CPU:       Dual core Intel Core i7-3520M (-HT-MCP-) speed/max: 2890/3600 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller
           Display Server: x11 (X.Org 1.19.5 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.22hz
           OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile
           version: 4.2 Mesa 17.2.8
Network:   Card-1: Intel 82579LM Gigabit Network Connection driver: e1000e
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak]
           driver: iwlwifi
Drives:    HDD Total Size: 2000.4GB (2.3% used)
Info:      Processes: 287 Uptime: 12:45 Memory: 2683.0/7883.2MB
           Client: Shell (bash) inxi: 2.3.37 


```

I have read the link you posted. These are all command line tools, but isnt there any GUI based frontend for it?

---

### Post by cruzer001 on 2018-02-22
Maybe laptop-mode-tools would be more to your liking.  Its a checklist (on or off) of power management options.  Here's a pic:

[http://3.bp.blogspot.com/-rSMJU61Fg3I/Us6KLTftmMI/AAAAAAAARBQ/u3lWf7a-B40/s1600/laptop-mode-tools-gui.jpg](http://3.bp.blogspot.com/-rSMJU61Fg3I/Us6KLTftmMI/AAAAAAAARBQ/u3lWf7a-B40/s1600/laptop-mode-tools-gui.jpg)

I can't tell you a lot about it as I do not use it, just thought you may like the user interface.

To install:
```
sudo apt install laptop-mode-tools
```

---

### Post by kerry_s on 2018-02-22
it says your using xfce, so if you right click the panel-> panel settings, look through the add ons i think the last time i used xfce there was a cpu scaling add on, which should give you those options.

---

### Post by igor-palica on 2018-02-25
Today i came across xfce4-cpufreq plugin, compiled it, but i cant see it anywhere between  the panel add-ons. So i take look at /usr/lib/xfce4 and there was directory panel/plugins/. I made directory panel-plugins copied the .la and .so file there and now i have it on the panel. But if i make any changes on the plugin nothing works. An example : I open it says that governor is on powersave. I switch it to perfomance then close and reopen it again and the settings are not saved as it says powersave. Can some more experienced user test it?

---

### Post by cruzer001 on 2018-02-25
Found this

> This is not a bug, though it might look like one because of the widgets used that pretentiously suggest the user could change something. Changing CPU frequency or the governor is not implemented and probably will never be, as it is supposed to be handled by the kernel or power manager.

[http://goodies.xfce.org/projects/panel-plugins/xfce4-cpufreq-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-cpufreq-plugin)

---

### Post by igor-palica on 2018-02-25
:-( in the happines of finding something i overlooked it somehow. ...

---

### Post by cruzer001 on 2018-02-25
I'm just not finding any GUI for the xfce desktop :(

The neat toys are gnome/ubuntu based.  An example for my gnome desktop:

[http://konkor.github.io/cpufreq/](http://konkor.github.io/cpufreq/)

Sorry

You might consider jumping the fence.  The Gnome desktop (and Ubuntu-Gnome) runs nice on my Dell Latitude (4core i7).

---

### Post by Impavidus on 2018-02-26
> **igor-palica said:**
> Today i came across xfce4-cpufreq plugin, compiled it, but i cant see it anywhere between  the panel add-ons. So i take look at /usr/lib/xfce4 and there was directory panel/plugins/. I made directory panel-plugins copied the .la and .so file there and now i have it on the panel. But if i make any changes on the plugin nothing works. An example : I open it says that governor is on powersave. I switch it to perfomance then close and reopen it again and the settings are not saved as it says powersave. Can some more experienced user test it?

No need to compile and install manually, as this is in the repositories:```
sudo apt install xfce4-goodies
```

---

### Post by cruzer001 on 2018-02-26
> **Impavidus said:**
> No need to compile and install manually, as this is in the repositories
Yes, but still won't work.

---

