---
title: "one third of the screen unavailable"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by al.adab on 2012-04-27
hello

I've just installed Xubuntu 12.04. All went well until I ran an update. All of a sudden, one third of the screen became "unavailable": the bottom one-third of the screen, in other words, is "covered" (sorry I don't know how to explain this) in a white stripe. Occasionally, the colour of the stripe changes slightly. 

I took a screenshot...and the screenshot doesn't show the stripe (?) I'm wondering if it's the computer that needs to be replaced - motherboard issues, etc, or if it might have something to do with some software error, etc? 

I'm attaching the screenshot, just in case. Thank you.

---

### Post by Toz on 2012-04-27
Sounds like it might be an issue with the video card. What card do you have and which driver are you using? Open a terminal window and type in this command to get you some more info:
```
sudo lspci -vnn | grep -A10 VGA
```

If you have the LiveCD, it might be worth booting with it to see if the problem persists.

---

### Post by al.adab on 2012-04-27
thanks Toz I'll do that as soon as I get back home tonight GMT 2300 - I tried the LiveCd this morning, incidentally, and the problem persists.

---

### Post by Toz on 2012-04-27
If the problem persists, it may be an issue with your video card or monitor.

---

### Post by al.adab on 2012-04-27
here it is: 

~$ sudo lspci -vnn | grep -A10 VGA
[sudo] password for imageraw: 
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV200 [Mobility Radeon 7500] [1002:4c57] (prog-if 00 [VGA controller])
	Subsystem: IBM ThinkPad T42 2373-4WU [1014:0530]
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
	Capabilities: [50] Power Management version 2
	Kernel modules: radeon, radeonfb

---

### Post by Toz on 2012-04-28
Looks like you've got the right video driver for the card that you have. However, I think that if you're experiencing the same problem with the LiveCd, then there may be a problem with the onboard video chip or the LCD screen itself.

---

### Post by Paqman on 2012-04-28
Always pays to start with the simple stuff: check the cable from your graphics card to monitor is pushed home and check the graphics card itself is properly seated.

---

### Post by al.adab on 2012-04-29
thanx both it looks like the card is properly connected - upgrading to "new" T42 at this stage, don't really have the means to investigate this further, sorry.

---

