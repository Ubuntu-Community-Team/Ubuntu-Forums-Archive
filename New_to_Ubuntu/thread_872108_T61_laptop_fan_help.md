---
title: "T61 laptop fan help"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by feedmeh8 on 2008-07-27
i have ubuntu 8.04 installed on the t61 lenovo laptop and the fan will not start at all ... ever. whereas if i boot in windows XP sp2 (what the laptop came with) the fan runs fine. It is a pretty big problem as it gets to so hot it shuts down sometimes .. i am wandering if there is anything in the 8.04 that allows fan control, or if there are any programs that could help me fix this problem. Any and all help appreciated. :D

---

### Post by tamoneya on 2008-07-27
just use "fancontrol".  Here is the man page: [http://linux.die.net/man/8/fancontrol](http://linux.die.net/man/8/fancontrol)

---

### Post by feedmeh8 on 2008-07-28
hey thanks for the help :) i got it and ran pwmconfig and got this output

```
Failed to set hwmon0/device/pwm1 to full speed
Something's wrong, check your fans!

```

logical assumption i suppose is hardware malfunction. but it works fine on my xp partition :/

---

### Post by tamoneya on 2008-07-28
you can also try fan1_input if pwm1 doesnt work.  Also make sure you are calling with sudo.  This directory is owned by root.

---

### Post by feedmeh8 on 2008-07-28
hmm ya thanks il try that 1. I opened it up and it does spin at lowest speed when i run pwmconfig but will not get to top speed ... terminal error spits out:

```
Found the following devices:
   hwmon0/device is thinkpad

Found the following PWM controls:
   hwmon0/device/pwm1
hwmon0/device/pwm1_enable stuck to 2
Failed to set hwmon0/device/pwm1 to full speed
Something's wrong, check your fans!
```

---

### Post by dannyman on 2008-12-08
Hello,

I have the same trouble with my T60p, except the fan is stuck on high, so I'm not too distraught:

```
1-11:14 root@T60p thinkpad_hwmon# **pwd**
/sys/devices/platform/thinkpad_hwmon
0-11:17 root@T60p thinkpad_hwmon# **ls -l pwm***
-rw-r--r-- 1 root root 4096 2008-12-08 09:54 pwm1
-rw-r--r-- 1 root root    0 2008-12-08 11:14 pwm1_enable
0-11:18 root@T60p thinkpad_hwmon# **cat pwm1_enable** 
2
0-11:18 root@T60p thinkpad_hwmon# **echo 1 > pwm1_enable**
bash: echo: write error: Operation not permitted
1-11:18 root@T60p thinkpad_hwmon# **pwmconfig** 
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0/device is thinkpad

Found the following PWM controls:
   hwmon0/device/pwm1
hwmon0/device/pwm1_enable stuck to 2
Failed to set hwmon0/device/pwm1 to full speed
Something's wrong, check your fans!
1-11:18 root@T60p thinkpad_hwmon# **sensors**
thinkpad-isa-0000
Adapter: ISA adapter
fan1:       3460 RPM
temp1:       +53.0°C                                    
temp2:       +43.0°C                                    
temp3:       +37.0°C                                    
temp4:       +72.0°C                                    
temp5:       +38.0°C                                    
temp7:       +35.0°C                                    
temp9:       +43.0°C                                    
temp10:      +54.0°C                                    
temp11:      +48.0°C
```

---

