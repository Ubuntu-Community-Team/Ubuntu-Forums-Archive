---
title: "Slow boot time after installing Ubuntu 18.04.1 LTS"
date: 2018-11-08
forum: New to Ubuntu
---

### Post by ni2tre on 2018-11-08
Hi,

I wanted to "revive" my old laptop with a OS that works faster with an older device and I'm very happy with the performance so far when it's already booted. But the boot time is much worse than when I had Windows 10 on it.

System Specs:

```
System:    Host: test-HP-G7000-Notebook-PC Kernel: 4.15.0-36-generic i686
           bits: 32 gcc: 7.3.0
           Desktop: MATE 1.20.1 (Gtk 3.22.30-1ubuntu1)
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: Hewlett-Packard product: HP G7000 Notebook PC v: F.08 serial: N/A
           Mobo: Hewlett-Packard model: 30D9 v: 83.19 serial: N/A
           BIOS: Hewlett-Packard v: F.08 date: 09/13/2007
Battery    BAT0: charge: 4.8 Wh 101.0% condition: 4.8/4.8 Wh (100%)
           model: Hewlett-Packard Primary status: Full
CPU:       Dual core Intel Pentium Dual T2310 (-MCP-) 
           arch: Conroe rev.13 cache: 1024 KB
           flags: (lm nx pae sse sse2 sse3 ssse3) bmips: 5852
           clock speeds: max: 1467 MHz 1: 1241 MHz 2: 1142 MHz
^[[BGraphics:  Card: Intel Mobile GM965/GL960 Integrated Graphics Controller (primary)
           bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1280x800@59.98hz
           OpenGL: renderer: Mesa DRI Intel 965GM x86/MMX/SSE2
           version: 2.1 Mesa 18.0.5 Direct Render: Yes
Audio:     Card Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-36-generic
Network:   Card-1: Broadcom Limited BCM4311 802.11b/g WLAN
           driver: wl bus-ID: 01:00.0
           IF: wlp1s0 state: up mac: <filter>
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too v: 0.9.28 port: 1000 bus-ID: 02:01.0
           IF: enp2s1 state: down mac: <filter>
Drives:    HDD Total Size: 60.0GB (13.4% used)
           ID-1: /dev/sda model: Corsair_Nova_2_S size: 60.0GB
Partition: ID-1: / size: 55G used: 7.5G (15%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 55.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 160 Uptime: 40 min Memory: 491.0/2002.8MB
           Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 


```

systemd-analyze

```
Startup finished in 1min 5.896s (kernel) + 34.696s (userspace) = 1min 40.592s
graphical.target reached after 34.662s in userspace

```

systemd-analyze critical-chain

```
graphical.target @34.662s
&#9492;&#9472;multi-user.target @34.662s
  &#9492;&#9472;getty.target @34.662s
    &#9492;&#9472;getty@tty1.service @34.612s
      &#9492;&#9472;system-getty.slice @34.601s
        &#9492;&#9472;setvtrgb.service @34.580s +17ms
          &#9492;&#9472;systemd-user-sessions.service @2.638s +31ms
            &#9492;&#9472;network.target @2.611s
              &#9492;&#9472;NetworkManager.service @1.810s +799ms
                &#9492;&#9472;dbus.service @1.696s
                  &#9492;&#9472;basic.target @1.450s
                    &#9492;&#9472;sockets.target @1.450s
                      &#9492;&#9472;snapd.socket @1.414s +34ms
                        &#9492;&#9472;sysinit.target @1.412s
                          &#9492;&#9472;systemd-backlight@backlight:acpi_video0.service @2.3
                            &#9492;&#9472;system-systemd\x2dbacklight.slice @2.377s
                              &#9492;&#9472;system.slice @296ms
                                &#9492;&#9472;-.slice @290ms


```

I would appreciate any help!
ni2tre

---

### Post by Autodave on 2018-11-08
First off, that is a rather slow laptop with only 1/2G of Ram  Secondly, Windows 10 does not shut down: it merely hibernates.  Thirdly, Ubuntu is a rather heavy desktop.

First thing that I would do is to either install Lubuntu or possibly (for a little better looking desktop) Xubuntu. Lubuntu would be the fastest desktop to use.  A lighter desktop will make the laptop run a little better. Understand that Lubuntu will not boot up much quicker, but a little faster.  If you want the instant boot that Win 10 had, then don't shut the PC down, but just choose *hibernate*.

For comparison, I have Win 10 and Xubuntu installed on this machine (which is rather fast0.  To dual boot, I had to shut off *fast boot *which is what Win 10 uses to just hibernate when you choose to shut it down.  To boot this machine to Xubuntu takes about 35 seconds. To boot it to Win 10 takes almost 3 minutes.

---

### Post by ni2tre on 2018-11-08
Thank you, I will try Xubuntu then and if that is too slow then Lubuntu.

---

### Post by valvegrid on 2018-11-08
The other thing you can do to speed things up is to replace the HDD with an SSD, that is what I did with my old Toshiba NB-100, I would still be using it, but it was an old 32 bit system and some of my applications were not offered in 32 bit anymore. It had a 32 bit version of Lubuntu on it.

---

### Post by ni2tre on 2018-11-08
> **valvegrid said:**
> The other thing you can do to speed things up is to replace the HDD with an SSD, that is what I did with my old Toshiba NB-100, I would still be using it, but it was an old 32 bit system and some of my applications were not offered in 32 bit anymore. It had a 32 bit version of Lubuntu on it.

Thank you.

I've tried Xubuntu now and it's the same, will try to find some little tweaks that can maybe help speed things up *a little bit* at least because it doesn't bother me too much.

---

### Post by Autodave on 2018-11-08
Understand that the boot time is not going to change much at all: all of these derivatives run the same kernel.  Going to a lighter distro will free up more of your little memory to run programs.

---

