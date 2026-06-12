---
title: "Ubuntu 20.04.3 won't shut down"
date: 2022-01-07
forum: New to Ubuntu
---

### Post by shiga23 on 2022-01-07
I'm having a problem:I have been trying to turn off my PC for days, the monitors turn off, but the power supply and the processor cooler are not cut off.
The components of my PC are:

AMD A10 9700
Asrock A320MK
16GB Ram
500 SSD
Sentey 500w generic

I tried the next commands:
$ sudo shutdown -h now
$ sudo poweroff
$ sudo reboot
-----------------------------------------------------
$ sudo grub-update
$ sudo nano /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;
Add **acpi=force** at the end:
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash acpi=force&#8221;
$ sudo nano /etc/modules
Add **apm=power_off=1**
$ sudo update-grub
-----------------------------------------------------

Update BIOS
I tried ALT+SYSRQ+REISUB
I tried ALT+SYSRQ+REISUO
I try booting an older kernel

Without any positive result.

P.S. Before the update it turned off normally. The same is happening with 7 other computers with the same components. I need help, thanks!!

---

### Post by col48 on 2022-01-11
If the OS is shut down but the power supply is still on....
does anybody have a more elegant solution than unplugging it (= turn off wall switch)?

---

### Post by TheFu on 2022-01-11
What do the system logs show at the time for each command above?  Any errors or warnings?

---

### Post by shiga23 on 2022-01-19
Nothing out of the ordinary, proceeded correctly.

---

### Post by shiga23 on 2022-01-19
> **col48 said:**
> If the OS is shut down but the power supply is still on....
does anybody have a more elegant solution than unplugging it (= turn off wall switch)?




Before some update x, it turned off without problems.

---

