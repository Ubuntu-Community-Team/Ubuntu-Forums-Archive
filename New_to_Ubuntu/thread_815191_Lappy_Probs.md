---
title: "Lappy Probs"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by londonlad on 2008-06-01
hi all,

i had a mate who tried to install 7.10 on a GATEWAY 3108b lappy, he had no joy.........will 8.04 be any diff?

---

### Post by bobnutfield on 2008-06-01
Not nearly enough information.  Why would it not install 7.10?  What were the error messages?  What's the hardware?

Post some of that and you may get some helpful ideas.

Bob

---

### Post by londonlad on 2008-06-02
there were no error msgs, 7.10 would always get so far then freeze........yes we did try more than once! now, we tried to install 8.04, that installed ok, but now the wireless doesnt work! :(

GATEWAY 3108B LAPPY, 1.3GHZ AMD MOBILE SEMPRON CPU, NVIDEA GEFORCE GO 6100 GFX..........

---

### Post by kwacka on 2008-06-02
if you open terminal (Applications --> Accessories --> terminal) and type: ```
lspci
```
you will be given a list of the hardware, one of which will be the wireless card (e.g. Broadcom). 

It might be that the card's drivers are provided by the manufacturer, or it might be that they can't be bothered to make them available to all their customers and you'll have to use something like 'ndiswrapper'.

Search Ubuntu Forums for the steps to get your card working.

---

### Post by londonlad on 2008-06-02
this is what i got:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
ubuntu@ubuntu:~$

---

### Post by matucker on 2008-06-02
hola - i've been fiddling with a Gateway P-6822 laptop...using the update manager, i installed 8.04 (from 7.10)...seems to work well...however:

o   it doesn't recognize the built-in audio device...
o   the screen layout is funky...the task bar & status bar at top/bottom only extends horizontally 2/3 of the way across the screen & the the bottom status bar is only about 3/4 of the way down the screen...the desktop background & all other applications show fine across the full screen...

any ideas on where to start diagnosing these problems - especially the audio config?  thanks...

---

