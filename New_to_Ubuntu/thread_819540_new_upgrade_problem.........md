---
title: "new upgrade problem........"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by chaddiesel on 2008-06-05
I just upgraded to 8.04 and I get the ubuntu status bar at the beginning but then i get this....

> Busy Box v1.1.3 (Debian 1:1.1.3-5ubuntu12)  Built-in shell (ash) Enter 'help' for a list of built-in commands.

(initramfs)

what do i do at this screen?

---

### Post by chaddiesel on 2008-06-05
I can get ubuntu to load if i chose a lower option on grub but then it will only run in low graphics mode.

HELP!!! :(

---

### Post by chaddiesel on 2008-06-05
Please help!

---

### Post by avtolle on 2008-06-05
First, what graphics card do you have? When in Ubuntu, at the terminal type ```
lspci
``` and post the output for review. Thanks.

---

### Post by chaddiesel on 2008-06-08
here is what i got.....

> 00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
04:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)

---

### Post by chaddiesel on 2008-06-08
My graphics card is an Nvidia Gforce 7200. Before I upgraded I was able to configure the graphics card driver and ubuntu was working better than ever. Then after the upgrade all i've gotten is a black screen on .18 and a very low resolution setting on the .14 kernel that is in grub.

---

### Post by chaddiesel on 2008-06-10
what do I do? Can anyone help me? Please!!!

---

