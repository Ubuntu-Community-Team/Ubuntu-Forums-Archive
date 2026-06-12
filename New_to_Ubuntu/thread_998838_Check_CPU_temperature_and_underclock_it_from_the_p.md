---
title: "Check CPU temperature and underclock it from the panel?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by wangsacl on 2008-12-01
How to check the CPU temperature and underclock it from the panel? I remember doing something like this before, before clean installing Ubuntu 8.10, but after googling, I think I forget how to do it...

---

### Post by w4ett on 2008-12-01
Install the package lm-sensors via Synaptic or using apt-get.  This will report the temps and fan speeds.  After installing you will need to run the following command:
```
sudo sensors-detect
```
and follow the instructions.

To modify the CPU speed, add the applet to your panel:

---

### Post by wangsacl on 2008-12-05
OK, thanks!

---

### Post by wisd0m on 2008-12-26
> **w4ett said:**
> Install the package lm-sensors via Synaptic or using apt-get.  This will report the temps and fan speeds.  After installing you will need to run the following command:
```
sudo sensors-detect
```
and follow the instructions.

To modify the CPU speed, add the applet to your panel:


I did that, how to I see the temps and fan speed? Its not on the CPU speed applet. (8.10 64 bit gnome)

---

### Post by w4ett on 2008-12-26
> **wisd0m said:**
> I did that, how to I see the temps and fan speed? Its not on the CPU speed applet. (8.10 64 bit gnome)
wisd0m...it's generally better to start a new thread to get an answer (especially when the trhead is marked "solved")...but here ya go:

in the terminal type:

```
sensors
```

you will see an output like this:

---

