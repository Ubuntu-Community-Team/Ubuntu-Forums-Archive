---
title: "Ubuntu freeze"
date: 2018-02-15
forum: New to Ubuntu
---

### Post by rich879 on 2018-02-15
Hi all.
My computer has started to freeze up. I first noticed a couple of days ago when using Blender. I saw the same when later running some games. It happened most recently when I was running only firefox (youtube), a terminal window and a calculator program.
I don't think it's GPU because Blender doesn't support my model.

Basically, display freezes up, lose mouse control. Sometimes the sound will stutter (When this happens, I have to reset the computer) but other times, the screen flickers and I get normal service back.

I'm running Ubuntu 17.10
AMD® Fx(tm)-4170 quad-core processor × 4 
It's happened on Wayland, Xorg and Unity.

I'm running memtester right now.
Can anyone help me track down this problem?

---

### Post by cruzer001 on 2018-02-15
Also try reverting back to previous kernel at boot (grub menu>advance options).

And please post your full system specs.

```
inxi -b
```

---

### Post by rich879 on 2018-02-15
Thanks for the response...
I'll try to revert tomorrow.
Here's the output from inxi -b:```

System:    Host: numbercrunch Kernel: 4.13.0-32-generic x86_64 bits: 64
           Desktop: Gnome 3.26.2 Distro: Ubuntu 17.10
Machine:   Device: desktop Mobo: ASUSTeK model: M5A87 v: Rev X.0x serial: N/A
           BIOS: American Megatrends v: 1506 date: 05/01/2013
CPU:       Quad core AMD FX-4170 (-MCP-) speed/max: 1400/4200 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Cayman PRO [Radeon HD 6950]
           Display Server: x11 (X.Org 1.19.5 )
           drivers: ati,vesa (unloaded: modesetting,fbdev,radeon)
           Resolution: 1360x768@59.93hz
           OpenGL: renderer: AMD CAYMAN (DRM 2.50.0 / 4.13.0-32-generic, LLVM 5.0.0)
           version: 4.1 Mesa 17.2.8
Network:   Card-1: Ralink RT5592 PCIe Wireless Network Adapter
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 560.1GB (6.0% used)
Info:      Processes: 229 Uptime: 6:30 Memory: 2235.5/11992.6MB
           Client: Shell (bash) inxi: 2.3.37
```

---

### Post by cruzer001 on 2018-02-16
Your running the "vesa" graphic driver, but your chip set (cayman) is supported by the open source "radeon" driver. I'm not an AMD expert, but radeon looks like the better choice to me.  Plus it should of been the default driver.

So to switch back to it, run this command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and reboot

Then run
```
inxi -G
```
and it should now have radeon in the print out.

Reference:
```
man radeon
```

ps
Use xorg instead of wayland

---

### Post by rich879 on 2018-02-16
Right, so I reverted to the previous kernel and that *seems* to have stabilized things. Many thanks!

I'm running Xorg.

Bit confused about the radeon driver. I tried that excellent command "mun radeon" and tried "mun  vesa" (this is all new to me) and I see now, the difference between those drivers.

This is the line that shows you which drivers I'm using, "drivers: ati,vesa (unloaded: modesetting,fbdev,radeon)" which looks like I'm using "ati,vesa" and "radeon" is unloaded.
So I used "sudo dpkg-reconfigure -phigh xserver-xorg". 
There was a brief pause, then the command went through. I restarted my computer. After startup, I typed in "inxi -G" and I still had this line : 

"drivers: ati,vesa (unloaded: modesetting,fbdev,radeon)". 

I looked online and found another command: 

"lspci -k | grep -EA2 'VGA|3D'" which gave this output: 

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cayman PRO [Radeon HD 6950]
    Subsystem: PC Partner Limited / Sapphire Technology Cayman PRO [Radeon HD 6950]
    "Kernel driver in use: radeon"

why does it say, "Kernal driver in use: radeon"?

---

### Post by cruzer001 on 2018-02-16
Interesting, two different answers.

We call them drivers, but they are kernel modules.  So what module is loaded in the kernel is the one your running.  The command to list all kernel modules:
```
lsmod
```

Just for your own info "3D" in that command you used is a Nvidia reference, AMD can also be listed as "Display". So to cover everything next time you have a use for it:
```
lspci -k | grep -EA3 'VGA|3D|Display'
```

I have read that dpkg-reconfigure is in a degraded condition.  I guess its no longer a dependable command.

And last
Dropping back to the previous kernel seems to have worked for you, this is good, but its a temporary fix.  I say use it for now and wait for the next kernel upgrade.

---

### Post by rich879 on 2018-02-17
Right, ok.
I decided not to go with the LTS Ubuntu because I figured I'd learn something and that's definitely happening.

Thank you for your help.

---

### Post by cruzer001 on 2018-02-17
Your welcome

So which one is listed in the kernel, radeon or vesa?

---

