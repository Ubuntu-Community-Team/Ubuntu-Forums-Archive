---
title: "Live CD Hangs on Boot"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by jonathan.david.lim on 2008-07-23
I finally decided to get rid of Windows XP Pro on my PC and replace it with Ubuntu 8.04. I've used Ubuntu before (in fact, I'm using it right now on my laptop), but this is the first time the CD hasn't worked.

I've set my PC to boot from the CD, and when it does it takes me to the language setting and then the menu which asks if I want to 'Try Ubuntu', 'Install', etc. I go ahead and try it and then it starts to load and then nothing. I tried switching to safe graphics mode, and still nothing happens.

I'm using the same CD I used to install Ubuntu on my laptop, so I don't understand what gives. Should I just install it and hope nothing bad happens, or should I install alongside Windows and try it without the CD? I'm not at all sure what to do, and am still really, really new at Linux commands and all that jazz.

Any help?

---

### Post by overdrank on 2008-07-23
> **jonathan.david.lim said:**
> I finally decided to get rid of Windows XP Pro on my PC and replace it with Ubuntu 8.04. I've used Ubuntu before (in fact, I'm using it right now on my laptop), but this is the first time the CD hasn't worked.

I've set my PC to boot from the CD, and when it does it takes me to the language setting and then the menu which asks if I want to 'Try Ubuntu', 'Install', etc. I go ahead and try it and then it starts to load and then nothing. I tried switching to safe graphics mode, and still nothing happens.

I'm using the same CD I used to install Ubuntu on my laptop, so I don't understand what gives. Should I just install it and hope nothing bad happens, or should I install alongside Windows and try it without the CD? I'm not at all sure what to do, and am still really, really new at Linux commands and all that jazz.

Any help?

Hi and welcome, could you give us some system specs? Just in case have you checked the cd for errors?

---

### Post by jonathan.david.lim on 2008-07-24
I did run a CD check and it said it was fine.

My specs:

Windows: Windows XP5.1 (Build 2600) Service Pack 2
Internet Explorer: 7.0.5730.11
Memory (RAM): 1279 MB
CPU Info: Intel(R) Pentium(R) 4 CPU 2.20GHz
CPU Speed: 2184.9 MHz
Sound card: SoundMAX Digital Audio
Display Adapters: NVIDIA GeForce FX 5500 | NetMeeting driver | RDPDD Chained DD
Screen Resolution: 1440 X 900 - 32 bit
Network: Network Present
Network Adapters: NETGEAR RangeMax(TM) Wireless USB 2.0 Adapter WPN111 - Packet Scheduler Miniport
CD / DVD Drives: D: ATAPI   DVD DC 16X8X5    | E: SAMSUNG CD-R/RW SW-248F  | F: XG3775C TGH407F
COM Ports: COM1
LPT Ports: LPT1
Hard Disks: C:  55.8GB | H:  232.8GB
Hard Disks - Free: C:  32.5GB | H:  30.9GB
Manufacturer: Mitac International
Product Make: Dimension 2350
AC Power Status: OnLine
BIOS Info: AT/AT COMPATIBLE | 03/24/03 | IntelR - 42302e31
Motherboard: Dell Computer Corporation 07W080

The thing is old, old, old. I just want to run an operating system on it that won't give me anymore hastle.

---

### Post by ET! on 2008-07-25
ubuntu will run pretty fine....could you check your drive for errors??

---

### Post by gimlithedwarf on 2008-07-25
if you used the 64 bit ubuntu cd for your laptop it may not work with your desktop as the desktop may have a 32 bit processor

---

### Post by Efros on 2008-07-25
Generally whenever I've had issues with the live CD I use the equivalent alternate CD and usually that is enough to get going.

---

### Post by jonathan.david.lim on 2008-07-25
Now that I think of it, I don't really need my PC at all. I use my laptop far more, especially now since I've tried it with my printer and that works great, as well as taking it over to a friend's house and connecting to his wireless network. I'll just keep the PC as a Windows machine for gaming and suchlike for whenever I'm bored, I suppose, but I'll keep the laptop for absolutely everything else. It just seems a bit more trouble than it's worth to start an Ubuntu installation and possibly have it screw up.

---

### Post by dstew on 2008-07-25
It is possible that the display driver for the installation disk is not working properly with your hardware. Try using the kernel parameters **vesa=force** or **vga=791**. You enter these on the kernel line, which you can get to by pressing F6 at the opening menu.

---

