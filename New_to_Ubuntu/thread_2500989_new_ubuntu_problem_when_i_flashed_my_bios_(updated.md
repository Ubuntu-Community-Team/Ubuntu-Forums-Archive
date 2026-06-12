---
title: "new ubuntu problem when i flashed my bios (updated to newest non-beta)"
date: 2024-09-18
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2024-09-18
well, i tried to flash newest bios updates from msi for my motherboard.  now i'm having a new problem.   i can get at my bios now, but after i set time/ date, it freezes at a new screen and this is what it says.

SCREEN COMPUTER FROZEN ON READS:

HEADING:  gnu grub version 2.06-13+deb12u1

minimal BASH-like line editing is supported.  for the first word, TAB  lists of possible command completions.  anywhere else tab lists possible  device or file completions.

grub>

i hit tab and tried using those commands but kept getting something about arguments being incomplete or something like that.

SYSTEM STATS (copied and pasted from a previous post since i can't get o.s. to open):


System:
  Kernel: 6.8.0-40-generic x86_64 bits: 64 Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: Micro-Star model: MEG X570 UNIFY (MS-7C35) v: 2.0
    serial: <superuser required> UEFI: American Megatrends LLC. v: A.E2
    date: 08/01/2022
CPU:
  Info: 12-core AMD Ryzen 9 5900X [MT MCP] speed (MHz): avg: 2532
    min/max: 2200/4950
Graphics:
  Device-1: AMD Navi 21 [Radeon RX 6800/6800 XT / 6900 XT] driver: amdgpu
    v: kernel
  Device-2: NVIDIA GP107 [GeForce GTX 1050 Ti] driver: nvidia v: 535.183.01
  Device-3: NVIDIA GP107 [GeForce GTX 1050 Ti] driver: nvidia v: 535.183.01
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: X:
    loaded: amdgpu,ati,modesetting,nouveau,nvidia,radeon unloaded: fbdev,vesa
    gpu: amdgpu,nvidia,nvidia resolution: 1: 1920x1080~75Hz 2: 1920x1080~60Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.2.1-1ubuntu3.1~22.04.2
Network:
  Device-1: Realtek RTL8125 2.5GbE driver: r8169
  Device-2: Intel Wi-Fi 6 AX210/AX211/AX411 160MHz driver: iwlwifi
Drives:
  Local Storage: total: 2.05 TiB used: 17.06 GiB (0.8%)
Info:
  Processes: 459 Uptime: 3h 42m Memory: 62.71 GiB used: 4.01 GiB (6.4%)
  Shell: Bash inxi: 3.3.13 				

oh yeah i INSTALLED 20.04 (focal fossa) copied and pasted that info from previous post after having difficulties with multiple workstations magically opening up and not being able to use my computer the way i wanted too

---

### Post by TheFu on 2024-09-18
Flashing a BIOS often resets all Linux-friendly settings, so got through all the screens and verify the 5 or so settings necessary for Linux to be happy are still set correctly.

Most computers have a way to use the older BIOS, so you might try that and also search the motherboard forums for specific issues with the new BIOS impacting Linux OSes.

---

