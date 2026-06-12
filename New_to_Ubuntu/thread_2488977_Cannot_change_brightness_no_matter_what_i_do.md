---
title: "Cannot change brightness no matter what i do"
date: 2023-07-14
forum: New to Ubuntu
---

### Post by 0zgkoz0 on 2023-07-14
I have installed Ubuntu onto my surface laptop 4 and no matter what i try, commands or third party apps nothing can seem to change my brightness
I am running the linux surface kernel
Any idea what to try?

---

### Post by MAFoElffen on 2023-07-17
Do this... This just writes a value to the setting file in sysfs...
```

grep . $(ls -l /sys/class/backlight/*_backlight | awk '{print $9}')/brightness

```
That value is the current setting of the screen brightness...

You can change that value by echoing a number that location in the sysfs... Decrease the number for dimmer. Increase for brighter.
```

SysFS_Brightness=$(ls -l /sys/class/backlight/*_backlight | awk '{print $9 "/brightness"}')  # This sets the path and file system to where the setting is...
export Brightness_Default=$(grep . $SysFS_Brightness)  # This reads what the original setting was and saves it as an Environment variable
Brightness_Setting=0.75  # <-- Set this as how many percent brightness. 0.10 through 1.00
sudo echo $(awk -v brightness="${Brightness_Default}" -v setting="${Brightness_Setting}" 'BEGIN{print (brightness*setting)}') > $SysFS_Brightness  # This will set it.

```

---

