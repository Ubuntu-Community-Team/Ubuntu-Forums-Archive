---
title: "use something like corsair link in ubuntu?"
date: 2015-07-05
forum: New to Ubuntu
---

### Post by john409 on 2015-07-05
Several of my hardware components are Corsair branded. They make a cool app for windows called Corsair Link that gives me a nice picture of how my hardware is doing.

Is there any similar system in ubuntu that will let me see and control my fans and temperature from my motherboard, cooler, power supply, graphics card, and CPU?

Currently the best I can get is:

```
:~$ sensors && inxi -s
fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       77.91 W  (crit = 125.19 W)


k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +40.6°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +67.0°C)


Sensors:   System Temperatures: cpu: 40.1C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A

```
Which does not show much considering my ASROCK MOBO has 4 temp sensors, the H100i cooler has 1 (and a pump and 2 fans as well.)

---

### Post by tristan16 on 2015-07-06
Try Psensor from the Software Center. It's a very nice and lightweight monitor that graphs temperature and usages. It even supports showing data in the menu bar for quick access!

As far as changing fan speeds, everything I found was extremely outdated, some threads dating back to Ubuntu 7.04. Apparently lm-sensors used to be able to control fan speed, but I have no idea if it's still capable of this.

If you have an Nvidia GPU with the Nvidia drivers installed, you can enable the coolbits option and manually set GPU fan speed in the X Server settings.

---

