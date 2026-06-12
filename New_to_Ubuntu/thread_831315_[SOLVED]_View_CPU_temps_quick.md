---
title: "[SOLVED] View CPU temps quick"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by skymera on 2008-06-16
Hi
Got a new processor today and i cant view the temps.
I don't know how, is there a small app which i can just use from terminal to report the temps from the CPU?

Thanks a lot =D

---

### Post by sdennie on 2008-06-16
You should be able to type:

```

cat /proc/acpi/thermal_zone/*/temperature

```

---

### Post by RomeReactor on 2008-06-16
Hi. Alternatively, you can install sensors-applet, which you can then add to one of your panels to monitor CPU and GPU temperatures:
```
sudo aptitude install sensors-applet
```
then right-click on one of the panels, select 'Add to panel...' and look for 'Hardware Sensors Monitor'.

---

### Post by marialice on 2008-06-16
Or simply
```
acpi -t
```

---

