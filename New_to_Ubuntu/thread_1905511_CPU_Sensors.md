---
title: "CPU Sensors"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by expatCM on 2012-01-07
I would like to monitor my CPU core temperature but I seem to be missing a step.  The output of the sensors command is below and if I have got this right the CPU core temperature is missing.  To me this looks like the motherboard and the GPU being reported.

What do I need to to show the CPU temperature?


```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +24.0°C  (crit = +127.0°C)

it8718-isa-0e80
Adapter: ISA adapter
in0:          +0.94 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.14 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.31 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +3.01 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +2.98 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +1.60 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +1.20 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +2.90 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.18 V  
fan1:        3245 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +24.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp2:        +34.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +31.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +49.0°C  (high = +100.0°C, crit = +110.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +22.2°C  (high = +70.0°C)

```

---

### Post by Paqman on 2012-01-07
Have you run:
```
sudo sensors-detect
```
?

---

### Post by expatCM on 2012-01-07
yes, it will run.

---

### Post by marin123 on 2012-01-07
So did you get the cpu temp?

You should run
```
sensors
```
to get the temperatures.

---

### Post by expatCM on 2012-01-07
I ran sensors >sensors.txt and then opened the file and copied the information to my first post.  

The CPU temperatures do not appear to be stated there which I find to be strange.  However, the bios does report the CPU temperature so I know the information is available....

---

### Post by marin123 on 2012-01-07
Are you on a laptop?

Did you run all probes? Even the ones where you got a warning that it might not be safe?

Maybe your motherboard manages the CPU temps and it will shut down automatically if temp exceeds critical value (~100 degrees Celsius).

---

### Post by expatCM on 2012-01-07
Not a laptop.  The motherboard is a Biostar A770E3 and the CPU as an AMD Athlon II X2 245.

Yes, you are right, I could set the bios to shutdown at a critical value but if I use a script with a sensor I will get an email to tell me there is a problem so that I know what has just happened.

---

### Post by expatCM on 2012-01-07
Oh and yes, I ran all probes, even the ones not flagged as totally safe.

---

### Post by marin123 on 2012-01-07
The only thing that comes to my mind is running conky and setting it to show temperatures and check what it picks up. (With my laptop, it gets graphics temp, maybe you get lucky and get CPU temps).
Now I'm sorry because I'm out of ideas. Good luck :)

---

### Post by QIII on 2012-01-07
Your CPU temp is given:

```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +22.2°C  (high = +70.0°C)
```k10temp represents the processor temperature on recent AMD CPUs.

I can't tell you why sensors says "PCI", except that perhaps the on-die sensor passes info through a PCI channel somehow.

AMD processors are infamous for giving unreasonably low temperatures.  I'd add 6 - 8 °C to that reading.  Maybe 6, because you aren't using a Phenom II.

I offset my 1100T by 8°C in gkrellm/conky... etc.  I have another machine with a Phenom II x4 that I offset by 6°C.

If you go by 6°C offset, I'd say you are running at 28°C.

If you are using software to shut down your machine at a critical temperature, don't let is get anywhere near the high of 70°C you see there.  You'll smoke that processor starting around 60°C

Temps 1 - 3 may be things like system temp, socket temp, northbridge temp, etc.  You'll have to study the technical documents for your board.

---

### Post by expatCM on 2012-01-07
Thank you all for your comments.

QIII ...  that is very helpful, thank you.  Your comments "You'll have to study the technical documents for your board." suggest an interesting sense of humour as well ....  my board user manual (applies for all my computers)  has nothing at all to do with sensors, indeed only the very basic features of the i/o ports and bios features are presented ...  nothing useful if you want to do things  :)

---

