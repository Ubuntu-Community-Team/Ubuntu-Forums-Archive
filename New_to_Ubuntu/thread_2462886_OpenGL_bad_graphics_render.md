---
title: "OpenGL bad graphics render"
date: 2021-05-29
forum: New to Ubuntu
---

### Post by abobusabobusabobus on 2021-05-29
[COLOR=#333333][FONT=&amp]Hi i have problem with OpenGL graphics.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]i`m using Ubuntu 20.04 and have legacy notebook Lenovo G700 that runs on Celeron 1005M (with integrated video) and haves 4gb ram.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]when i run any program that uses OpenGL i see half of graphics turns into transparent triangles (screenshots attached below). i`ve used mint and debian and have same problem on them.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]how can i fix this?
[/FONT][/COLOR][IMG]https://imgur.com/a/4K3lpQW[/IMG][IMG]https://i.imgur.com/vuEFBLe.png[/IMG]
[IMG]https://i.imgur.com/rf9pWZj.jpg[/IMG][COLOR=#333333][FONT=&amp]

[/FONT][/COLOR]```
System:  Kernel: 5.8.0-53-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Xfce 4.14.2 tk: Gtk 3.24.13 info: xfce4-panel wm: xfwm4 
  dm: LightDM 1.30.0 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 20251 v: Lenovo G700 serial: <filter> 
  Chassis: type: 10 v: Lenovo G700 serial: <filter> 
  Mobo: LENOVO model: G700 serial: <filter> UEFI [Legacy]: LENOVO 
  v: 7ACN89WW date: 11/19/2013 
Battery:
  ID-1: BAT0 charge: 37.0 Wh condition: 37.0/42.8 Wh (87%) volts: 12.2/10.8 
  model: Lenovo LNV-L11M6Y01 type: Li-ion serial: <filter> status: Full 
CPU:
  Topology: Dual Core model: Intel Celeron 1005M bits: 64 type: MCP 
  arch: Ivy Bridge rev: 9 L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 7582 
  Speed: 1197 MHz min/max: 1200/1900 MHz Core speeds (MHz): 1: 1197 2: 1197 
Graphics:
  Device-1: Intel 3rd Gen Core processor Graphics vendor: Lenovo 
  driver: i915 v: kernel bus ID: 00:02.0 chip ID: 8086:0156 
  Display: x11 server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1600x900~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 2500 (IVB GT1) 
  v: 4.2 Mesa 21.2.0-devel (git-cd34c7f 2021-05-25 focal-oibaf-ppa) 
  compat-v: 3.0 direct render: Yes 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio vendor: Lenovo 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 chip ID: 8086:1e20 
  Sound Server: ALSA v: k5.8.0-53-generic 
Network:
  Device-1: Qualcomm Atheros AR9485 Wireless Network Adapter vendor: Lenovo 
  driver: ath9k v: kernel port: 3040 bus ID: 02:00.0 chip ID: 168c:0032 
  IF: wlp2s0 state: up mac: <filter> 
  Device-2: Qualcomm Atheros AR8162 Fast Ethernet vendor: Lenovo driver: alx 
  v: kernel port: 2000 bus ID: 03:00.0 chip ID: 1969:1090 
  IF: enp3s0 state: down mac: <filter> 
  Device-3: Qualcomm Atheros AR3012 Bluetooth 4.0 type: USB driver: btusb 
  bus ID: 1-1.4:6 chip ID: 0cf3:3004 serial: <filter> 
Drives:
  Local Storage: total: 704.24 GiB used: 97.54 GiB (13.9%) 
  ID-1: /dev/sda vendor: Seagate model: ST500LT012-9WS142 size: 465.76 GiB 
  speed: 3.0 Gb/s rotation: 5400 rpm serial: <filter> rev: LVM1 scheme: GPT 
  ID-2: /dev/sdb type: USB vendor: A-Data model: SD700 size: 238.47 GiB 
  serial: <filter> rev: 9304 scheme: MBR 
Partition:
  ID-1: / size: 22.79 GiB used: 18.23 GiB (80.0%) fs: ext4 dev: /dev/sdb5 
  ID-2: /boot size: 938.0 MiB used: 139.6 MiB (14.9%) fs: ext2 
  dev: /dev/sdb1 
  ID-3: /home size: 209.89 GiB used: 79.18 GiB (37.7%) fs: ext4 
  dev: /dev/sdb6 
Sensors:
  System Temperatures: cpu: 50.0 C mobo: 50.0 C 
  Fan Speeds (RPM): N/A 
Repos:
  Active apt repos in: /etc/apt/sources.list 
  1: deb http://ru.archive.ubuntu.com/ubuntu/ focal main restricted
  2: deb http://ru.archive.ubuntu.com/ubuntu/ focal-updates main restricted
  3: deb http://ru.archive.ubuntu.com/ubuntu/ focal universe
  4: deb http://ru.archive.ubuntu.com/ubuntu/ focal-updates universe
  5: deb http://ru.archive.ubuntu.com/ubuntu/ focal multiverse
  6: deb http://ru.archive.ubuntu.com/ubuntu/ focal-updates multiverse
  7: deb http://ru.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
  8: deb http://security.ubuntu.com/ubuntu focal-security main restricted
  9: deb http://security.ubuntu.com/ubuntu focal-security universe
  10: deb http://security.ubuntu.com/ubuntu focal-security multiverse
  Active apt repos in: /etc/apt/sources.list.d/google-chrome.list 
  1: deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
  Active apt repos in: /etc/apt/sources.list.d/kisak-ubuntu-kisak-mesa-focal.list 
  1: deb http://ppa.launchpad.net/kisak/kisak-mesa/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/megasync.list 
  1: deb https://mega.nz/linux/MEGAsync/xUbuntu_20.04/ ./
  Active apt repos in: /etc/apt/sources.list.d/microsoft-prod.list 
  1: deb [arch=amd64] https://packages.microsoft.com/ubuntu/20.04/prod focal main
  Active apt repos in: /etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-focal.list 
  1: deb http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu focal main
  No active apt repos in: /etc/apt/sources.list.d/phablet-team-ubuntu-tools-focal.list 
  Active apt repos in: /etc/apt/sources.list.d/steam.list 
  1: deb [arch=amd64,i386] https://repo.steampowered.com/steam/ stable steam
  2: deb-src [arch=amd64,i386] https://repo.steampowered.com/steam/ stable steam
  Active apt repos in: /etc/apt/sources.list.d/vscode.list 
  1: deb [arch=amd64,arm64,armhf] http://packages.microsoft.com/repos/code stable main
  Active apt repos in: /etc/apt/sources.list.d/windscribe-repo.list 
  1: deb https://repo.windscribe.com/ubuntu bionic main
Info:
  Processes: 233 Uptime: 44m Memory: 3.74 GiB used: 1.74 GiB (46.6%) 
  Init: systemd v: 245 runlevel: 5 Compilers: gcc: 9.3.0 alt: 9 Shell: zsh 

  v: 5.8 running in: mate-terminal inxi: 3.0.38
```[COLOR=#333333][FONT=&amp]
[/FONT][/COLOR]

---

### Post by mikewhatever on 2021-05-29
I don't see any "transparent triangles", but whatever you want fixed, get the source code, study it, and hack away.

---

### Post by monkeybrain20122 on 2021-05-29
Can you do 

```
glxinfo|egrep "OpenGL vendor|OpenGL renderer"
```

and post outputs?

---

### Post by abobusabobusabobus on 2021-05-30
&#9654;glxinfo|egrep "OpenGL vendor|OpenGL renderer"


OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 2500 (IVB GT1)

---

### Post by mastablasta on 2021-05-31
i also don't see any transparent triangles. could this be a monitor issue? can you hook up an external one & see what happens?

---

