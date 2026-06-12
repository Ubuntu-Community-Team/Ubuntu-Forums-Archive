---
title: "Ubutntu 16.04 startup/login screen trouble"
date: 2016-06-25
forum: New to Ubuntu
---

### Post by devlin3 on 2016-06-25
Hi there,

My brother recently gave me an old laptop of his. He installed Ubuntu 16.04 himself. There is a somewhat frequent problem where the laptop, while starting up, does not display the login screen. It seems to startup normally aside from this. I should also note that I hear the login screen drumbeat, even when the login screen itself is not displayed.

I have yet to put anything important on the laptop, should I use my own 16.04 bootable flash drive to do a fresh install? Or is there a simpler, more direct way to diagnose and solve the problem.

Thank you in advance for taking the time

---

### Post by QDR06VV9 on 2016-06-25
This might help you get started here...copy and paste the return of this from the terminal
```
inxi -Fxz
```
That will help with knowing the specs of the machine.
And also paste back the return of this from the terminal
```
apt-cache policy lightdm
```

---

### Post by devlin3 on 2016-06-26
the output of ```
inxi -Fxz
``` is ```
   inxi -Fxz
 System:    Host: devlinux Kernel: 4.4.0-24-generic x86_64 (64 bit gcc: 5.3.1)
            Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3)
            Distro: Ubuntu 16.04 xenial
 Machine:   System: LENOVO (portable) product: 291224U v: ThinkPad T410s
            Mobo: LENOVO model: 291224U
            Bios: LENOVO v: 6UET53WW (1.33 ) date: 09/02/2010
 CPU:       Dual core Intel Core i5 M 520 (-HT-MCP-) cache: 3072 KB
            flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9575
            clock speeds: max: 2400 MHz 1: 1466 MHz 2: 1866 MHz 3: 1333 MHz
            4: 1333 MHz
 Graphics:  Card-1: Intel Core Processor Integrated Graphics Controller
            bus-ID: 00:02.0
            Card-2: NVIDIA GT218M [NVS 3100M] bus-ID: 01:00.0
            Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa) FAILED: nouveau
            Resolution: 1440x900@60.06hz
            GLX Renderer: Mesa DRI Intel Ironlake Mobile
            GLX Version: 2.1 Mesa 11.2.0 Direct Rendering: Yes
 Audio:     Card-1 Intel 5 Series/3400 Series High Definition Audio
            driver: snd_hda_intel bus-ID: 00:1b.0
            Card-2 NVIDIA High Definition Audio Controller
            driver: snd_hda_intel bus-ID: 01:00.1
            Sound: Advanced Linux Sound Architecture v: k4.4.0-24-generic
 Network:   Card-1: Intel 82577LM Gigabit Network Connection
            driver: e1000e v: 3.2.6-k port: 1820 bus-ID: 00:19.0
            IF: enp0s25 state: down mac: <filter>
            Card-2: Intel Centrino Advanced-N 6200
            driver: iwlwifi bus-ID: 03:00.0
            IF: wlp3s0 state: up mac: <filter>
 Drives:    HDD Total Size: 250.1GB (16.3% used)
            ID-1: /dev/sda model: TOSHIBA_MK2529GS size: 250.1GB temp: 40C
 Partition: ID-1: / size: 222G used: 31G (15%) fs: ext4 dev: /dev/sda1
            ID-2: swap-1 size: 8.37GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
 RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
 Sensors:   System Temperatures: cpu: 55.0C mobo: 0.0C gpu: 65.0
            Fan Speeds (in rpm): cpu: 3417
 Info:      Processes: 240 Uptime: 4 min Memory: 1075.5/7779.7MB
            Init: systemd runlevel: 5 Gcc sys: 5.3.1
            Client: Shell (bash 4.3.421) inxi: 2.2.35  
``` and the output of ```
 apt-cache polict lightdm
``` is ```
lightdm:
  Installed: 1.18.1-0ubuntu1
  Candidate: 1.18.1-0ubuntu1
  Version table:
 *** 1.18.1-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by grahammechanical on 2016-06-26
> frequent problem where the laptop, while starting up, does not display the login screen.

Does that mean that there are times when you can get to a log in screen and log in? You have two graphic adapters. An integrated Intel graphic adapter and a Nvidia GT 218m. I think that the GT 218 is a relative of my GT 220 and I can tell you that the latest Nvidia Linux drivers do not support the GT 220. And so, I think that the GT 218 would not be supported either.

If you can use the BIOS set up utility to run the machine using the Intel graphics adapter then you may be able to get to a working desktop. Then, Go to System Settings>Software & Updates>Additional Drivers tab and change video drivers. You will need to be connected to the internet and to allow time for Additional Drivers to do its stuff. You might want to try the open source video driver (Nouveau).

I suggest that you as a practice you shutdown and start the machine running on Intel graphics and only switch to the Nvidia adapter once the operating system has loaded. To switch between Intel & Nvidia you will need an Nvidia driver installed. Then you can use the Nvidia settings utility to switch between graphic adapters. You will find the Nvidia settings utility in the Dash. Search for "nvidia."

Regards

---

### Post by devlin3 on 2016-06-27
> Does that mean that there are times when you can get to a log in screen and log in?

Yes. About 60% of the time the login screen does not display, the rest of the time the login screen and everything else displays fine. 

I went into the BIOS display settings and saw that one of the graphic settings was set to "SWITCHABLE" as opposed to "INTEGRATED" or "DISCRETE." Under SWITCHABLE, it said that this setting should only be activated with Windows 7 and the appropriate driver. I set it to DISCRETE, rebooted 4 times, and the login screen displayed every time. I will mark this thread SOLVED unless or until the problem crops up again.

Thanks for your help.

---

