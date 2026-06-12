---
title: "No sound after installation"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by cjnc201 on 2008-06-06
Hey all, 

New ubuntu user here in a way... I installed ubuntu on a new harddrive and now my sound is not working.. when i had ubuntu on my old harddrive the sound worked automatically... not sure what to do here.

if anyone can help me out it would be great.. not sure all the twists and turns of this OS so if you can be a little bit detailed with steps it would help me a lot.

thanks much,

cjnc201

---

### Post by finito on 2008-06-06
try lspci in terminal to see what sound card you have. post the contects of lspci

---

### Post by cjnc201 on 2008-06-06
thanks for the reply, here is what came up

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:08.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)

---

### Post by finito on 2008-06-06
try asoundconf list in terminal
 post what it says.
if it list a sound car (Audigy somthing)
then goto system -> Pref-> Sound 
and click test if nothing comes up most likey ALsa is broken

---

### Post by cjnc201 on 2008-06-06
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio


whats alsa??

---

### Post by cjnc201 on 2008-06-06
any ideas anyone? having no sound sucks lol

---

### Post by cjnc201 on 2008-06-06
actually i just solved my sound problem.. i went into control panel and selected my sound card lol

thanks anyway 

btw, anyone know of a good dvd player??

---

### Post by cariboo on 2008-06-06
Just to avoid future problems, you may want to disable your builtin sound card in the bios.

Jim

---

### Post by cjnc201 on 2008-06-06
ok cool, will do

anyone ever have a problem where sound works in some programs and doesnt in others? I just tried playing a cd and there is no sound in rhythmbox.

---

### Post by cjnc201 on 2008-06-09
> **cjnc201 said:**
> 

anyone ever have a problem where sound works in some programs and doesnt in others? I just tried playing a cd and there is no sound in rhythmbox.

bump

---

