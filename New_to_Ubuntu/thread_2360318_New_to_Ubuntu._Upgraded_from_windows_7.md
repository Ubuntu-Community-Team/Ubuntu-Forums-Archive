---
title: "New to Ubuntu. Upgraded from windows 7"
date: 2017-05-03
forum: New to Ubuntu
---

### Post by metalhead24 on 2017-05-03
Hey guys, I just upgraded an old toshiba satellite to Ubuntu 16.04. I am a Cyber Security student and I wanted to expand my knowledge of other OS'. I am having a common problem of the touchpad not working. The USB trackball works just fine. I'm even using said machine now. I have looked through some older threads and used some commands that I found there, but no dice. 

If you guys need more info, I'd be happy to get it... you just might have to tell me HOW to get it. 

Thanks.

---

### Post by #&amp;thj^% on 2017-05-03
First lets see if it is detected:
Post back the return from a terminal:
```
xinput list
```

Mine shows as follows:

```
xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   **&#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]**
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=13    [slave  keyboard (3)]

```

---

### Post by metalhead24 on 2017-05-03
```

xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Logitech M325                               id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                     id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Toshiba input device  

```

Looks like it can see it.

---

### Post by #&amp;thj^% on 2017-05-03
Curious??
Can you try a keyboard combo of <Fn F7>
after check your touchpad again.

---

### Post by metalhead24 on 2017-05-03
On this one, the touchpad enable/disable is F5. That isn't working either. F7 is the play/pause music control. In windows, there is a device manager... does Ubuntu have something like that?

---

### Post by #&amp;thj^% on 2017-05-03
need to check some older notes i keep...be back soon. 
and a device manager on linux ...nope.
EDIT: can you also give me the output from:
```
inxi -Fxz
```

---

### Post by #&amp;thj^% on 2017-05-03
It would be great to have this information first:
```
inxi -Fxz
```
You may need to install it first.
```
sudo apt install inxi
```
I need some specs for your machine.

---

### Post by metalhead24 on 2017-05-03
yeah, had to install it first.

```

CPU:       Dual core Intel Celeron N2840 (-MCP-) cache: 1024 KB bmips: 8663 
           clock speeds: max: 2582 MHz 1: 516 MHz 2: 583 MHz
           CPU Flags: 3dnowprefetch acpi aperfmperf apic arat arch_perfmon bts
           clflush cmov constant_tsc cx16 cx8 de ds_cpl dtes64 dtherm dts
           eagerfpu epb ept erms est flexpriority fpu fxsr ht ida lahf_lm lm
           mca mce mmx monitor movbe msr mtrr nonstop_tsc nopl nx pae pat pbe
           pclmulqdq pdcm pebs pge pni popcnt pse pse36 rdrand rdtscp rep_good
           sep smep ss sse sse2 sse4_1 sse4_2 ssse3 syscall tm tm2 tpr_shadow
           tsc tsc_adjust tsc_deadline_timer vme vmx vnmi vpid xtopology xtpr

```

---

### Post by #&amp;thj^% on 2017-05-03
> **metalhead24 said:**
> yeah, had to install it first.

```

CPU:       Dual core Intel Celeron N2840 (-MCP-) cache: 1024 KB bmips: 8663 
           clock speeds: max: 2582 MHz 1: 516 MHz 2: 583 MHz
           CPU Flags: 3dnowprefetch acpi aperfmperf apic arat arch_perfmon bts
           clflush cmov constant_tsc cx16 cx8 de ds_cpl dtes64 dtherm dts
           eagerfpu epb ept erms est flexpriority fpu fxsr ht ida lahf_lm lm
           mca mce mmx monitor movbe msr mtrr nonstop_tsc nopl nx pae pat pbe
           pclmulqdq pdcm pebs pge pni popcnt pse pse36 rdrand rdtscp rep_good
           sep smep ss sse sse2 sse4_1 sse4_2 ssse3 syscall tm tm2 tpr_shadow
           tsc tsc_adjust tsc_deadline_timer vme vmx vnmi vpid xtopology xtpr

```

Not exactly what i was looking for:
Mine:
```
inxi -Fxz
[B]System:    Host: me-pc Kernel: 4.10.13-1-ARCH x86_64 (64 bit gcc: 6.3.1)
           Desktop: MATE 1.18.0 (Gtk 3.22.12) Distro: Archrolling
Machine:   Device: laptop System: LENOVO product: 2349M88 v: ThinkPad T430
           Mobo: LENOVO model: 2349M88
           UEFI [Legacy]: LENOVO v: G1ET41WW (1.16 ) date: 05/25/2012[/B]
Battery    BAT0: charge: 49.6 Wh 94.7% condition: 52.4/56.2 Wh (93%)
           model: LGC 45N1005 status: N/A
CPU:       Dual core Intel Core i5-3320M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10381
           clock speeds: max: 3300 MHz 1: 1199 MHz 2: 1200 MHz 3: 1199 MHz
           4: 1200 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.19.3 drivers: intel (unloaded: modesetting,fbdev,vesa)
           Resolution: 1600x900@59.98hz
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile
           GLX Version: 3.0 Mesa 17.0.5 Direct Rendering: Yes
Audio:     Card Intel 7 Series/C216 Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.10.13-1-ARCH
Network:   Card-1: Intel 82579LM Gigabit Network Connection
           driver: e1000e v: 3.2.6-k port: 5080 bus-ID: 00:19.0
           IF: enp0s25 state: down mac: <filter>
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak]
           driver: iwlwifi bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (13.7% used)
           ID-1: /dev/sda model: TOSHIBA_MK5065GS size: 500.1GB
Partition: ID-1: / size: 445G used: 52G (13%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 13.76GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
Sensors:   System Temperatures: cpu: 41.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 2566
Info:      Processes: 195 Uptime: 3:49 Memory: 1028.0/7704.9MB
           Init: systemd Gcc sys: 6.3.1
           Client: Shell (bash 4.4.121) inxi: 2.3.8 


```
EDIT: I see you left the "-" out should be entered as "inxi -Fxz"
Got to go I have some doctor visits to attend to will check back later>

---

### Post by metalhead24 on 2017-05-03
Actually, turns out I used a lower case 'f' instead of an upper case one.

```

inxi -Fxz
System:    Host: Mjolnir Kernel: 4.8.0-36-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: TOSHIBA product: Satellite C50-B v: PSCMLU-07U0EC
           Mobo: TOSHIBA model: ZBWAA v: 1.00
           Bios: TOSHIBA v: 5.10 date: 08/10/2015
CPU:       Dual core Intel Celeron N2840 (-MCP-) cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8663
           clock speeds: max: 2582 MHz 1: 583 MHz 2: 522 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@59.99hz
           GLX Renderer: Mesa DRI Intel Bay Trail
           GLX Version: 3.0 Mesa 12.0.6 Direct Rendering: Yes
Audio:     Card Intel Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.8.0-36-generic
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 01:00.0
           IF: enp1s0 state: down mac: <filter>
           Card-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
Drives:    HDD Total Size: 1000.2GB (1.0% used)
           ID-1: /dev/sda model: TOSHIBA_MQ01ABD1 size: 1000.2GB
Partition: ID-1: / size: 913G used: 5.2G (1%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 472M used: 116M (26%) fs: ext2 dev: /dev/sda1
           ID-3: swap-1 size: 4.18GB used: 0.00GB (0%) fs: swap dev: /dev/dm-3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 50.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 228 Uptime: 3:50 Memory: 1362.5/3839.2MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35

```

---

### Post by #&amp;thj^% on 2017-05-03
Well i have dug through all my notes, and the only thing i can suggest here:
See if this works: Here is the fix for the keyboard touchpad malfunction: found here and the link is still good. [http://www.tomsguide.com/forum/64083-35-toshiba-satellite-keyboard-touchpad-work](http://www.tomsguide.com/forum/64083-35-toshiba-satellite-keyboard-touchpad-work)
1- Turn off computer, disconnect the power cord, remove the battery.
2- Press the Power On button for 120 seconds or 2 minutes
3- Replace battery and/or connect power cord.
4- Turn On computer + immediately press F2 key repeatedly
5- Press F9 then press Enter
6- Press F10 then press Enter
Fingers crossed.
And was reported to work here also: [https://askubuntu.com/questions/602147/touchpad-wont-work-after-ubuntu-14-04-install-on-toshiba-satellite-s55-b5266-la](https://askubuntu.com/questions/602147/touchpad-wont-work-after-ubuntu-14-04-install-on-toshiba-satellite-s55-b5266-la)

---

### Post by Geoffrey_Arndt on 2017-05-03
Often, there is a second step required after doing the F+F5 combo which toggles the device on/off.   That second step is after the key combo is pressed, the system just needs a reboot to boot-up into the new configuration.    If you ever turn the touchpad off, be sure to re-enable it BEFORE turning the laptop off, else you'll have to go thru the same steps again.

---

### Post by metalhead24 on 2017-05-07
Almost.... the touchpad worked when in the bios, but still won't function when in the OS.

---

### Post by Geoffrey_Arndt on 2017-05-07
So, to confirm:

>   you do the combo key of Function + F5  . . and then the touchpad is still NOT activated . . not working . . . ,
>   _then, you reboot the system_ and try the touchpad (**WITHOUT doing the combo key of Function + F5**) and it still does not work?

ps - you shouldn't have to be in the bios unless there is a switch/option there for touchpad.   normally not the case (just like you don't need to activate an option in BIOS for your mouse to work . . . which it does work correct?)

---

