---
title: "CPU Thermal Sensor App"
date: 2020-03-17
forum: New to Ubuntu
---

### Post by robertweir on 2020-03-17
Hi
  I have a Ubuntu 4.19.83-v8-22 running on a Raspberry PI-4.  I have been having an issue with performance throttling as I have a surveillance system running 24/7.  I want an app that will monitor this situation and display ongoing CPU temperatures so I can test a new cooling solution I just purchased.  I have something called 'psense' but cannot get any CPU  Temperature information, only 'Free Memory.  Suggestions would be welcome...
Robert

---

### Post by MoebusNet on 2020-03-17
I don't have a Raspberry Pi 4 (yet), but DuckDuckGo volunteered: [https://askubuntu.com/questions/15832/how-do-i-get-the-cpu-temperature](https://askubuntu.com/questions/15832/how-do-i-get-the-cpu-temperature)

>  On Raspberry Pi, you can retrieve the temperature using vcgencmd:

```
 vcgencmd measure_temp 
``` 

---

### Post by robertweir on 2020-03-17
Thanks MoebusNet
     It works.  I was looking for a more graphical presentation.  Your CLI invocation does work though...
Robert

---

### Post by MoebusNet on 2020-03-17
That same link gives several methods of monitoring cpu temperature/system parameters via GUI, but I don't see any of them specified for a Raspberry Pi-type system. I suppose you could always experiment a little...

---

### Post by robertweir on 2020-03-17
HI MoebusNet

Thank you I have just tried 'lm-sensors', an app I am familiar with, but it does not support the SOC Processor that is in the Pi-4.  I will keep trying but will mark this thread solved.  Thanks for the URL and have a great day.
Robert

---

### Post by DuckHook on 2020-03-17
```
vcgencmd measure_temp
```&#8230;is not compiled for Ubuntu and there is no apt package for it.

As you noted, lm-sensors doesn't work with a Pi.

I use:```
watch cat /sys/class/thermal/thermal_zone0/temp
```The Pi will auto-throttle if it gets too hot but you could also build a script for a fan that watches this readout.

---

### Post by DuckHook on 2020-03-17
If you are willing to install all the accompanying bloat, glances does work on one of my Pi4-based NAS:```
sudo apt install glances
```It drags in a ton of stuff though, so not sure how happy you are with that.

---

