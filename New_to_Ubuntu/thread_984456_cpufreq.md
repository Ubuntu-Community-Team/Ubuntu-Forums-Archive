---
title: "cpufreq"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-11-16
I have installed this, and followed the tutorial for keeping my laptop cpu at maximum throttle....but whenever I start to do anything graphical, it will stay at max for about a minute or two....and then it will start to throttle halfway down (from 1.6ghz down to 1.28ghz) then back up to 1.6ghz.....and so on. 


does anyone know how to stop this?

---

### Post by binbash on 2008-11-16
sudo gedit /etc/rc.local

Before exit paste this : 

cpufreq-selector -g performance

---

### Post by B34ST1Y on 2008-11-16
that didn't fix my issue, it still throttles while under stress, =/


its peculiar, because 1.28ghz isnt a listed frequency that my processor can handle...yet it still throttles to it and kill performance

---

### Post by unutbu on 2008-11-16
I'm not sure that you want to do this, because your CPU(s) will be working at full clock speed even when it could be idle, but if you know what you are doing, this might work:

To set the scaling governor to full speed ("performance"):
```
echo performance | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```If you have more than one CPU, run the above command once for each cpu. Change cpu0 to cpu1, etc...


To see the available cpu scaling governors:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

```
To see what cpu scaling governor you are currently using:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
To watch your cpu clock speed:
```
watch -n 1 cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

```

---

### Post by B34ST1Y on 2008-11-16
I did that and it continued to throttle, I would watch it on a command line via a secondary monitor, and it would kick from 160000 to 800000 and then back and forth. Is there a way to just keep it max'd no matter what? is it reaching a temperature threshold that I can disable?

---

### Post by B34ST1Y on 2008-11-16
is there maybe some sort of underlying program that is throttling it...and overriding these settings I'm making? 


SOMEBODY please help.... @_@

---

