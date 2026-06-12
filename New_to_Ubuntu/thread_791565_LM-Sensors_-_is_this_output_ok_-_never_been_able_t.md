---
title: "LM-Sensors - is this output ok - never been able to do this stuff on old pc."
date: 2008-05-12
forum: New to Ubuntu
---

### Post by philinux on 2008-05-12
New to this stuff. Nice being able to check, but no able to understand. :lolflag:
```

sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +21.0°C                                    
Core0 Temp:  +18.0°C                                    
Core1 Temp:  +24.0°C                                    
Core1 Temp:  +16.0°C                                    

it8712-isa-0290
Adapter: ISA adapter
VCore 1:     +1.14 V  (min =  +0.00 V, max =  +4.08 V)
VCore 2:     +4.08 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +3.31 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +5.99 V  (min =  +0.00 V, max =  +6.85 V)
+12V:       +12.54 V  (min =  +0.00 V, max = +16.32 V)
-12V:       -15.21 V  (min = -27.36 V, max =  +3.93 V)
-5V:         +4.03 V  (min = -13.64 V, max =  +4.03 V)
Stdby:       +6.85 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +3.33 V
fan1:       2973 RPM  (min =    0 RPM, div = 2)
fan2:          0 RPM  (min =    0 RPM, div = 2)
fan3:          0 RPM  (min =    0 RPM, div = 2)
M/B Temp:    +33.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
CPU Temp:    +35.0°C  (low  =  -1.0°C, high = -17.0°C)  sensor = transistor
Temp3:      +128.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
cpu0_vid:   +1.550 V

```

---

### Post by drs305 on 2008-05-12
Yes, it looks pretty normal.

---

### Post by philinux on 2008-05-12
That's good to know pc about 2 weeks old.

---

### Post by tgalati4 on 2008-05-12
It looks like you have two temperature sensors on each CPU core, one probably on top and one on the bottom, that would account for the differences.  You can do a google search on your CPU and find out exactly where those sensors are located.

The IT8712 is a chip that keeps track of critical data on the motherboard.  The CPU temperature could be a sensor under the CPU socket.  Again, a google search on your specific motherboard may reveal its location.

You can edit /etc/sensors.conf and set high and low limits for each value.  When you run a thermometer applet, it will indicate an alarm condition for out-of-range values.

---

