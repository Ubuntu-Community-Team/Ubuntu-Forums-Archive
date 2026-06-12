---
title: "Battery stuck at 60%"
date: 2024-09-03
forum: New to Ubuntu
---

### Post by nourladdinxd on 2024-09-03
Hi, I'm new to Ubuntu.
so i was using Windows 10 and my laptop is legion 5, i used lenovo vantage software to limit my battery charge percentage at 60% but before i install ubuntu i forgot to turn off this option and when i installed ubuntu it still stuck at 60%
how can i fix this thx in advance!

---

### Post by TheFu on 2024-09-03
Just a guess, but doesn't Lenovo have power management tools for Linux?  [https://forums.lenovo.com/t5/Ubuntu/Battery-and-power-management-in-Linux-on-ThinkPad-T14/m-p/5273940](https://forums.lenovo.com/t5/Ubuntu/Battery-and-power-management-in-Linux-on-ThinkPad-T14/m-p/5273940)  Maybe it is just for Thinkpads?  IDK.  That's what I'd try.

---

### Post by maniacx2 on 2024-09-04
You can do it using command line.

To disable charging threshold
```
echo '0' | sudo tee /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode
```

To enable charging thrshold
```
echo '1' | sudo tee /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode
```

If you are on Gnome desktop enviroment, and if you want doing it using GUI, you can use Gnome extension[B] Battery health charging

[/B][https://extensions.gnome.org/extension/5724/battery-health-charging/](https://extensions.gnome.org/extension/5724/battery-health-charging/)

Install extension manager app and install Battery health charging from there

---

### Post by grahammechanical on 2024-09-04
My suggestion would be to go into the UEFI settings utility and see if you can change it from. The battery is part of the motherboard and it is charged by motherboard electronic components. Software utilities would need to change motherboard settings.

Regards

---

