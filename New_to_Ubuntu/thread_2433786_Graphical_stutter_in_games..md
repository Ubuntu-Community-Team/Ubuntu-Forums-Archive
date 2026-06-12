---
title: "Graphical stutter in games."
date: 2019-12-25
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2019-12-25
```
$ inxi -CGMDMachine:   Device: desktop System: NCSTECH product: CT1-A402 serial: N/A
           Mobo: ASUSTeK model: P8H61-M LE/CSM v: Rev x.0x serial: N/A
           BIOS: American Megatrends v: 4501 date: 05/10/2013
CPU:       Quad core Intel Core i5-3470 (-MCP-) cache: 6144 KB
           clock speeds: max: 3600 MHz 1: 1596 MHz 2: 1595 MHz 3: 1596 MHz
           4: 1596 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: ati,amdgpu (unloaded: modesetting,fbdev,vesa,radeon)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Radeon RX 570 Series (POLARIS10, DRM 3.23.0, 4.15.0-72-generic, LLVM 8.0.0)
           version: 4.5 Mesa 19.0.8
Drives:    HDD Total Size: 4500.9GB (40.3% used)
           ID-1: /dev/sda model: CT250MX500SSD1 size: 250.1GB
           ID-2: /dev/sdb model: ST250DM000 size: 250.1GB
           ID-3: /dev/sdc model: ST2000LM007 size: 2000.4GB
           ID-4: USB /dev/sdd model: Elements_25A2 size: 2000.4GB
```

I'm mainly using this machine for a few lxd containers and playing Minecraft. Xubuntu 18.04 LTS. I am getting light stuttering and can't figure why. Minecraft seems to be the only place stuttering occurs. I can't tell if this is a Linux issue that can be fixed? Or just something I have to live with. The hardware should be more than powerful enough. On windows this machine ran World of Warcraft at 100fps maxed out graphics. Any ideas?

---

### Post by Autodave on 2019-12-25
You may be asking too much of that video card.  Try lowering the resolution down a notch and see how well it works.

---

### Post by CatKiller on 2019-12-25
> **Tadaen_Sylvermane said:**
> I am getting light stuttering and can't figure why. Minecraft seems to be the only place stuttering occurs. I can't tell if this is a Linux issue that can be fixed? 

It's a Minecraft issue that can potentially be fixed. Java is not a great platform for a responsive gaming experience, and there is more information out there than you could possibly need on how game ticks work, and options for garbage collection in Java. You could tweak your Java options around memory allocation, or use Spigot instead of the vanilla Minecraft jar file. Either of those would help with stuttering. OptiFine can also help.

---

