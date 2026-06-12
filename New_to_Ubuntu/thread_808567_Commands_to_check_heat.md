---
title: "Commands to check heat?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Kestol on 2008-05-26
Hi everybody,

I've searched but cant find commands or anything to show me the current heat of:

- Core/GPU
- Graphic Card
- And what else there is

So could anybody tell me where i can get things to show me the tempature? I had the command for the core once... But i cant find it anymore:(

Another thing...
Could you also possibly post an interval for each thing? I mean an interval that shows what is acceptable while idle and while gaming?

Thx! Really hope someone can help:)

---

### Post by Nepherte on 2008-05-26
lm-sensors might do what you want: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29)

If you have an nvidia card, you can check the temperature in:
```
nvidia-settings
```

---

### Post by dizee on 2008-05-26
```
acpi -V
``` will give you the CPU temperature.

---

### Post by nick_h on 2008-05-26
The package *hddtemp* will monitor hard drive temperature.
The *sensors-applet* is a useful applet to show temperatures in a Gnome panel.

---

