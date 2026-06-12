---
title: "audio problem, dummy output"
date: 2023-02-14
forum: New to Ubuntu
---

### Post by abba1 on 2023-02-14
I  installed Ubuntu 22.04.1 lts and i kept windows for dual boot
Once installed some components do not work like wifi (it works randomly,)  sound card mic and webcam

Main issue, for my needs, is the audio
I alredy tried various suggestion but, since now, nothing worked





```
c@B:~$ lspci
00:00.0 Host bridge: Intel Corporation Gemini Lake Host Bridge (rev 06)
00:00.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Dynamic Platform and Thermal Framework Processor Participant (rev 06)
00:02.0 VGA compatible controller: Intel Corporation GeminiLake [UHD Graphics 600] (rev 06)
00:0e.0 Multimedia audio controller: Intel Corporation Celeron/Pentium Silver Processor High Definition Audio (rev 06)
00:0f.0 Communication controller: Intel Corporation Celeron/Pentium Silver Processor Trusted Execution Engine Interface (rev 06)
00:12.0 SATA controller: Intel Corporation Celeron/Pentium Silver Processor SATA Controller (rev 06)
00:14.0 PCI bridge: Intel Corporation Gemini Lake PCI Express Root Port (rev f6)
00:15.0 USB controller: Intel Corporation Celeron/Pentium Silver Processor USB 3.0 xHCI Controller (rev 06)
00:16.0 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO I2C Host Controller (rev 06)
00:16.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO I2C Host Controller (rev 06)
00:16.2 Signal processing controller: Intel Corporation Device 31b0 (rev 06)
00:16.3 Signal processing controller: Intel Corporation Device 31b2 (rev 06)
00:17.0 Signal processing controller: Intel Corporation Device 31b4 (rev 06)
00:17.1 Signal processing controller: Intel Corporation Device 31b6 (rev 06)
00:17.2 Signal processing controller: Intel Corporation Device 31b8 (rev 06)
00:17.3 Signal processing controller: Intel Corporation Device 31ba (rev 06)
00:18.0 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 06)
00:18.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 06)
00:18.2 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 06)
00:18.3 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO UART Host Controller (rev 06)
00:19.0 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller (rev 06)
00:19.1 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller (rev 06)
00:19.2 Signal processing controller: Intel Corporation Celeron/Pentium Silver Processor Serial IO SPI Host Controller (rev 06)
00:1c.0 SD Host controller: Intel Corporation Celeron/Pentium Silver Processor SDA Standard Compliant SD Host Controller (rev 06)
00:1e.0 SD Host controller: Intel Corporation Device 31d0 (rev 06)
00:1f.0 ISA bridge: Intel Corporation Celeron/Pentium Silver Processor LPC Controller (rev 06)
00:1f.1 SMBus: Intel Corporation Celeron/Pentium Silver Processor Gaussian Mixture Model (rev 06)
```






```
c@B:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: sofhdadsp [sof-hda-dsp], device 1: HDMI1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 2: HDMI2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 3: HDMI3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```




```
c@B:~$ amixer
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'PGA2.0 2 Master',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 32
  Mono:
  Front Left: Playback 32 [100%] [0.00dB]
  Front Right: Playback 32 [100%] [0.00dB]
Simple mixer control 'PGA3.0 3 Master',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 32
  Mono:
  Front Left: Playback 32 [100%] [0.00dB]
  Front Right: Playback 32 [100%] [0.00dB]
Simple mixer control 'PGA4.0 4 Master',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 32
  Mono:
  Front Left: Playback 32 [100%] [0.00dB]
  Front Right: Playback 32 [100%] [0.00dB]

```



```
c@B:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Intel Geminilake HDMI
```



```
c@B:~$ inxi -Fxz
System:
  Kernel: 5.15.0-60-generic x86_64 bits: 64 compiler: gcc v: 11.3.0
    Desktop: GNOME 42.5 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: MEDIACOM product: M-SB151 v: N/A
    serial: <superuser required>
  Mobo: MEDIACOM model: N/A serial: <superuser required>
    UEFI: American Megatrends v: 0.5.0_P6S43M2E0F0L2B0T0P2G00A0U0D605_ENE
    date: 07/07/2021
Battery:
  ID-1: BAT0 charge: 32.7 Wh (92.1%) condition: 35.5/35.5 Wh (100.0%)
    volts: 7.4 min: N/A model: Emdoor Li-ion Battery status: Discharging
CPU:
  Info: dual core model: Intel Celeron N4020 bits: 64 type: MCP
    arch: Goldmont Plus rev: 8 cache: L1: 112 KiB L2: 4 MiB
  Speed (MHz): avg: 1530 high: 1534 min/max: 800/2800 cores: 1: 1534
    2: 1526 bogomips: 4377
  Flags: ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel GeminiLake [UHD Graphics 600] vendor: nCipher Security
    driver: i915 v: kernel bus-ID: 00:02.0
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: i915 resolution: 1280x720~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics 600 (GLK 2) v: 4.6 Mesa 22.2.5
    direct render: Yes
Audio:
  Device-1: Intel Celeron/Pentium Silver Processor High Definition Audio
    driver: sof-audio-pci-intel-apl bus-ID: 00:0e.0
  Sound Server-1: ALSA v: k5.15.0-60-generic running: yes
  Sound Server-2: JACK v: 0.125.0rc1 running: no
  Sound Server-3: PulseAudio v: 15.99.1 running: yes
  Sound Server-4: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8152 Fast Ethernet Adapter type: USB driver: r8152
    bus-ID: 1-7:8
  IF: enx50a1320e8c60 state: down mac: <filter>
  IF-ID-1: wlx38ca73505282 state: up mac: <filter>
Bluetooth:
  Device-1: Realtek RTL8723BU 802.11b/g/n WLAN Adapter type: USB
    driver: btusb,rtl8xxxu bus-ID: 1-4:3
  Report: hciconfig ID: hci0 rfk-id: 1 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 115.31 GiB used: 20.65 GiB (17.9%)
  ID-1: /dev/mmcblk0 model: SCA128 size: 115.31 GiB
Partition:
  ID-1: / size: 55.61 GiB used: 20.57 GiB (37.0%) fs: ext4
    dev: /dev/mmcblk0p5
  ID-2: /boot/efi size: 96 MiB used: 74.4 MiB (77.5%) fs: vfat
    dev: /dev/mmcblk0p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 4 MiB (0.2%) file: /swapfile
Sensors:
  System Temperatures: cpu: 48.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 227 Uptime: 50m Memory: 3.65 GiB used: 2.34 GiB (64.0%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.3.0 Packages: 2435 Shell: Bash
  v: 5.1.16 inxi: 3.3.13
```

---

### Post by Autodave on 2023-02-15
I wonder if you got a bad download or a bad install.  If you still have your installation medium, try booting to that and see what works and what doesn't.  If you have the same problems, then try downloading again and make a new installation medium and try that.

---

### Post by abba1 on 2023-02-15
> **Autodave said:**
> I wonder if you got a bad download or a bad install.  If you still have your installation medium, try booting to that and see what works and what doesn't.  If you have the same problems, then try downloading again and make a new installation medium and try that.

Thx autodave, I already tried to install even different flavors but the problem persist

I guess it's a driver related problem.

I searched  and I found that other people encountered similar issues with audio card in some laptop

---

