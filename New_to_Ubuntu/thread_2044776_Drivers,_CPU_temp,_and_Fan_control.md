---
title: "Drivers, CPU temp, and Fan control"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by SOLS on 2012-08-19
I am very new to Ubuntu and PC building.  I just built my first PC as well, it is around the ASUS P8Z68-VLX mobo.  In the tutorials I have seen they talk about installing drivers for the chipset, sound, video card, etc.; it seems though that drivers are already installed on Ubuntu and each of the sites for my mobo and video card only work with Windows.  Is there something I am missing here?
Also the fan seems be running constantly from the get go, what is a way I can controll it? I am afraid the fan is what will ruin my CPU.  Lastly, I have installed through the terminal acpi and lm-sensors but the temperature the display I think is incorrect, everytime (Literally everytime) I display temperatures they read 
Thermal 0: ok, 29.8 degrees C
Thermal 1: ok, 27.8 degrees C
Which can't be right when the bios, from a cold boot says 40+ degrees C.  How do I get the temperature to read correctly?
I know it is a lot but if I can get help in resolving these 3 key issues I will be well on my way.  
-Cheers!

---

### Post by ub07 on 2012-08-20
Try running the following command:

```
sensors-detect
```

---

### Post by SOLS on 2012-08-20
Worked like a charm! Thanks!  Any idea on drivers or CPU fan control? Even if someone could point me to some threads already out there that would be awesome, been looking for some time for the right info.

---

