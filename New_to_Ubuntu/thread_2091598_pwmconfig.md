---
title: "pwmconfig"
date: 2012-12-05
forum: New to Ubuntu
---

### Post by katan82 on 2012-12-05
Hi all ):P . I recently changed my win os to ubuntu 12.10. My issue is I can't control the speed for all my fans which is my absolute priority becouse of noise.I have MSI P55 GD-80 and 4 additional fan installed.This is sensors output:
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +43.0°C  (high = +83.0°C, crit = +99.0°C)
Core 1:       +43.0°C  (high = +83.0°C, crit = +99.0°C)
Core 2:       +43.0°C  (high = +83.0°C, crit = +99.0°C)
Core 3:       +49.0°C  (high = +83.0°C, crit = +99.0°C)

f71889fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.38 V  
in1:          +1.22 V  (max =  +2.04 V)
in2:          +0.86 V  
in3:          +0.98 V  
in4:          +1.10 V  
in5:          +0.81 V  
in6:          +0.61 V  
3VSB:         +3.31 V  
Vbat:         +3.22 V  
fan1:        1429 RPM
fan2:        1163 RPM
fan3:         917 RPM
temp1:        +41.0°C  (high = +255.0°C, hyst = +251.0°C)
                       (crit = +255.0°C, hyst = +251.0°C)  sensor = thermistor
temp2:        +50.0°C  (high = +255.0°C, hyst = +251.0°C)
                       (crit = +255.0°C, hyst = +251.0°C)  sensor = thermistor
temp3:        +36.0°C  (high = +255.0°C, hyst = +253.0°C)
                       (crit = +255.0°C, hyst = +253.0°C)  sensor = transistor

pwmconfig foud this sensors:
   hwmon0/device is coretemp
   hwmon1/device is f71889fg

Win can control all my 5 fans smoothly using speedfan.
Fancontrol control my cpufan a 1 fan from 4.
Normally I'm not asking forums but using google first.
My question is can I control all my fans ? is it possible ?
C'mon guys help me out with this, thank u for any direction.
p.s sorry for my en ;p

---

