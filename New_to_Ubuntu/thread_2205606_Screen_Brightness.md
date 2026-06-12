---
title: "Screen Brightness"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by bobbyk56 on 2014-02-14
Hi everyone,

I'm running Ubuntu 12.04.4 and everything seems to be running ok except for one thing. When I boot up I have to reset the screen bightness each time. Is there any way to have the setting remain so that I don't have to do  this?

Thanks,

---

### Post by just_me76570 on 2014-02-14
Try this :guitar:

[http://www.hecticgeek.com/2012/09/ubuntu-12-04-resetting-your-displays-brightness-levels-fix/](http://www.hecticgeek.com/2012/09/ubuntu-12-04-resetting-your-displays-brightness-levels-fix/)

---

### Post by Clifford_Sarokoff on 2014-02-15
I had a similar problem. It turned out that my Lenovo Y560 has a auto brightness setting that dims or brightens the screen depending on the brightness of the ambient light. When I ran Windows I disabled it. On my Ubuntu 13.10 setup there is no way (that I know of) to disable it. I solved the problem by placing a piece of tape over the sensor which is located above the keyboard.
CliffordS

---

### Post by bobbyk56 on 2014-02-15
Turns out the problem is because of the proprietary driver for my graphics (Radeon). Disabling the driver and using the open source driver cured that problem.

---

### Post by Psil0cybin on 2014-02-15
How did you do this? I had a similar problem with my Lenovo G700 booting with the backlight turned off, I solved it by changing grub settings to acpi_os=linux or something similar, additional drivers says there are no drivers for my computer.

---

