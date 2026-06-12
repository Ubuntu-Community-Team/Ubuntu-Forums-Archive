---
title: "never had this happen before with ubuntu"
date: 2024-08-18
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2024-08-18
i moved my firefox window to the right, so i could read AND enter information in the command terminal.  when i finished sliding, i released the window, it dropped then went up toward right corner.  i assumed i had accidentally minimized the window, i clicked on firefox icon and all that happened is that it added a new red dot to the icon.  new window opened i know, but nothing appeared on screen.  where'd it go, how do i get it back without reinstalling the jelly fish.  that computer is my build, and less than a year old.  reinstalling ubuntu and updates took 20 mins when i dumped win10, i'm sure finding the window will take less time.

---

### Post by #&amp;thj^% on 2024-08-18
Use Key Combo <Alt +Tab>

---

### Post by TheFu on 2024-08-19
Might you have dropped it into a different workspace?  

I run with a 2x3 workspace step. These are like virtual monitors.  

In my config, I start in the upper left corner and by moving the mount across boundaries either down once or to the right once, twice, I can access any of the workspaces, leaving the original as it was.  

My window manager shows a small map in the lower right coner of each workspace with an overview of the different 2x3 grid and the windows open on each.  They are just little rectangles, but using the middle mouse button, I can move each window to a different workspace, if I like.  

In my mind, each workspace has a specific use.  One is for coding, so it is setup with all my coding tools and coding documentation.
Another is for any special research I'm doing on something not normally done. Call it a special interest workspace. It is usually for 1 day or less.
Another is for video editing, cutting, transcoding.
Another is for terminals into other systems.
The last workspace is empty. Usually I have 2 empty workspaces. It wouldn't be good to run out.  

I used to use a 3x3 grid of workspaces when I was younger and had more stuff in my daily todo list.  Back then, I had a project management workspace to track time on projects (for billing) and task prioritization/completion.

Anyway, could it be just placed into a different workspace?

---

### Post by cryofreeze666 on 2024-08-26
alt+tab only opens a small window that shows the windows in firefox i have open.  i tried clicking on one of them and nothing happened, it just changed the highlight in that temporary window that disappears as soon as i release alt+tab.

ok restarted machine, still cant get to my firefox,

---

### Post by cryofreeze666 on 2024-08-26
well that could be though why it would be there i don't know, i haven't taught myself workspaces yet, still learning the basics of ubuntu.  oh and by the way, i have no litte squares beside the menu icon.  ok i might have added work spaces, because i open the menu and there are two jellyfish desktops at the top.  how do i close those.

ok i suppose i've opened a workspace, don't know how or when, but if work spaces close when you close all open files what is keeping the desktop open when i power off the machine?  guess i'll try unplugging and cycling power switch while unplugged see if discharging residual helps

---

### Post by nicolasdentremont on 2024-08-26
I believe the default keys for switching between workspaces in Ubuntu is "Windows Key"+Tab. Maybe that will bring you to the workspace that your window is open in.

---

### Post by TheFu on 2024-08-26
Workspaces usually aren't dynamically added or removed.  There is usually a default which depends on your DE/WM and can be modified someway. You and I don't use the same DE or WM, of that I'm certain, so how mine works will be very different from yours.  

Google found this: 
[https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces.html.en](https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces.html.en) 
and
[https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces-switch.html.en](https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces-switch.html.en)

BTW, how things work in the GUI is dependent on the exact DE and the EXACT release you are running.  Seems that GUI programmers like to change things for the sake of change, not because it is better.  That's the main reason I stopped using any DE and use a WM that I've used for nearly 30 yrs now on multiple Unix platforms.  I just got tired of change that didn't actually improve things that mattered to me.  YMMV. We are all different.

---

### Post by Dennis N on 2024-08-27
> ok i suppose i've opened a workspace, don't know how or when, but if work spaces close when you close all open files what is keeping the desktop open when i power off the machine?

A workspace (a.k.a. desktop) closes if you close all windows in that workspace. But you always have one workspace, even if its empty. The Activities Overview shows what is on each workspace. Thumbnails appear across the top if more than one is in use. Click the thumbnails to switch, or use Super+PgUp and Super+PgDn to switch workspaces. You can also drag and drop windows between the displayed workspaces to rearrange. Extensions like "Workspace Indicator" and "All Windows" will help you deal with workspaces. There are also keyboard shortcuts to move windows to another workspace. 

Workspaces are indeed dynamic - a new empty one is added when all are being used. But Gnome allows a fixed number as well by changing a setting.

If you are dragging windows to the edges and they resize, you are possibly tiling them. Ubuntu has a new optional tiling helper that may be active here. Maybe it is crashing and causing the window to disappear?

---

### Post by TheFu on 2024-08-27
We are all guessing on the release and DE being used.  Might be good to have that confirmed.  The easiest way that I know to get it is with 
**$ inxi -bz**

For example, on this machine, 
```
$ inxi -bz
System:
  Kernel: 5.15.0-119-generic x86_64 bits: 64 **Desktop: FVWM 2.6.8**
    **Distro: Linux Mint 21.3 Virginia**
Machine:
  Type: Kvm System: QEMU product: Standard PC (i440FX + PIIX, 1996)
    v: pc-i440fx-focal serial: <superuser required>
  Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: 1.13.0-1ubuntu1.1
    date: 04/01/2014
CPU:
  Info: 2x 1-core AMD EPYC-Rome [SMP] speed (MHz): avg: 4200
Graphics:
  Device-1: Red Hat QXL paravirtual graphic card **driver: qxl** v: kernel
  **Display: x11 server: X.Org** v: 1.21.1.4 driver: X: loaded: N/A
    unloaded: fbdev,modesetting,vesa gpu: qxl note:  X driver n/a
    resolution: 1680x1050~60Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.2.1-1ubuntu3.1~22.04.2
...

```
The **bold**ed items are the main things to know, I think.
So, I'm running Linux Mint 21.3 Virginia using FVWM2 as my desktop and using X.Org with qxl GPU drivers in the example above.

---

### Post by cryofreeze666 on 2024-08-28
_distro:_
ubuntu 22.04.4 jammy jellyfish

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

[h=2][/h] 		 				 				 		 			 				[INDENT] 					not sure if this is pertinent right now, but i cannibalized a few  of my computers to make this one.  except for the motherboard and  processor those are new.  i spent a year researching the passive income  potential, tax laws, and stuff related to crypto mining before i built  this data miner.  i'm currently waiting for answers to my questions  about whether crypto o.s.'s are actual o.s.'s or if they are a program  that needs an o.s. to run.  i'm just misunderstanding the reading on the  minerstat and rave os sites i'm sure. 				[/INDENT]

---

### Post by cryofreeze666 on 2024-08-28
not sure if this is pertinent right now, but i cannibalized a few of my computers to make this one.  except for the motherboard and processor those are new.  i spent a year researching the passive income potential, tax laws, and stuff related to crypto mining before i built this data miner.  i'm currently waiting for answers to my questions about whether crypto o.s.'s are actual o.s.'s or if they are a program that needs an o.s. to run.  i'm just misunderstanding the reading on the minerstat and rave os sites i'm sure.

---

### Post by TheFu on 2024-08-29
So, you are running 22.04 with Gnome and using Wayland with both AMD and nVidia GPUs.
As I don't use the Gnome DE, I cannot help. Sorry.

I know nothing about cryptomining anymore.  It became unprofitable for the "small guys" where I live around 2012 thanks to the cost of electricity.  Laws and taxes are different everywhere, so nobody who doesn't live in the same jurisdiction can comment on that.  Around here, only people with $25K+ computers with lots of 4080 or better per chassis nVidia GPUs are making money.

---

