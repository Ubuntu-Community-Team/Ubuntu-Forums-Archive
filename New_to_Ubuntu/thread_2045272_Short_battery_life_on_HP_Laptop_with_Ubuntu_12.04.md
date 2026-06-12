---
title: "Short battery life on HP Laptop with Ubuntu 12.04"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by gsingh2011 on 2012-08-20
I just installed Ubuntu 12.04 64 bit on my laptop and everything is great except the battery life. I installed powertop and the power consumption varies between 27 and 40 watts when no other programs are running. From what I can find on google, that's fairly high.

How can I debug this? Powertop gives me a list of things that are using power, but I don't know what to do with that data. Here's what it tells me:

**Overview page**
```
Summary: 618.0 wakeups/second,  0.0 GPU ops/second and 0.0 VFS ops/sec

                Usage       Events/s    Category       Description
             27.5 ms/s     131.2        Process        /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
            612.7 pkts/s                Device         Network interface: wlan1 (iwlwifi)
              4.6 ms/s     135.7        Interrupt      PS/2 Touchpad / Keyboard / Mouse
             18.7 ms/s      47.3        Process        compiz
             15.2 ms/s      32.4        Process        gnome-terminal
             10.1 ms/s      25.2        Process        /opt/google/chrome/chrome --type=renderer --lang=en-GB --force-fieldtrials=ConnCountImpac
              6.8 ms/s      33.3        Process        /opt/google/chrome/chrome
              1.6 ms/s      52.4        Timer          tick_sched_timer
              1.6 ms/s      51.1        Interrupt      [54] i915
              1.1 ms/s      32.2        Timer          hrtimer_wakeup
              7.1 ms/s       0.0        kWork          acpi_os_execute_deferred
              2.6 ms/s       3.7        Process        /usr/lib/unity/unity-panel-service
              2.3 ms/s       1.2        Process        /usr/lib/indicator-appmenu/hud-service
            605.4 µs/s       9.5        Process        syndaemon -i 2.0 -K -R -t
            635.3 µs/s       6.9        Process        /opt/google/chrome/chrome --type=renderer --lang=en-GB --force-fieldtrials=ConnCountImpac
            654.8 µs/s       6.6        Interrupt      [6] tasklet(softirq)
            179.5 µs/s       7.6        Process        [rtsx-polling]
              1.0 ms/s       3.1        Process        //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
              0.8 ms/s       3.8        Process        /usr/lib/bamf/bamfdaemon
              1.2 ms/s       0.4        Process        powertop
              0.7 ms/s       2.0        Process        /usr/lib/indicator-application/indicator-application-service
            578.0 µs/s       2.5        Process        /usr/lib/gnome-settings-daemon/gnome-settings-daemon
            306.1 µs/s       2.3        Process        /usr/bin/gtk-window-decorator
              0.7 ms/s       0.0        Timer          delayed_work_timer_fn
             78.7 µs/s       3.3        kWork          ieee80211_iface_work
            464.0 µs/s       1.1        Interrupt      [7] sched(softirq)
            416.9 µs/s       0.9        Process        nm-applet
            544.1 µs/s       0.0        kWork          do_dbs_timer
             33.4 µs/s       2.7        kWork          iwl_bg_run_time_calib_work
            460.3 µs/s       0.0        Interrupt      [52] iwlwifi
            392.2 µs/s       0.2        Interrupt      [1] timer(softirq)
            276.1 µs/s       0.1        Process        /usr/sbin/irqbalance
             43.7 µs/s       1.3        Interrupt      [4] block(softirq)
             69.1 µs/s       1.0        Process        /usr/lib/gvfs/gvfs-afc-volume-monitor


```

**Device Stats page**
```
   Usage     Device name
             13.1%        CPU use
            216.9 pkts/s  Network interface: wlan1 (iwlwifi)
            100.0%        Audio codec hwC0D3: Intel
            100.0%        Audio codec hwC0D0: IDT
             10.0%        Display backlight
            100.0%        Radio device: iwlwifi
            100.0%        USB Device: usb-device-8087-0024
            100.0%        USB Device: usb-device-8086-0189
            100.0%        PCI Device: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader
            100.0%        PCI Device: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader
            100.0%        PCI Device: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
            100.0%        PCI Device: Intel Corporation 2nd Generation Core Processor Family DRAM Controller
            100.0%        Radio device: hp-wmi
            100.0%        Radio device: hp-wmi
            100.0%        PCI Device: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]
            100.0%        Radio device: btusb
            100.0%        PCI Device: Intel Corporation Centrino Wireless-N 1030
            100.0%        USB Device: usb-device-138a-0018
            100.0%        USB Device: usb-device-8087-0024
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3
            100.0%        PCI Device: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
            100.0%        PCI Device: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller
            100.0%        USB device: EHCI Host Controller
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2
            100.0%        USB device: EHCI Host Controller
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4
            100.0%        PCI Device: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
              0.0 pkts/s  Network interface: eth0 (r8169)
              0.0%        USB device: HP TrueVision HD (HP TrueVision HD)
              0.0%        USB device: xHCI Host Controller

```

---

### Post by Moose on 2012-08-20
Hmmm, do you have many processes running at once? That can be a factor. I don't know 'bout ubuntu, but when i had Windows 7 i had a HP G62 Notebook laptop and battery only lasted 30 mins at the most. I sometimes run out of battery pretty quick on Ubuntu aswell. I don't know if its the main cause of your problem but try to run less programs and it might help your Laptop live longer.. Sorry i couldn't help specifically.
 
-Anarchy

---

### Post by Jakin on 2012-08-20
try 

sudo apt-get install laptop-mode-tools



see if you save battery :)

---

### Post by Toz on 2012-08-20
I have an HP 6730b and get about 27W usage (and about 2:30 battery time - which is similar to what I was getting when Windows was installed) - most of it coming from firefox, flash and my twitter client. Have a look at the tunables section. How many of them are rated Bad? You could try adjusting those to see if you get any further power savings.

---

