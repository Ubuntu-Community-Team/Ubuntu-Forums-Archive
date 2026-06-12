---
title: "power management"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by abhirajtk on 2011-10-01
i installed 10.04 version. on power management i can't see battery option.  

ac power and general option can see but can't see "on battery power".

 i think battery power can't detect. how can i solve this? 

also in panel i can see a battery indication. from there i couldn't get any information.i want to show current battery level, charging or discharging.

---

### Post by matt_symes on 2011-10-01
Hi

What is the make and model of the laptop ?

Kind regards

---

### Post by abhirajtk on 2011-10-01
toshiba L650-I5310

---

### Post by Frogs Hair on 2011-10-01
Try this command to see if the battery is detected . ```
sudo modprobe pmu_battery
```

---

### Post by matt_symes on 2011-10-01
Hi

> **abhirajtk said:**
> toshiba L650-I5310

Have a read through this thread

[http://ubuntuforums.org/showthread.php?t=1852231](http://ubuntuforums.org/showthread.php?t=1852231)

Kind regards

---

