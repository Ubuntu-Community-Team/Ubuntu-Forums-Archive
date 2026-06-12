---
title: "ThinkPad x60s gets VERY hot"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Sydius on 2008-07-30
My Lenovo ThinkPad X60s gets very hot on the bottom, near the center and to the lower-right (but moreso in the center, under the keyboard).  So hot, in fact, that touching it actually hurts and leaves a tingling sensation in my finger even after removing it.  I don't know the actual temperature, but I assume that hot enough to hurt me is hot enough to hurt the computer.

It doesn't get anywhere near that temperature when in Windows XP.

Oh, and this was after browsing the web for about 20 minutes.

What should my next steps to diagnose the problem be?

---

### Post by Tom--d on 2008-07-30
When its hot.
post the outcome of
```
acpi -t
```

---

### Post by Sydius on 2008-07-30
```
chris@chris-work-laptop:~$ acpi -t
     Battery 1: charging, 81%, 00:31:08 until charged
     Thermal 1: ok, 46.0 degrees C
     Thermal 2: ok, 47.0 degrees C
```

Now I'm thinking it is more in the lower-right than in the center... but I can't be sure.

---

### Post by Tom--d on 2008-07-30
Right,
I think that is your CPU's temp.
That is good. :)

I think it might be your gpu. 
Mine does it. my gpu gets hot. but I have no sensor for it :( so i dont know what it is.

---

### Post by Sydius on 2008-07-30
I don't know what's customarily in the lower-right corner of laptops, but could it be the hard drive?

Is there an easy way to read the hard drive's temperature?

---

### Post by rossjman1 on 2008-07-30
It's a problem with Thinkpads. I have a T60 and the GPU can get up to 100 degrees C. Everything else is normal temp. Just don't worry about it. The GPU is made to withstand heat up to 110 (then the computer will shutdown).

---

### Post by Sydius on 2008-07-30
> **rossjman1 said:**
> It's a problem with Thinkpads. I have a T60 and the GPU can get up to 100 degrees C. Everything else is normal temp. Just don't worry about it. The GPU is made to withstand heat up to 110 (then the computer will shutdown).

Are you sure it's okay? It's a work laptop, and I really don't want to wreck it. :-?

---

### Post by Tom--d on 2008-07-30
What graphics card is it?

also you can get the hdd temp.
```
sudo apt-get install hddtemp
```

if I remember rightly. 
its 
```
sudo hddtemp /dev/sda
```
where sda is your hdd (change it to what yours is)

---

### Post by Sydius on 2008-07-30
> **Tom--d said:**
> What graphics card is it?

How do I tell?

---

### Post by Tom--d on 2008-07-30
post the outcome of:
```
lspci
```

---

### Post by rossjman1 on 2008-07-30
Mine is ATI Mobility Radeon X1400 (im not the OP). There is more info in this already existing thread: [http://ubuntuforums.org/showthread.php?t=869106](http://ubuntuforums.org/showthread.php?t=869106)

---

### Post by Sydius on 2008-07-30
Hard drive seems ok:

```
chris@chris-work-laptop:~$ sudo hddtemp /dev/sda
/dev/sda: HITACHI HTS541680J9SA00: 38°C
```

And here's the stats (doesn't seem to be a Radeon):

```
chris@chris-work-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
chris@chris-work-laptop:~$ 
```

---

### Post by Gun_Smoke on 2008-07-30
you can install lm-sensors

```
sudo apt-get install lm-sensors
```

```
sudo sensors-detect
```

hit y to everything

then install sensors-appelet

```
sudo apt-get install sensors-applet
```

Then right click a panel and add the sensor to a panel.

I you don't want the appelet you can see the temps with 

```
sudo sensors
```

---

### Post by Tom--d on 2008-08-01
Right, 
I think I have an idea what it is.

Its not your GPU.

It might be the touchpad.
Mine gets very hot for no reason. Its next to the HDD but thats quite low (30 -40C) hddtemp says.

I turned off my touchpad in the BIOS and it still gets very warm. 
I might open it up and see what It really is.

---

### Post by Sydius on 2008-08-01
> **Tom--d said:**
> I might open it up and see what It really is.

Let me know how it goes.  I wouldn't be able to figure it out even if I did open it up--laptop parts are more or less indistinguishable for me, beyond the basics like CPU or RAM.

A shot-in-the-dark idea: hard drive controller? I read Linux handles the hard drives in laptops in a way they aren't designed for (something about the head trying to rest too often), but maybe this has some impact on the controller too?  Just a random idea from a newbie.

---

### Post by Tom--d on 2008-08-01
> **Sydius said:**
> Let me know how it goes.  I wouldn't be able to figure it out even if I did open it up--laptop parts are more or less indistinguishable for me, beyond the basics like CPU or RAM.

A shot-in-the-dark idea: hard drive controller? I read Linux handles the hard drives in laptops in a way they aren't designed for (something about the head trying to rest too often), but maybe this has some impact on the controller too?  Just a random idea from a newbie.

Wait. 
That might be it!
The HDD controller.
I was wondering as I took my laptop apart. And there was a black chip under my touchpad with Intel on it. (quite big but not the gpu) and my hdd is right next to it.

I think that might be it!
I'll look around now for that :D

---

### Post by Lord Xeb on 2008-08-04
The way the ThinkPad series is designed, the GPU sits under the mouse pad area. The X1400 is known to get hot (like 160 plus F). Just make sure you keep it it well ventilated and watch the temp with lmsensors and you will be just fine. At least it isn't a 9800GX2 (which can get upto 105C). The graphics cards that use 90nm tech get hot. They are like the pentium 4s.

---

### Post by deco on 2008-08-20
after watching this video:

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-64322](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-64322)

im pretty sure it's the wireless card, the place where it gets hot is exactly where the wireless card is located (right next to the HD)

well LAN og WLAN card..

edit: on the other hand, i noticed that it gets hot when the screensaver starts which prolly stresses the GPU, turning that off and heat was low after.

so final conclusion must be: it's the GPU which has to be located around same area as the network cards :)

-Deco

---

### Post by merike on 2008-08-23
I do have intel graphics card, so it's a bit different situation here.

But what I've noticed that with some recent (couple of weeks) updates my laptop has become cooler. The warmest spot PCI used to be around 54-55, but now it's 51. Fan speed seems to be the same as before.

Anyone knows which updates might have influenced this? Because unfortunately it has rendered hibernate somewhat buggy for me: [https://bugs.launchpad.net/ubuntu/+bug/259496]("https://bugs.launchpad.net/ubuntu/+bug/259496")

---

### Post by wol4nd on 2009-04-10
Hi!

I got the same laptop -- more or less. Mine gets hot when I play intensive 3D games. Therefore I concluded it must be the graphic card. Which I don't like because I goes till a blue screen sometimes depending on how hot it gets (btw I got Vista). Now I'm looking for a solution to cool it down while in 3D.

If your xwindow manager is graphically accelerated then that might be the reason.

GL,
Lucian

---

### Post by merike on 2009-04-11
I found the following helpful for cooling down wireless card
```
echo 5 | sudo tee /sys/bus/pci/drivers/iwl3945/*/power_level

```
You can't run it on startup though, only if you're already connected to a network. Has worked really nice with Intrepid for me.

---

### Post by brodedra on 2012-08-08
> **Tom--d said:**
> post the outcome of:
```
lspci
```

Check this [thread]("http://ubuntuforums.org/showthread.php?t=2039148")

lenovo@lenovo-ThinkPad-X60s:~$ thinkfan

WARNING: Using default temperature inputs in /proc/acpi/ibm/thermal.
WARNING: You have not provided any correction values for any sensor, and your fan will only start at 55 °C. This can be dangerous for your hard drive.
Config as read from /etc/thinkfan.conf:
Fan level    Low    High
 0        0    55
 1        48    60
 2        50    61
 3        52    63
 4        56    65
 5        59    66
 7        63    32767
/proc/acpi/ibm/fan: Permission denied
Error opening /proc/acpi/ibm/fan. Is this a computer really Thinkpad? Is the thinkpad_acpi module loaded? Are you running thinkfan with root privileges?

---

### Post by TenPlus1 on 2012-08-09
You could also try installing Jupiter which is a good power manager that sits in your system tray:

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

---

### Post by Elfy on 2012-08-09
Old thread closed.

---

