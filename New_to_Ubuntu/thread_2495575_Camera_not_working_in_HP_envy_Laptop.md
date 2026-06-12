---
title: "Camera not working in HP envy Laptop"
date: 2024-02-23
forum: New to Ubuntu
---

### Post by Ranjitsinh_B._Bhal on 2024-02-23
[COLOR=#ECECEC][FONT=Söhne]The camera is not working in Skype and all other applications on my HP Envy Laptop[/FONT][/COLOR]

---

### Post by him610 on 2024-02-23
Welcome to the forums.
Insufficient information provided. 
```
 inxi -Fxxz 
```
Please post results between code tags.

---

### Post by Ranjitsinh_B._Bhal on 2024-02-24
> **him610 said:**
> Welcome to the forums.
Insufficient information provided. 
```
 inxi -Fxxz 
```
Please post results between code tags.

```
System:
  Kernel: 6.5.0-15-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    tk: GTK 3.24.33 wm: gnome-shell dm: GDM3
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Convertible System: HP product: HP ENVY x360 2-in-1 Laptop 13-bf0xxx
  Mobo: HP model: 8A28 v: 21.46 UEFI: Insyde
    v: F.21 date: 10/30/2023
Battery:
  ID-1: BAT1 charge: 16.9 Wh (24.2%) condition: 69.8/66.5 Wh (105.0%)
    volts: 7.7 min: 7.7 model: Hewlett-Packard PABAS0241231 serial: <filter>
    status: Discharging
CPU:
  Info: 10-core (2-mt/8-st) model: 12th Gen Intel Core i5-1230U bits: 64
    type: MST AMCP arch: Alder Lake rev: 4 cache: L1: 928 KiB L2: 6.5 MiB
    L3: 12 MiB
  Speed (MHz): avg: 645 high: 1033 min/max: 400/4400:3300 cores: 1: 745
    2: 703 3: 907 4: 400 5: 994 6: 400 7: 1033 8: 962 9: 400 10: 400 11: 400
    12: 400 bogomips: 40550
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel vendor: Hewlett-Packard driver: i915 v: kernel ports:
    active: eDP-1 empty: DP-1, DP-2, DP-3, DP-4 bus-ID: 00:02.0
    chip-ID: 8086:46aa
  Display: x11 server: X.Org v: 1.21.1.4 compositor: gnome-shell driver: X:
    loaded: modesetting unloaded: fbdev,vesa gpu: i915 display-ID: :1
    screens: 1
  Screen-1: 0 s-res: 2560x1600 s-dpi: 96
  Monitor-1: eDP-1 model: BOE Display res: 2560x1600 dpi: 227
    diag: 337mm (13.3")
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: Intel vendor: Hewlett-Packard driver: N/A bus-ID: 00:05.0
    chip-ID: 8086:465d
  Device-2: Intel vendor: Hewlett-Packard driver: sof-audio-pci-intel-tgl
    bus-ID: 00:1f.3 chip-ID: 8086:51cc
  Sound Server-1: ALSA v: k6.5.0-15-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: no
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Alder Lake-P PCH CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 00:14.3 chip-ID: 8086:51f0
  IF: wlo1 state: up mac: <filter>
Bluetooth:
  Device-1: Intel type: USB driver: btusb v: 0.8 bus-ID: 3-10:2
    chip-ID: 8087:0033
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
Drives:
  Local Storage: total: 476.94 GiB used: 62.26 GiB (13.1%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVL2512HDJD-00BH1
    size: 476.94 GiB speed: 63.2 Gb/s lanes: 4 serial: <filter> temp: 38.9 C
Partition:
  ID-1: / size: 161.85 GiB used: 62.18 GiB (38.4%) fs: ext4
    dev: /dev/nvme0n1p7
  ID-2: /boot/efi size: 256 MiB used: 90.1 MiB (35.2%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 111.8 MiB (5.5%) priority: -2
    file: /swapfile
Sensors:
  System Temperatures: cpu: 27.8 C mobo: 10.0 C
  Fan Speeds (RPM): cpu: 0 fan-2: 0
Info:
  Processes: 380 Uptime: 2d 14h 1m Memory: 15.31 GiB used: 5.03 GiB (32.8%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: N/A Packages: 1958
  apt: 1941 snap: 17 Shell: Bash v: 5.1.16 running-in: gnome-terminal
  inxi: 3.3.13
```

---

