---
title: "Help please CPU usage 100%"
date: 2024-02-13
forum: New to Ubuntu
---

### Post by zanderstudio on 2024-02-13
Hello!

Total noob here so I'm sorry if asking stupid questions. Truth to be told I got tired of other operating systems years ago but never bothered to try a Linux one. I recently tried to revive an old laptop that I have by upgrading a ram and swapping HDD with an ssd. I installed Ubuntu Studio and the problem is I get spikes in CPU usage even on simple tasks. And on YouTube or anything rendering a video it goes and stays at 100%. Even while moving the cursor I get CPU spikes. Wifi shows as low as a few kbps even though on speedtest I get 40mb download. If I can run any command to offer more info please guide me a little. 
The system is and AMD A6 Apu with Radeon A4 integrated GPU, 16gb Ram and 480Gb Ssd

---

### Post by Frogs Hair on 2024-02-13
Hello and welcome

The top command may help identify the process/s responsible. Open the terminal and enter the following.
```
top
```

---

### Post by TenPlus1 on 2024-02-14
What are your system specs ?

---

### Post by ActionParsnip on 2024-02-14
```

top -n 1

```
would be more useful. You can copy and paste the text from the snapshot in time

---

### Post by TheFu on 2024-02-14
Studio isn't a light distro.  It puts demands that other Ubuntu flavors don't onto a system.  Without a good, factual, system overview, that include exact GPU and CPU models it is impossible to set reasonable expectations for what should and shouldn't be possible.  The output from this command:
**inxi -Fxz**
will provide those details as text. _For example_:```

$ inxi -Fxz
System:    Kernel: 5.15.0-92-generic x86_64 bits: 64 compiler: N/A Desktop: FVWM2 2.6.8 
           Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: <filter> 
           UEFI: American Megatrends v: 5003 date: 02/03/2023 
CPU:       Topology: 6-Core model: AMD Ryzen 5 5600G with Radeon Graphics bits: 64 type: MT MCP arch: Zen 3 
           L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm bogomips: 100803 
           Speed: 4199 MHz min/max: 1400/4200 MHz Core speeds (MHz): 1: 4200 2: 4199 3: 4200 4: 4200 5: 4200 
           6: 4202 7: 4201 8: 4201 9: 4200 10: 4199 11: 4200 12: 4215 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] vendor: ASUSTeK driver: amdgpu v: kernel bus ID: 0a:00.0 
           Display: x11 server: X.Org 1.20.13 driver: amdgpu,ati unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1200~60Hz 
           OpenGL: renderer: AMD RENOIR (DRM 3.42.0 5.15.0-92-generic LLVM 12.0.0) v: 4.6 Mesa 21.2.6 
           direct render: Yes 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] vendor: ASUSTeK driver: snd_hda_intel v: kernel 
           bus ID: 0a:00.1 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio vendor: ASUSTeK driver: snd_hda_intel 
           v: kernel bus ID: 0a:00.6 
           Device-3: C-Media Audio Adapter (Unitek Y-247A) type: USB driver: cmedia_hs100b,snd-usb-audio,usbhid 
           bus ID: 1-6.3:9 
           Sound Server: ALSA v: k5.15.0-92-generic 
Network:   Device-1: Intel I211 Gigabit Network vendor: ASUSTeK driver: igb v: kernel port: d000 bus ID: 03:00.0 
           IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
           Device-2: Intel 82575GB Gigabit Network driver: igb v: kernel port: c020 bus ID: 07:00.0 
           IF: enp7s0f0 state: down mac: <filter> 
...
           IF-ID-1: br0 state: up speed: 10000 Mbps duplex: unknown mac: <filter> 
           IF-ID-2: lxcbr0 state: down mac: <filter> 
           IF-ID-3: veth742f2dde state: up speed: 10000 Mbps duplex: full mac: <filter> 
           IF-ID-4: veth8c52a0e6 state: up speed: 10000 Mbps duplex: full mac: <filter> 
           IF-ID-5: vethd53c58c8 state: up speed: 10000 Mbps duplex: full mac: <filter> 
           IF-ID-6: vethd73bba4f state: up speed: 10000 Mbps duplex: full mac: <filter> 
           IF-ID-7: vethd92b5a8b state: up speed: 10000 Mbps duplex: full mac: <filter> 
...
Drives:    Local Storage: total: 37.13 TiB used: 30.13 TiB (81.1%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 EVO 500GB size: 465.76 GiB temp: 39 C 
...
Partition: ID-1: / size: 34.15 GiB used: 28.00 GiB (82.0%) fs: ext4 dev: /dev/dm-1 
           ID-2: /boot size: 573.7 MiB used: 280.9 MiB (49.0%) fs: ext4 dev: /dev/nvme0n1p2 
           ID-3: /home size: 25.42 GiB used: 9.75 GiB (38.4%) fs: ext4 dev: /dev/dm-3 
           ID-4: /var size: 53.84 GiB used: 15.53 GiB (28.8%) fs: ext4 dev: /dev/dm-2 
           ID-5: swap-1 size: 4.10 GiB used: 2.79 GiB (68.1%) fs: swap dev: /dev/dm-0 
Sensors:   System Temperatures: cpu: 39.0 C mobo: N/A gpu: amdgpu temp: 41 C 
           Fan Speeds (RPM): N/A 
Info:      Processes: 697 Uptime: 9d 2h 54m Memory: 30.71 GiB used: 23.73 GiB (77.3%) Init: systemd runlevel: 5 
           Compilers: gcc: 9.4.0 Shell: bash v: 5.0.17 inxi: 3.0.38 
```
Lots of good stuff in there. Hardware, drivers, file systems, networking, temperatures, system stability, RAM, CPU, kernel, OS release, GPU and display info.

As for what is eating all the CPU, there are a number of tools that can show this.  **top**, **htop**, **glances** are the typical text/CLI tools.   Glances does need a big terminal window, but it has lots of performance "cheese" for seeing more than just CPU use, but RAM, swap, network and disk I/O as well. 

We prefer text for posting to these forums, since if columns are honored (use forum 'code-tags'), they are much more efficient than any image.  [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains code-tags and other tagging.  It works like bold/italics/quote tags, so don't overthink it.  Just select/paste the output from a terminal into  the advanced editor in the forum browser here .... then select the all that output and press the **#** button.  Next, use the "Preview" button to see how the columns line up perfect, just like in your terminal window.  No editing of the terminal text needed.

_For example_
```
istar (Ubuntu 20.04 64bit / Linux 5.15.0-92-generic)                                      Uptime: 9 days, 3:04:46

CPU  [  8.3%]   CPU       8.3%  nice:     0.0%  ctx_sw:   13K    MEM     72.9%    SWAP     68.1%    LOAD    12-core
MEM  [ 72.9%]   user:     5.5%  irq:      0.0%  inter:   8158    total:  30.7G    total:   4.10G    1 min:    0.41
SWAP [ 68.1%]   system:   3.1%  iowait:   0.0%  sw_int:  5336    used:   22.4G    used:    2.79G    5 min:    0.42
                idle:    91.4%  steal:    0.0%                   free:   8.33G    free:    1.31G    15 min:   0.42

NETWORK       Rx/s   Tx/s   TASKS 700 (2049 thr), 1 run, 539 slp, 160 oth sorted automatically by memory consumption
br0            2Kb    2Kb
enp3s0         3Kb    2Kb   CPU%   MEM%  VIRT  RES       PID USER          TIME+ THR  NI S  R/s W/s  Command
lo              0b     0b   0.0    18.0  6.65G 5.51G    4551 libvirt-q  17h47:03 7     0 S    ? ?    /usr/bin/qemu-s
lxcbr0          0b     0b   0.0    12.7  4.68G 3.91G    4650 libvirt-q   45h4:44 7     0 S    ? ?    qemu-system-x86
_th8c52a0e6     0b     0b   0.0    4.2   1.50G 1.28G  879173 1000115        1:39 2     0 S    ? ?    /usr/sbin/clamd
_th742f2dde     0b     0b   0.0    2.8   1.82G 875M     4357 libvirt-q    1h0:04 6     0 S    ? ?    qemu-system-x86
_thd53c58c8     0b     0b   6.3    2.2   1.76G 696M     4401 libvirt-q     40:39 6     0 S    ? ?    qemu-system-x86
_thd73bba4f     0b     0b   0.0    1.8   7.93G 555M     2653 jellyfin    3h18:15 45    0 S    ? ?    /usr/bin/jellyf
_thd92b5a8b     0b     0b   0.0    1.4   1.20G 443M     4444 libvirt-q     25:02 5     0 S    ? ?    qemu-system-x86
virbr0          0b     0b   0.0    1.3   3.21G 395M   280011 1000000       31:30 45    0 S    ? ?    mysqld --default
...
```

**I posted sample information **so you can see it really isn't too sensitive and some stuff is filtered in the inxi output thanks to the **-z** option.

---

### Post by TenPlus1 on 2024-02-15
You are using an older Ubuntu release, maybe updating to 22.04 with the newer 6.2 kernel will help your AMD system run smoothly.

---

### Post by TheFu on 2024-02-15
> **TenPlus1 said:**
> You are using an older Ubuntu release, maybe updating to 22.04 with the newer 6.2 kernel will help your AMD system run smoothly.

The OP hasn't posted that information or did I miss it?  I worried that someone would be confused by example posts with data.

I can assure you that my systems (mostly AMD Ryzen) are very stable and were on 18.04 too.
```
$ uptime 
 10:27:05 up 10 days, 57 min, 
```

---

### Post by SeijiSensei on 2024-02-15
This discussion will be fruitless as long as the OP doesn't post the results of the top command.

---

### Post by MAFoElffen on 2024-02-17
Ediited his one and only post from 4 days ago to highlight what he dis say (no responses of anything since)
> **zanderstudio said:**
> 
I recently tried to revive an old laptop that I have by upgrading a ram and swapping HDD with an ssd. The system is and AMD A6 Apu with Radeon A4 integrated GPU, 16gb Ram and 480Gb Ssd

I installed Ubuntu Studio...

...and the problem is I get spikes in CPU usage even on simple tasks. And on YouTube or anything rendering a video it goes and stays at 100%. Even while moving the cursor I get CPU spikes. Wifi shows as low as a few kbps even though on speedtest I get 40mb download. If I can run any command to offer more info please guide me a little. 

There is no mention of what release version of Ubuntu Studio he installed.

The laptop is most likely about 10 years old... That was when the AMD A6 was released.

The AMD A6 was comparable to the Intel 4th Gen i5, so mid-range. The actual iGPU in that GPU was Radeon HD 8470D. Which was also mid-range. It would stutter if you tried to play demanding games with it.

For 2013, the Wifi in a laptop with that CPU was most likely 802.11a or 802.11g, which were both rated at 54 Mbps.

He should really run the Forum's 'system-info' script to provide what he has posting the URL of where the report uploads to, and do
```

ps -e v | awk '$9 !~ /0\.0/' > temp-processes.log.txt && ps -e -f | awk '$4 !~ /0/' > tmp-cpu-proc.log.txt

```
And upload both produced files as text files attached to his post.

That is what I would do to track that down.

---

