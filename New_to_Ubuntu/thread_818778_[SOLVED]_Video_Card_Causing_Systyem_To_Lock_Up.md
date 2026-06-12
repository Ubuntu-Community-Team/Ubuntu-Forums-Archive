---
title: "[SOLVED] Video Card Causing Systyem To Lock Up?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by pemur1 on 2008-06-04
Here are the specs:

SDRAM: 1.5 GB
Processor: AMD Athlon XP 2600+
Ubuntu Release: 8.04 Hardy
Kernel Linux 2.6.24-18-generic
GNOME 2.22.2

Video Card: ATI Radeon 9200

I really have no clue if that's what the problem. Everything was running fine for a while, then suddenly Firefox crashes constantly and the system locks up almost as much. Any assistance is greatly appreciated.

---

### Post by tj111 on 2008-06-04
Can you describe in a little more detail when you say the system locks up?  Is it just a specific program, does everything freeze but the mouse, does the mouse freeze, does it drop to a terminal or reboot, things like that.

---

### Post by pemur1 on 2008-06-04
> **tj111 said:**
> Can you describe in a little more detail when you say the system locks up?  Is it just a specific program, does everything freeze but the mouse, does the mouse freeze, does it drop to a terminal or reboot, things like that.

Sometimes the whole system freezes. No mouse, no keyboard. Sometimes it freezes and the mouse can be moved, but I'm unable to select anything. Anytime the system locks up, I have to do a manual reboot.

---

### Post by pemur1 on 2008-06-05
No solution, huh?

Since it appears this problem can't be corrected, can anyone recommend a reasonably priced video card that works out of the box and won't cause me to pull my hair out when installing the drivers?

---

### Post by bondo101 on 2008-06-05
Sounds more like a memory problem. Usually when mem goes bad you'll get these problems. Either mem on video card or system mem.
also new card driver under linux . Ebay on video card s the cheapest but buy new in box. Try a basic card if ya have.
         just trying ta help bondo101 out

---

### Post by Paqman on 2008-06-05
I used to use a 9200SE on an Athlon XP processor myself, and never had any problems. The fact that your errors started happening suddenly makes me suspicious of a hardware fault. Did you make any changes to your software prior to it flaking out?

---

### Post by pemur1 on 2008-06-05
> **Paqman said:**
> I used to use a 9200SE on an Athlon XP processor myself, and never had any problems. The fact that your errors started happening suddenly makes me suspicious of a hardware fault. Did you make any changes to your software prior to it flaking out?

Last week a friend gave me an ATI 9250 and a 1GB stick of SDRAM, but I could never get the drivers for the video card installed and took it out. I reinstalled my old 9200 and did a fresh re-install of Hardy. Everything ran fine for about a day, but then the system starting freezing. The only changes I've made are installing Emerald and AWN. I had the desktop effects set to Normal, but turned them off when the freezing started. Apparently, this did'nt stop the problem. I'm hoping that it's just the video card causing these problems.

---

### Post by tj111 on 2008-06-05
Next time it freezes, try this.  
-Hit Ctrl+Alt+F1
-login using your username and password
-input the following command
```

dmesg | tail -n 20 > ~/Desktop/dmesg.txt

```
The you can try to hit Alt+Left(arrow key) twice to attempt to return to your desktop.  If that doesnt work Ctrl+Alt+Backspace should log you out, restart x, and take you to the login screen.  If that still doesn't work just reboot normally.

After that, there should be a new text file on your desktop (dmesg.txt).  Post the contents of it up here so we can take a look at it.

---

### Post by pemur1 on 2008-06-05
> **tj111 said:**
> Next time it freezes, try this.  
-Hit Ctrl+Alt+F1
-login using your username and password
-input the following command
```

dmesg | tail -n 20 > ~/Desktop/dmesg.txt

```
The you can try to hit Alt+Left(arrow key) twice to attempt to return to your desktop.  If that doesnt work Ctrl+Alt+Backspace should log you out, restart x, and take you to the login screen.  If that still doesn't work just reboot normally.

After that, there should be a new text file on your desktop (dmesg.txt).  Post the contents of it up here so we can take a look at it.


Sorry about the delay. Here's the result of the above:

```
[   47.425357] Bluetooth: L2CAP socket layer initialized
[   47.485435] Bluetooth: RFCOMM socket layer initialized
[   47.485739] Bluetooth: RFCOMM TTY layer initialized
[   47.485743] Bluetooth: RFCOMM ver 1.8
[   49.360419] [drm] Initialized drm 1.1.0 20060810
[   49.373560] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   49.373684] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   49.946865] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   49.946887] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   49.946928] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   50.288451] 0000:00:0a.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   50.288465] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   50.329837] [drm] Setting GART location based on new memory map
[   50.329852] [drm] Loading R200 Microcode
[   50.329889] [drm] writeback test succeeded in 1 usecs
[   51.484524] NET: Registered protocol family 17
[   56.432462] NET: Registered protocol family 10
[   56.433012] lo: Disabled Privacy Extensions
[   56.433885] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   67.236595] eth0: no IPv6 routers present
```

---

### Post by pemur1 on 2008-06-06
I guess there's no solution. I'm at my wit's end about this. If it's not my video card, what else could it be? I'd hate to spend money on a new card if that's not the problem.

---

### Post by pemur1 on 2008-06-06
Apparently, I'll have to go it alone. Thanks for the assistance.

Can anyone recommend a video card under $100 that would work? Doing some research, ATI doesn't seem the way to go. I'm looking at either a GeForce 8500 GT or an 8600 GT. Does anyone have either of these and, if so, have you encountered any problems with them?

---

### Post by jtrindle on 2008-06-06
NVIDIA is generally well-supported in Linux.  I have an older GeForce and have no problem.  My particular card doesn't have enough texture memory to support compiz effects with a big desktop, but that's the only glitch.

You can probably tell whether your lockup is memory versus the video card if you set the display to "vesa" and run it for a while with your existing card.

Has the temperature of the room changed?  I know it's been mighty hot here and that has caused some issues with my electronics (not my linux box) that weren't visible two weeks ago.

---

### Post by pemur1 on 2008-06-06
> **jtrindle said:**
> NVIDIA is generally well-supported in Linux.  I have an older GeForce and have no problem.  My particular card doesn't have enough texture memory to support compiz effects with a big desktop, but that's the only glitch.

You can probably tell whether your lockup is memory versus the video card if you set the display to "vesa" and run it for a while with your existing card.

Has the temperature of the room changed?  I know it's been mighty hot here and that has caused some issues with my electronics (not my linux box) that weren't visible two weeks ago.

I'd really enjoy using compiz, but at the moment, whenever I have the visual effects set to normal the system runs extremely slow.

How would I go about setting the display to vesa?

It's been in the 90s the last few days, but we have the ac running. The room temp is at about 78.

---

### Post by tj111 on 2008-06-06
Hmm, I don't see anything (edit: in your dmesg) that would cause a system crash.  Random crashes like you describe are commonly due to a hardware fault.  I'd guess the two most common causes of this are:

a) If your power supply is insufficient, is partially fried due to a power surge, or has bad connectors somewhere on it.  If a main part of your system is underpowered, random crashes are quite common.

b) If your computer is over-heating.  Next time it crashes check to see how hot it is.  If its a desktop, open the side of it and try to gauge the temperature of some components (don't touch them!).  Overheated cpus/gpus/psus are common causes of seemingly random crashes.

My only other recommendation would be to add the system moniter to one of your panels (with at least cpu/ram displayed) and see if your maxing out your CPU/RAM or anything when the system crashes.

---

### Post by ____ on 2009-05-16
I had the same problem but after I turned off emerald it doesn't freeze anymore. I would like to get it to work again but can not find a way to fix it.

---

