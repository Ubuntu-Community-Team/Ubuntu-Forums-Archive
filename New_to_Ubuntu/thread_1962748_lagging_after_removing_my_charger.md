---
title: "lagging after removing my charger ?"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by G R E E N on 2012-04-21
how can remove the lag when i remove the charger i feel like ubuntu lags harder when running java

---

### Post by matt_symes on 2012-04-23
Hi

Is it reducing the CPU speed when on battery power ?

Open a terminal and type

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

to see the current governor on eah chip. To get a list of the available governors type

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```

To see the current frequency.

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
```

```
echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

This will run the performance governor but will reduce battery life. Unplug the charger.

Do you still have laggy performance with the performance governor ?

Kind regards

---

