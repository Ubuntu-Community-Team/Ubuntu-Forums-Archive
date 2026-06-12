---
title: "Laptop &quot;Hiccups&quot;  when disconnected from power."
date: 2011-10-24
forum: New to Ubuntu
---

### Post by Gaddy on 2011-10-24
I've recently installed ubuntu. I enabled the Nvidia additional drivers to use the advanced visual effects.
They run great on my Dell XPS, as long as the laptop is plugged in to a power source.
When I disconnect the charging cable, the screen freezes every 10 seconds or so, for about 3-6 seconds. The mouse stops moving or moves very slowly. Keyboard input stops. 
I'm new, and I don't even know where to start diagnosing the source of my problem.
Reading other forums I've tried:
1. Instaling drivers directly from Nvidia.
2. Setting the display at 1920x 1080 and 60 HZ, as opposed to Auto.

Having said that, doing 2 works sometimes. But not all of the time. 

Help?!

What do i begin with?

---

### Post by LinuxFan999 on 2011-10-24
A good idea would be to disable the visual effects before unplugging the laptop.

---

### Post by Gaddy on 2011-10-29
I tried that. It sort of helps in that it doesn't freeze anymore. But the screen does flicker just as often. 
I noticed that as soon as the screen flickers, in the Nvidia X Server Settings the resolution changes from 1920x1080 , 60hz to 1920x1080 , Auto. 
I've tried setting it to 60hz manually. But the setting doesn't stick. It comes right back after some time.
The wierd thing is. Sometimes, it does stick. But it certainly gets messed up in the next reboot.

---

### Post by sadaruwan12 on 2011-10-29
It's seems like your laptop recalibrate it self to suite the power source one of my coworkers has a laptop similar to your spec but it's a HP configurations seems to be the same.

To get more life out of the battery it recalibrate everything from display effects to the CPU load handling including the secondary GPU in the laptop this is a feature I think that comes with i7 laptops to get more life out of the battery.

In his lap he users Win7 with dual monitors which actually flickers and do some silly stuff when removed from AC current input. But when we give the AC power back it just rotates back to what it was.

This might be the issue with yours when it tries to recalibrate it just get confused and does those things you've described.

I think the settings are in the BIOS for that 'cos I didn't see any software setting in the laptop my friend has.

hope this help you.

---

### Post by Gaddy on 2011-11-04
> **sadaruwan12 said:**
> It's seems like your laptop recalibrate it self to suite the power source one of my coworkers has a laptop similar to your spec but it's a HP configurations seems to be the same.

To get more life out of the battery it recalibrate everything from display effects to the CPU load handling including the secondary GPU in the laptop this is a feature I think that comes with i7 laptops to get more life out of the battery.

In his lap he users Win7 with dual monitors which actually flickers and do some silly stuff when removed from AC current input. But when we give the AC power back it just rotates back to what it was.

This might be the issue with yours when it tries to recalibrate it just get confused and does those things you've described.

I think the settings are in the BIOS for that 'cos I didn't see any software setting in the laptop my friend has.

hope this help you.

Thanks for pointing it out. 
The thing is, this doesn't happen in windows 7. Aero relies on the graphics card too, much like the unity interface in Ubuntu. So it's not a Bios thing. 
Once I've fixed my resolution to 1920x1080, 60 hz using the nvidia x server settings, and I've saved the configuration to the X configuration file (by clicking that button) it sort of works for the remainder of the time, till the next reboot. 
On the next reboot the 60 Hz changes back to auto. and I have to go back through this cycle again. 
Why doesn't it just stick!
Is there a way that I can manually set this? 

And has anyone noticed if using the Gnome 3 interface keeps the gpu loaded a little more than expected.
My GPU temperature shoots to 78 degrees.
I'm now back to using Unity prefer Gnome

Please help.
I think it's got something to do with the NVIDIA settings.

---

### Post by Gaddy on 2011-11-04
> **Gaddy said:**
> Thanks for pointing it out. 
The thing is, this doesn't happen in windows 7. Aero relies on the graphics card too, much like the unity interface in Ubuntu. So it's not a Bios thing. 
Once I've fixed my resolution to 1920x1080, 60 hz using the nvidia x server settings, and I've saved the configuration to the X configuration file (by clicking that button) it sort of works for the remainder of the time, till the next reboot. 
On the next reboot the 60 Hz changes back to auto. and I have to go back through this cycle again. 
Why doesn't it just stick!
Is there a way that I can manually set this? 

And has anyone noticed if using the Gnome 3 interface keeps the gpu loaded a little more than expected.
My GPU temperature shoots to 78 degrees.
I'm now back to using Unity prefer Gnome

Please help.
I think it's got something to do with the NVIDIA settings.

This is the last few lines of my xorg log
[  1717.782] (WW) SynPS/2 Synaptics TouchPad: Ignoring new tracking ID for existing touch.
[  1776.176] (II) NVIDIA(0): Setting mode "1920x1080_60+0+0"
[  1806.162] (II) NVIDIA(0): Setting mode "1920x1080_60_0"
[  1855.142] (II) NVIDIA(0): Setting mode "1920x1080_60+0+0"
[  1870.549] (WW) NVIDIA(0): WAIT (2, 6, 0x8000, 0x00009c68, 0x000034f0)
[  1871.680] (WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x000034f0, 0x000034f0)
[  1871.881] (II) NVIDIA(0): Setting mode "1920x1080_60_0"
[  1880.651] (II) NVIDIA(0): Setting mode "1920x1080_60+0+0"
[  2166.228] (II) NVIDIA(0): Setting mode "1920x1080_60_0"
[  2234.252] (II) NVIDIA(0): Setting mode "1920x1080_60+0+0"
[  2252.352] (WW) SynPS/2 Synaptics TouchPad: Ignoring new tracking ID for existing touch.
[  2256.153] (II) NVIDIA(0): Setting mode "1920x1080_60_0"

---

