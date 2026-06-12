---
title: "Confused Noob: Where are the System Folders?"
date: 2020-08-04
forum: New to Ubuntu
---

### Post by scayers on 2020-08-04
Hello
Upgraded to 20 today.
I cannot find a way to access the folders with etc, boot, home...I would call them System Folders.
What's the deal?
I am a Mint user learning Ubuntu.
Thank you.
(Does the dollar sign as opposed to the hashtag make a difference?)

||
||
||
 V
```

 $ inxi -Fxz



System:
  Kernel: 5.4.0-42-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Gnome 3.36.3 Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: SAMSUNG product: 300E4A/300E5A/300E7A/3430EA/3530EA 
  v: 0.1 serial: <filter> 
  Mobo: SAMSUNG model: 300E4A/300E5A/300E7A/3430EA/3530EA v: FAB1 
  serial: <filter> UEFI [Legacy]: Phoenix v: 09QA date: 11/02/2012 
Battery:
  ID-1: BAT1 charge: 37.3 Wh condition: 46.6/48.8 Wh (95%) 
  model: SAMSUNG Electronics status: Unknown 
CPU:
  Topology: Dual Core model: Intel Core i3-2310M bits: 64 type: MT MCP 
  arch: Sandy Bridge rev: 7 L2 cache: 3072 KiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 16762 
  Speed: 799 MHz min/max: 800/2100 MHz Core speeds (MHz): 1: 798 2: 798 
  3: 798 4: 798 
Graphics:
  Device-1: Intel 2nd Generation Core Processor Family Integrated Graphics 
  vendor: Samsung Co driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 3000 (SNB GT2) 
  v: 3.3 Mesa 20.0.8 direct render: Yes 
Audio:
  Device-1: Intel 6 Series/C200 Series Family High Definition Audio 
  vendor: Samsung Co driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-42-generic 
Network:
  Device-1: Intel Centrino Wireless-N 100 driver: iwlwifi v: kernel 
  port: efa0 bus ID: 01:00.0 
  IF: wlp1s0 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Samsung Co driver: r8169 v: kernel port: 2000 bus ID: 02:00.0 
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 1.42 TiB used: 769.59 GiB (52.9%) 
  ID-1: /dev/sda vendor: Hitachi model: HTS547550A9E384 size: 465.76 GiB 
  ID-2: /dev/sdb type: USB vendor: SanDisk model: Cruzer Blade 
  size: 29.25 GiB 
  ID-3: /dev/sdc type: USB vendor: SanDisk model: Cruzer Blade 
  size: 29.25 GiB 
  ID-4: /dev/sdd type: USB vendor: Western Digital 
  model: WD My Passport 25E1 size: 931.48 GiB 
Partition:
  ID-1: / size: 130.57 GiB used: 22.55 GiB (17.3%) fs: ext4 dev: /dev/sda5 
  ID-2: swap-1 size: 3.92 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda6 
Sensors:
  System Temperatures: cpu: 55.0 C mobo: 29.8 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 261 Uptime: 32m Memory: 3.76 GiB used: 1.16 GiB (30.9%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38

```

---

### Post by yancek on 2020-08-04
You can cd to any directory in a terminal.  If you are trying to use the File Manager and have the default install, when you open Files from the left panel of the Desktop, the window will have a panel on the left with Other Locations, click that then go to Computer to navigate to different directories.  The dollar sign in a terminal means you are logged in to the terminal as a normal user while the hashtage means with root/sudo privileges.

---

### Post by scayers on 2020-08-04
Thanks, Yancek.
I want to use clamtk to scan the cache, mozilla, boot, and config folders.
I need to get to that directory, which is the parent directory of "home".
In terminal, I cd to what?
Other locations, on 20, doesn't show the system files.
In Mint, it is prominent.

---

### Post by pbear42 on 2020-08-04
He (or she) told you.  Open Files.  Look in the left navigation pane.  Find [COLOR=#ff0000]Other Locations[/COLOR].  Click it.  Now click [COLOR=#ff0000]Computer [/COLOR]in the right pane.

Every desktop and file manager is different.  You have to look around, try branching paths, etc.

---

### Post by scayers on 2020-08-04
Thank you.

---

### Post by sdsurfer on 2020-08-05
There's a couple articles out there that will help understand where things are and why, here's a decent one. Note you will have to sudo to get to/read/modify some of them.

[https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/](https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/)

---

### Post by ActionParsnip on 2020-08-05
MInt is based on Ubuntu (Or Debian, which Ubuntu is based on) and the folders are identical. For the most part in most distributions the folders are in the same locations too. Its one of the beautys of Linux.

---

