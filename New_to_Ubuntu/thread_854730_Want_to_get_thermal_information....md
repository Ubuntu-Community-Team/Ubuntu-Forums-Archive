---
title: "Want to get thermal information..."
date: 2008-07-09
forum: New to Ubuntu
---

### Post by chris062689 on 2008-07-09
When I try to run the command "acpi -V" it says:

```

chris@chris-desktop:~$ acpi -V
No support for device type: thermal

```
But in Windows it works, gasp!

What do I need to install?  Drivers?
GIGABYTE GA-EP35-DS3L LGA 775 Intel P35 ATX Intel Motherboard - Retail

---

### Post by tjwoosta on 2008-07-09
i have no idea what that command does but..

have you tried installing lm-sensors ?

```
sudo apt-get install lm-sensors
```

i know i had to istall it in order to make my temp gauge work

also after installing do this

```
sensors-detect
``` then answer everythig yes

---

### Post by Tatty on 2008-07-09
You might also want to install the sensors applet for the menu bar.  Ive got it sitting nicely on my top panel, so I can always see when my laptop is about to burn up.

```
sudo apt-get install sensors-applet
```

---

### Post by tjwoosta on 2008-07-09
> You might also want to install the sensors applet for the menu bar. Ive got it sitting nicely on my top panel, so I can always see when my laptop is about to burn up.


yea thats what i did also

---

### Post by chris062689 on 2008-07-09
Apparently it detected my GPU temps; but not my CPU.
E7200.

Got any ideas?

---

### Post by chris062689 on 2008-07-16
Sorry for the late response, I rebooted and everything works great!
Thanks a lot!
Theres one sensor that's reading at -2C, which I find odd, and it says my fan RPM is running at 2200 RPM :P

---

### Post by Dr Small on 2008-07-16
I found that on my systems, none of the sensor's were accurate...

---

### Post by markbuntu on 2008-07-16
The sensor applet uses a formula to convert the sensor voltages to numbers, you can try tweaking the formula for your sensor(s) in

 usr/share/lm-sensors/sensors.conf.eg

---

### Post by markbuntu on 2008-07-16
sorry, double post.

---

### Post by chris062689 on 2008-07-18
> **Dr Small said:**
> I found that on my systems, none of the sensor's were accurate...

There pretty much the same as how they read on XP and through BIOS on mine.

---

### Post by Horomancer on 2008-07-19
I think I may be having some cooling trouble and want to check my temps.
I got the lm-sensor pack from Synaptic as well as X sensors from add/remove programs.
I ran the detect command and said yes to everything, but I don't know what to do now to get a reading.
I tried clicking on X sensor from Applications and it did nothing.
I'm also playing around with gDesklets and the ones made to show LM sensor data are blank.
What am i missing?

---

### Post by Vivaldi Gloria on 2008-07-19
This is how I installed sensors:

```
sudo apt-get install lm-sensors
sudo sensors-detect
```

Answered yes to all questions. Then loaded modules:

```
sudo /etc/init.d/module-init-tools
sudo sensors -s
```

Now the following command works in a terminal:

```
sensors
```

---

### Post by Horomancer on 2008-07-19
Yep that modules command did the trick and it proves my system is running warm (about 45 C)
I'm guessing Intl temp is the general temperature in the case and RD1 temp is my vid card temp?

---

### Post by Horomancer on 2008-07-19
Yep that modules command did the trick and it proves my system is running warm (about 45 C)
I'm guessing Intl temp is the general temperature in the case and RD1 temp is my vid card temp?

---

### Post by Vivaldi Gloria on 2008-07-19
> **Horomancer said:**
> Yep that modules command did the trick and it proves my system is running warm (about 45 C)
I'm guessing Intl temp is the general temperature in the case and RD1 temp is my vid card temp?

Actually different systems have different names. I have no Intl or RD1. It depends on the type of sensors on the mobo I guess. So I have no idea what Intl or RD1 is.

---

### Post by djxstream on 2008-08-25
i'm having the same issues with the same equipment!

e7200 & ep35-ds3l

however i got "sensors" to work in terminal. but i feel its not accurate?

```
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.14 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.89 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.33 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.88 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +0.10 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +0.08 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +3.07 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.17 V
fan1:        912 RPM  (min =    0 RPM)
fan2:       1022 RPM  (min =    0 RPM)
fan3:       1069 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +31.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:       +20.0°C  (low  = +127.0°C, high = +60.0°C)  sensor = thermal diode
temp3:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +1.700 V

```

the fan speeds change little by little, but the temp stay at exactly those temps, while i'll just reboot the machine and go into XP dual-booted and speedfan reports my CPU & GPU temps in the 45/55 range

and is in0 my CPU voltage? then whats cpu0_vid? i know my cpu voltage is NOT 1.7V

---

### Post by chris062689 on 2008-08-28
This information gets me worried.
In XP, my temps always spiked up a bit after a lot of usage (50C?)
But even in Ubuntu they stay at a constant 32C (with a tad bit of fluxation) though the nvidia card (9600GT) appears to be reporting correctly.

Can anyone verify this?  Solutions?

```
chris@chris-desktop:~$ sensors
it8718-isa-0290
Adapter: ISA adapter
in0:         +0.98 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.92 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.33 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +0.13 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +0.10 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +3.07 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.25 V
fan1:       1939 RPM  (min =   10 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +43.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:       +32.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = thermal diode
temp3:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +2.050 V
```

I assume temp1 is ambient, and temp2 is CPU?  Temp3?

---

### Post by chris062689 on 2008-08-28
New thermal information now that I installed Nvidia drivers.
```

chris@chris-desktop:~$ sensors
it8718-isa-0290
Adapter: ISA adapter
in0:         +0.98 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.92 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.33 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +0.13 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +0.10 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +3.07 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.25 V
fan1:       1885 RPM  (min =   10 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +43.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:       +32.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = thermal diode
temp3:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +2.050 V


```

---

