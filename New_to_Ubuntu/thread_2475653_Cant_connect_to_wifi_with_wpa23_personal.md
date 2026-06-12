---
title: "Cant connect to wifi with wpa2/3 personal"
date: 2022-06-03
forum: New to Ubuntu
---

### Post by senkoooo on 2022-06-03
Good morning/afternoon/evening/evening. I want to ask why every time I install linux it doesn't want to connect to my cellphone's internet hotspot with personal wpa2/3 security. But if the security is changed to wpa2 personal wifi can be connected. If I want to connect to mixed wpa what should I do? Wifi using intel ac 7265, thinkpad x250. Thank you.

I used Xubuntu

---

### Post by ajgreeny on 2022-06-03
Which version of Xubuntu?

Please show us the output of command
***inxi -Fzx*** 
using code tags for your output please. 

See my signature below for a How-To.

---

### Post by senkoooo on 2022-06-03
```
xubuntu@xubuntu:~$ inxi -Fzx
System:
  Kernel: 5.15.0-25-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: Xfce 4.16.0 Distro: Ubuntu 22.04 (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 20CLA2M5JP v: ThinkPad X250
    serial: <superuser required>
  Mobo: LENOVO model: 20CLA2M5JP v: SDK0E50510 WIN
    serial: <superuser required> UEFI: LENOVO v: N10ET36W (1.15 )
    date: 06/19/2015
Battery:
  ID-1: BAT0 charge: 16.5 Wh (78.9%) condition: 20.9/23.2 Wh (89.9%)
    volts: 11.9 min: 11.1 model: SANYO 45N1773 status: Not charging
  ID-2: BAT1 charge: 8.1 Wh (47.4%) condition: 17.1/23.5 Wh (72.9%)
    volts: 11.2 min: 11.4 model: LGC 45N1127 status: Discharging
CPU:
  Info: dual core model: Intel Core i5-5200U bits: 64 type: MT MCP
    arch: Broadwell rev: 4 cache: L1: 128 KiB L2: 512 KiB L3: 3 MiB
  Speed (MHz): avg: 1497 min/max: 500/2700 cores: 1: 1497 2: 1497 3: 1497
    4: 1497 bogomips: 17559
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3
Graphics:
  Device-1: Intel HD Graphics 5500 vendor: Lenovo driver: i915 v: kernel
    bus-ID: 00:02.0
  Device-2: Silicon Motion - Taiwan (formerly Feiya ) Motion SM371 Camera
    type: USB driver: uvcvideo bus-ID: 2-8:5
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1366x768~60Hz
  OpenGL: renderer: Mesa Intel HD Graphics 5500 (BDW GT2)
    v: 4.6 Mesa 22.0.1 direct render: Yes
Audio:
  Device-1: Intel Broadwell-U Audio vendor: Lenovo driver: snd_hda_intel
    v: kernel bus-ID: 00:03.0
  Device-2: Intel Wildcat Point-LP High Definition Audio vendor: Lenovo
    driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  Sound Server-1: ALSA v: k5.15.0-25-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Ethernet I218-LM vendor: Lenovo driver: e1000e v: kernel
    port: 3080 bus-ID: 00:19.0
  IF: enp0s25 state: down mac: <filter>
  Device-2: Intel Wireless 7265 driver: iwlwifi v: kernel bus-ID: 03:00.0
  IF: wlp3s0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth wireless interface type: USB driver: btusb v: 0.8
    bus-ID: 2-7:4
  Report: hciconfig ID: hci0 rfk-id: 1 state: up address: <filter>
    bt-v: 2.1 lmp-v: 4.2
Drives:
  Local Storage: total: 267.13 GiB used: 2.52 GiB (0.9%)
  ID-1: /dev/sda vendor: Samsung model: MZ7TD256HAFV-000L9 size: 238.47 GiB
  ID-2: /dev/sdb type: USB vendor: SanDisk model: Cruzer Force
    size: 28.65 GiB
Partition:
  ID-1: / size: 3.82 GiB used: 166.3 MiB (4.2%) fs: overlay source: ERR-102
Swap:
  Alert: No swap data was found.
Sensors:
  System Temperatures: cpu: 41.0 C pch: 41.5 C mobo: N/A
  Fan Speeds (RPM): fan-1: 3063
Info:
  Processes: 214 Uptime: 2m Memory: 7.65 GiB used: 1.04 GiB (13.6%)
  Init: systemd runlevel: 5 Compilers: gcc: N/A Packages: 1727 Shell: Bash
  v: 5.1.16 inxi: 3.3.13
```

---

