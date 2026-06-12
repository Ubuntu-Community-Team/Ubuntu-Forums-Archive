---
title: "cooler"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by vahevahevahevahe on 2012-04-16
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.
 
We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.
 
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

WHAT ME DO???

---

### Post by Bobhuber on 2012-04-16
> **vahevahevahevahe said:**
> # pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.
 
We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.
 
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

WHAT ME DO???
No, what ARE you doing. You need to let your bios control the fan speed . That's telling you that you don't have the chipset to manually control the fan using fancontrol.

---

