---
title: "Temperature"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by neverett on 2008-09-24
I'm trying to gather other opinions on the following temperatures.

CPU: 37*C
System: 128*C
HDD: 38*C

Are these within normal range?  Colder than normal?  Hotter than normal?  Just wondering!  Any input is appreciated.

---

### Post by bobnutfield on 2008-09-24
CPU and HDD appear in normal range, but 128 degrees for System seems extremely hot.  Laptops will return much hotter temps than desktops, but that might be an incorrect reading.

---

### Post by tangibleorange on 2008-09-24
> **neverett said:**
> I'm trying to gather other opinions on the following temperatures.

CPU: 37*C
System: 128*C
HDD: 38*C

Are these within normal range?  Colder than normal?  Hotter than normal?  Just wondering!  Any input is appreciated.

yeah my system (laptop) temp never goes above 70C without the fans kicking in big time...

---

### Post by kpatz on 2008-09-24
That has to be an incorrect reading.  First of all, 128C would cook the system, and second, there's no way the CPU and HD could retain sub-40 temps with everything around it above the boiling point of water. :)

What tool did you use to get those readings?  Maybe it isn't totally compatible with your laptop.

The CPU and HDD temps look good, assuming those are accurate.  CPUs usually run hotter than that.

---

### Post by neverett on 2008-09-24
I'm using the sensors applet on the toolbar.  Downloaded it through synaptic.

```
sudo apt-get install sensors-applet
```

Right click on the menu bar (task bar if you will) at the top click add to panel and it should be in that list.

I just turned my system on right now (it's a desktop) and I have:

CPU: 37*C
System: 128*C
HDD: 31*C
GPU: 46*C

I agree something must be wrong with the system temp.  Also, what is the normal range for the above listed temps?  Thanks for your input guys!

---

### Post by bobnutfield on 2008-09-24
This is just a front-end for lm-sensors.  Open a terminal and just type:

> sensors

and see if they give you the same readings. There is a HOWTO for lm-sensors here:

> [http://wiki.linuxquestions.org/wiki/Lm-sensors](http://wiki.linuxquestions.org/wiki/Lm-sensors) 

You sometimes have to edit a config file to get proper readings.  It's been a long time since I have done it, but the readings you are gettings I am betting are way off.

---

### Post by SuperSonic4 on 2008-09-24
Mid 40s to mid 50s is about average, anything stable above 70 is too hot and you shut down the pc at 75 to protect it. My BIOS automatically shuts down the PC if it reaches 85C or if the system reaches 75C (I think)

---

### Post by neverett on 2008-09-24
```
#sensors
f71882fg-isa-0600
Adapter: ISA adapter
3.3V:        +3.28 V
Vcore:       +1.24 V  (max =  +2.04 V)   
Vdimm:       +2.21 V
Vchip:       +1.76 V
+5V:         +5.12 V
12V:        +11.39 V
5VSB:        +3.78 V
3VSB:        +3.28 V
Battery:     +3.17 V
CPU:        2377 RPM
System:     1224 RPM
Power:         0 RPM  ALARM
Aux:           0 RPM  ALARM
CPU:         +38.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
System:        FAULT  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor


```

That is what I get when run sensors.  I've noticed that the ambient GPU temp is 39*C.  So, that is closer to the system temp.

Current temps:

CPU: 37*C
System: 128*C -- still can't figure out how to fix that one
HDD: 35*C
GPU: 48*C
GPU Ambient: 39*C

Thanks guys.  Any help on the system temp would be greatly appreciated.

---

### Post by kpatz on 2008-09-24
I just tried sensors on my Myth box and it shows some odd temperatures on some sensors (such as 121C on an AUX sensor).  This probably means the sensor doesn't actually exist, but the driver doesn't know that, it just reads all the sensor ports on the chip.  120+C temps are probably an open or short circuit on the sensor input, for sensors that don't actually exist in your system.

You should be able to comment out that sensor in your /etc/sensors3.conf file.  Look for entries labeled "System" and comment them out.

---

