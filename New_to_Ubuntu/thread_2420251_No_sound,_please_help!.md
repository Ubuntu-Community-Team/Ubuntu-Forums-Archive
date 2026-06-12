---
title: "No sound, please help!"
date: 2019-06-01
forum: New to Ubuntu
---

### Post by denisstk11 on 2019-06-01
Hello,I'm new in the Lubuntu world. Got impressed with the simplicity of the system and replaced Windows 10 with Lubuntu 19.04 successfully. I face difficulties with sound drivers ( no sound despite attempts to update drivers). Please, I need your help. Is there a way to improve on graphics ( image quality), please ? Thanks in advance !

---

### Post by ajgreeny on 2019-06-01
It's difficult to help you much as we have no idea what hardware you are using.

Please install inxi (if necessary) and then run command ```
inxi -Fzx
``` and copy the output back here.
Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

---

### Post by SeijiSensei on 2019-06-01
First thing I'd check is whether you have multiple sound outputs and you've chosen the wrong one.  Look in System Settings.

---

### Post by denisstk11 on 2019-06-02
Hello, using an ST106 notebook 2GB RAM. Have installed inxi and run the command
"inxi -Fzx"  but no sound. 
Got a single sound output. Thanks!

---

### Post by yancek on 2019-06-02
> "inxi -Fzx"  but no sound.

Apparently you missed the part of the suggestion on inxi above which said "and copy the output back here".  The purpose of running the command is to get information on your system to post here so that members with more knowledge/experience might help.  It won't "fix" anything nor is it meant to.

---

### Post by denisstk11 on 2019-06-02
ok, ...sorry i didn't get it earlier


```
System:    Host: che-pc Kernel: 5.0.0-13-generic x86_64 bits: 64 compiler: gcc v: 8.3.0 Desktop: LXQt 0.14.1 
           Distro: Ubuntu 19.04 (Disco Dingo) 
Machine:   Type: Desktop System: SHENZHEN X&F product: ST106 v: N/A serial: <filter> 
           Mobo: SHENZHEN X&F model: ST106 serial: <filter> UEFI: American Megatrends 
           v: N1003TQD.C3L3LW.GX.X003.2017.1220.1449 date: 12/20/2017 
Battery:   ID-1: axp288_fuel_gauge charge: 96% condition: N/A model: N/A status: Discharging 
CPU:       Topology: Quad Core model: Intel Atom x5-Z8350 bits: 64 type: MCP arch: Airmont rev: 4 L2 cache: 1024 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 11520 
           Speed: 480 MHz min/max: 480/1920 MHz Core speeds (MHz): 1: 1282 2: 1357 3: 1000 4: 1092 
Graphics:  Device-1: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers 
           driver: i915 v: kernel bus ID: 00:02.0 
           Display: x11 server: X.Org 1.20.4 driver: modesetting unloaded: fbdev,vesa resolution: 800x1280~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics (Cherrytrail) v: 4.5 Mesa 19.0.2 direct render: Yes 
Audio:     Device-1: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit 
           driver: intel_atomisp2_pm v: kernel bus ID: 00:03.0 
           Sound Server: ALSA v: k5.0.0-13-generic 
Network:   Message: No Device data found. 
           IF-ID-1: enp0s20u2 state: unknown speed: N/A duplex: N/A mac: <filter> 
           IF-ID-2: wlan0 state: down mac: <filter> 
Drives:    Local Storage: total: 28.50 GiB used: 22.38 GiB (78.5%) 
           ID-1: /dev/mmcblk0 model: T52732 size: 28.50 GiB 
Partition: ID-1: / size: 27.63 GiB used: 22.37 GiB (81.0%) fs: ext4 dev: /dev/mmcblk0p2 
Sensors:   System Temperatures: cpu: 49.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 190 Uptime: 36m Memory: 1.85 GiB used: 819.6 MiB (43.2%) Init: systemd runlevel: 5 Compilers: 
           gcc: 8.3.0 Shell: bash v: 5.0.3 inxi: 3.0.33 
chei@che-pc:~$
```

---

### Post by denisstk11 on 2019-06-02
Distro; lubuntu 19.04- 64bit - code tags - NO SOUND - Grub2wiki & Grub2 Basics - sudo apt-get install Blueman - connect to external bluetooth audio device - solved Threads

Thanks to all !!!!

---

