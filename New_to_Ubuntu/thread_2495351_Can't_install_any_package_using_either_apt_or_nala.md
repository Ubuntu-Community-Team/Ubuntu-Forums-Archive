---
title: "Can't install any package using either apt or nala"
date: 2024-02-15
forum: New to Ubuntu
---

### Post by hoscorto on 2024-02-15
When I try to install any package it gives me this error :

```
0 upgraded, 8 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,251 kB of archives.
After this operation, 6,598 kB disk space will be freed.
(Reading database ... 257050 files and directories currently installed.)
Removing linux-image-6.5.0-10-generic (6.5.0-10.10) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.5.0-10-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-15-generic
Found initrd image: /boot/initrd.img-6.5.0-15-generic
Found linux image: /boot/vmlinuz-6.5.0-13-generic
Found initrd image: /boot/initrd.img-6.5.0-13-generic
Found memtest86+x64 image: /boot/memtest86+x64.bin
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows 10 on /dev/sdb1
Found Ubuntu 20.04.5 LTS (20.04) on /dev/sdb5
Adding boot menu entry for UEFI Firmware Settings ...
/etc/grub.d/proxifiedScripts/linux: 1: version_find_latest: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-6.5.0-10-generic (--remove):
installed linux-image-6.5.0-10-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
linux-image-6.5.0-10-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Also when I try upgrade system using software updater it tells me : "Not all updates can be installed" and I can do partial upgrade[/INDENT]

---

### Post by ajgreeny on 2024-02-15
Please show us full details of your hardware and software with output from terminal command ```
inxi -Fzxr
```
Copy that output using the mouse to highlight and then right click in the highlighted text (or use Ctrl+Shift+C) and paste it in your reply usinge **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by Andreyshel on 2024-02-15
Here are a couple of options to solve this. 
[https://askubuntu.com/questions/1491726/dpkg-error-after-upgrading-to-ubuntu-23-10](https://askubuntu.com/questions/1491726/dpkg-error-after-upgrading-to-ubuntu-23-10)

---

### Post by hoscorto on 2024-02-15
```

System:
  Kernel: 6.5.0-13-generic arch: x86_64 bits: 64 compiler: N/A Desktop: GNOME
    v: 45.2 Distro: Ubuntu 23.10 (Mantic Minotaur)
Machine:
  Type: Desktop Mobo: MSI model: B85-G43 GAMING (MS-7816) v: 2.0
    serial: <superuser required> BIOS: American Megatrends v: 12.7
    date: 07/18/2014
CPU:
  Info: quad core model: Intel Core i5-4460 bits: 64 type: MCP arch: Haswell
    rev: 3 cache: L1: 256 KiB L2: 1024 KiB L3: 6 MiB
  Speed (MHz): avg: 1238 high: 1978 min/max: 800/3400 cores: 1: 801 2: 1978
    3: 1375 4: 800 bogomips: 25599
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: AMD Curacao XT / Trinidad [Radeon R7 370 R9 270X/370X]
    vendor: PC Partner / Sapphire driver: radeon v: kernel arch: GCN-1
    bus-ID: 01:00.0 temp: 49.0 C
  Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 23.2.0 driver: X:
    loaded: radeon unloaded: fbdev,modesetting,vesa dri: radeonsi gpu: radeon
    resolution: 1: 1920x1080~144Hz 2: 1920x1080~60Hz
  API: OpenGL v: 4.5 Mesa 23.2.1-1ubuntu3.1 renderer: PITCAIRN ( LLVM
    15.0.7 DRM 2.50 6.5.0-13-generic) direct-render: Yes
Audio:
  Device-1: Intel 8 Series/C220 Series High Definition Audio
    vendor: Micro-Star MSI 8 driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  Device-2: AMD Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000
    Series] vendor: PC Partner / Sapphire driver: snd_hda_intel v: kernel
    bus-ID: 01:00.1
  Device-3: Kingston HyperX Cloud Flight S
    driver: hid-generic,snd-usb-audio,usbhid type: USB bus-ID: 3-11:4
  API: ALSA v: k6.5.0-13-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: active
Network:
  Device-1: Qualcomm Atheros Killer E220x Gigabit Ethernet
    vendor: Micro-Star MSI driver: alx v: kernel port: d000 bus-ID: 03:00.0
  IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
  IF-ID-1: virbr0 state: down mac: <filter>
Drives:
  Local Storage: total: 1.78 TiB used: 72.74 GiB (4.0%)
  ID-1: /dev/sda vendor: Samsung model: SSD 870 QVO 1TB size: 931.51 GiB
  ID-2: /dev/sdb vendor: Kingston model: SA400S37960G size: 894.25 GiB
Partition:
  ID-1: / size: 915.32 GiB used: 72.74 GiB (7.9%) fs: ext4 dev: /dev/sda3
  ID-2: /boot/efi size: 512 MiB used: 6.1 MiB (1.2%) fs: vfat dev: /dev/sda2
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 50.0 C mobo: N/A gpu: radeon temp: 48.0 C
  Fan Speeds (rpm): N/A
Repos:
  Packages: 2599
  Active apt repos in: /etc/apt/sources.list
    1: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic main restricted
    2: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic-updates main restricted
    3: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic universe
    4: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic-updates universe
    5: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic multiverse
    6: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic-updates multiverse
    7: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic-backports main restricted universe multiverse
    8: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic-security main restricted
    9: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic-security universe
    10: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic-security multiverse
  No active apt repos in: /etc/apt/sources.list.d/audio-recorder-ubuntu-ppa-lunar.list
  No active apt repos in: /etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-jammy.list
  Active apt repos in: /etc/apt/sources.list.d/google-chrome.list
    1: deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main
  Active apt repos in: /etc/apt/sources.list.d/mozillateam-ubuntu-ppa-jammy.list
    1: deb https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu/ mantic main
  Active apt repos in: /etc/apt/sources.list.d/nala-sources.list
    1: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic multiverse
    2: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic multiverse
    3: deb http://mirror.library.ucy.ac.cy/linux/ubuntu/archive/ mantic multiverse
  No active apt repos in: /etc/apt/sources.list.d/obsproject-ubuntu-obs-studio-lunar.list
  Active apt repos in: /etc/apt/sources.list.d/teejee2008-ubuntu-timeshift-jammy.list
    1: deb https://ppa.launchpadcontent.net/teejee2008/timeshift/ubuntu/ mantic main
  Active apt repos in: /etc/apt/sources.list.d/vscode.list
    1: deb [arch=amd64,arm64,armhf] http://packages.microsoft.com/repos/code stable main
  No active apt repos in: /etc/apt/sources.list.d/audio-recorder-ubuntu-ppa-mantic.sources
  Active apt repos in: /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-mantic.sources
    1: deb https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/ mantic main
Info:
  Processes: 265 Uptime: 32m Memory: total: 32 GiB available: 31.27 GiB
  used: 2.34 GiB (7.5%) Init: systemd target: graphical (5) Compilers:
  gcc: 13.2.0 Shell: Zsh v: 5.9 inxi: 3.3.29
[COLOR=#000000]
```[/COLOR]

---

### Post by hoscorto on 2024-02-15
> **Andreyshel said:**
> Here are a couple of options to solve this. 
[https://askubuntu.com/questions/1491726/dpkg-error-after-upgrading-to-ubuntu-23-10](https://askubuntu.com/questions/1491726/dpkg-error-after-upgrading-to-ubuntu-23-10)

Thanks a lot, this fixed it.

---

### Post by ajgreeny on 2024-02-15
Great!

I still think it a great pity that grub-customiser is still available as it seems to cause more of these sort of problems than it ever helps make changes to grub.
I hope this has made you remove grub-customiser from your system and to never use it again!

---

### Post by hoscorto on 2024-02-15
> **ajgreeny said:**
> Great!

I still think it a great pity that grub-customiser is still available as it seems to cause more of these sort of problems than it ever helps make changes to grub.
I hope this has made you remove grub-customiser from your system and to never use it again!

My first step trying to solve the error alone was in fact uninstalling it, I was only using it to reorder my boot anyway.

---

