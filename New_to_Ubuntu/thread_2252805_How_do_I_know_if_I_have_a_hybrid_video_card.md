---
title: "How do I know if I have a hybrid video card?"
date: 2014-11-14
forum: New to Ubuntu
---

### Post by rolin on 2014-11-14
hello to everyone
For a long time I have a question that I could not solve it
I have a hybrid video card ?? ... if so, how to install video driver

my laptop

@root:~$ inxi -zv7
System:    Host: root Kernel: 3.13.0-37-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: LXDE (Openbox 3.5.2) info: lxpanel dm: lightdm Distro: Ubuntu 14.04 trusty
Machine:   System: Sony (portable) product: VPCEB1S1E version: C603SN0R Chassis: type: 10
           Mobo: Sony model: VAIO Bios: American Megatrends version: R0300Y8 date: 07/20/2010
CPU:       Dual core Intel Core i5 CPU M 430 (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9044.28 
           Clock Speeds: 1: 1199.00 MHz 2: 1199.00 MHz 3: 1199.00 MHz 4: 1199.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] bus-ID: 01:00.0 chip-ID: 1002:68c1 
           X.Org: 1.15.1 driver: fglrx Resolution: 1360x768@59.9hz, 1360x768@60.0hz 
           GLX Renderer: AMD Mobility Radeon HD 5000 Series GLX Version: 4.4.13084 - CPC 14.301.1001 Direct Rendering: Yes
Audio:     Card-1: Intel 5 Series/3400 Series High Definition Audio driver: snd_hda_intel bus-ID: 00:1b.0 chip-ID: 8086:3b56

---

### Post by oldrocker99 on 2014-11-14
Your i5 has graphics circuitry built-in, and your AMD card does too. You're almost certainly using the AMD chip currently, and would probably best be advised to keep your system the way it is. You might be able to go into BIOS and select the i5's graphics in favor of the AMD's, and you might like the results better.

It's worth a try if you're curious. If you're happy with your deck the way it is, if it ain't broke...

---

### Post by mastablasta on 2014-11-15
depends how you installed the AMD driver and if they support your build iof hybrid GPU. you shoul dbe able to see that in AMD Catalyst center.

---

