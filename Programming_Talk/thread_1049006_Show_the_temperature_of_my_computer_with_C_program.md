---
title: "Show the temperature of my computer with C program?"
date: 2009-01-24
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-24
I know, there IS a temperature sensor inside my computer, watching the temperature of battery and processor. There must be.

But how can I use it? I want a program which shows the current temperature of my system. Is there a header for this?

---

### Post by jimi_hendrix on 2009-01-24
this is computer dependent i believe...so time to dig up the manuals for your hardware!

---

### Post by slavik on 2009-01-24
there is a tool called sensors. take a look there. be warned though, for different sensor chips, it uses a different configuration and then different motherboard manufacturers might connect things differently to the chip.

there is no "import sensorlib and use some functions" for this one, I am afraid (unless you use sensors code).

the package is lm-sensors :)

---

### Post by jimi_hendrix on 2009-01-24
@OP after you figure this out...can you kindly post the source?

---

### Post by crazyfuturamanoob on 2009-01-24
Hey! With lm-sensors there comes a program which does it everything :D

```

**$ sudo apt-get install lm-sensors**
blahblahblah
**$ sensors**
acpitz-virtual-0
Adapter: Virtual device
temp1:       +46.0°C  (crit = +100.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +38.0°C                                    
Core0 Temp:  +39.0°C                                    
Core1 Temp:  +39.0°C                                    
Core1 Temp:  +35.0°C                                    
**$ **

```

---

### Post by stevescripts on 2009-01-24
> **crazyfuturamanoob said:**
> Hey! With lm-sensors there comes a program which does it everything :D
...
[/code]

Nifty, thanks!
Steve

---

### Post by crazyfuturamanoob on 2009-01-24
And there's even sensors-applet which can be inserted right on desktop toolbar, and displays it graphically! Gee! :D:D:D

Edit: Oh crap, I got 11 temperature sensors, with weird labels, can't know which one is which. 

Which one is battery?
Why there are 4(?) sensors for dual-core CPU?
What is sg0 and sg1?

> temp1
Core0 Temp
Core0 Temp #2
Core1 Temp
Core1 Temp #2
GPUCoreTemp
THRM
/dev/sg0
/dev/sg1
/dev/sda
/dev/sdb

---

### Post by slavik on 2009-01-24
which battery are you looking for? would it be the main battery on a laptop or the CMOS battery? CMOS battery is VBAT, but it won't tell you the charge level of that battery since that is not easy to know (but if voltage on it falls below certain level, you know it's about to run out).

For a laptop's battery, there is a battery charge monitor applet that you can use.

---

### Post by crazyfuturamanoob on 2009-01-25
> **slavik said:**
> 
For a laptop's battery, there is a battery charge monitor applet that you can use.

That applet doesn't tell the temperature.

I want to know the temperature of the large removable battery.

That information is kinda useless but it looks pro. :)

---

### Post by slavik on 2009-01-25
does the battery in question have a thermal diode inside and ways to access it?

---

### Post by crazyfuturamanoob on 2009-01-25
> **slavik said:**
> does the battery in question have a thermal diode inside and ways to access it?

What else might be those 'thermal diodes' used for?

I guess it has because I can see that from BIOS menu, right before booting.

---

### Post by slavik on 2009-01-25
see if the sensors program gives you a temperature for it. if it does, you can probably do it yourself, but you will have to look at the code and also find out the docs for the monitoring chip on your motherboard. (I am not sure what they call these chips)

---

