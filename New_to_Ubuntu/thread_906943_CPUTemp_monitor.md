---
title: "CPU/Temp monitor"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-09-01
Any recomendations for something to monitor my CPU/RAM usage, temperature, and possibly fan speed? Something that could sit on the desktop? Simple and lightweight. I tried to do the steps from [http://www.xawk.com/ubuntu-cpu-temperature.html](http://www.xawk.com/ubuntu-cpu-temperature.html) but i could not get XSensors to work. Anyone got any better ideas?

---

### Post by ds[de] on 2008-09-01
Maybe conky is for you.

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

It's also in the universe repository if my memory serves me correctly.


Regards,
ds[de]

---

### Post by Codemastadink on 2008-09-01
> **'ds[de] said:**
> Maybe conky is for you.

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

It's also in the universe repository if my memory serves me correctly.


Regards,
ds[de]

Cool thanks, any other ideas?

---

### Post by ramjet_1953 on 2008-09-01
I like a combination of two small applets that load on your task bar.

[COLOR="Blue"]1. Sensors applet
[/COLOR]
[COLOR="Blue"]2. HDD Temp
[/COLOR]
```
sudo apt-get install sensors-applet

```
When this loads, it will ask you if you want it to start at system boot and also some locations. Just click OK to all questions.

```
sudo apt-get install hddtemp

```
When this is done, just right-click on a blank section of the taskbar and select H[COLOR="Blue"]ardware Sensors Monitor[/COLOR] in the [COLOR="Blue"]System and Hardware[/COLOR] Section.

When the icon is on your toolbar, just right-click on it and select [COLOR="Blue"]preferences[/COLOR] to configure it. The [COLOR="Blue"]Sensors tab[/COLOR] will list all available sensors to monitor.

Regards,
Roger :cool:

---

### Post by fedex1993 on 2008-09-01
you also might need to install lm-sensors to detect the sensors

---

### Post by doas777 on 2008-09-01
check out this thread:
[HOW TO: Install and configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780")

there is a script you need to run to detect your sensors initially. I use lm-sensors wiht the Sensors-Applet panel applet, so the temp is always on my main panel. 

hope that helps
frank

---

### Post by Codemastadink on 2008-09-01
> **ramjet_1953 said:**
> 

When the icon is on your toolbar, just right-click on it and select [COLOR="Blue"]preferences[/COLOR] to configure it. The [COLOR="Blue"]Sensors tab[/COLOR] will list all available sensors to monitor.

Regards,
Roger :cool:


I dont have a taskbar.. i'm using a dock.. any way i could get around this?

---

### Post by doas777 on 2008-09-01
> **Codemastadink said:**
> I dont have a taskbar.. i'm using a dock.. any way i could get around this?

if you don;t have any panels (I keep one on type with the menus etc and keep the dock on the bottom.) 

perhaps conky would be better for you. look up the thread for info

---

### Post by lovinglinux on 2008-09-01
> **doas777 said:**
> check out this thread:
[HOW TO: Install and configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780")

there is a script you need to run to detect your sensors initially. I use lm-sensors wiht the Sensors-Applet panel applet, so the temp is always on my main panel. 

hope that helps
frank

That tutorial is outdated. Several posts on that thread and others tell that you don't have to do all those complicated stuff to install and configure sensors. 

You can follow a recent tutorial at [http://www.techthrob.com/tech/linuxsensors.php](http://www.techthrob.com/tech/linuxsensors.php) or at [http://ubuntuforums.org/showthread.php?t=854746&highlight=sensors+wrong+temperature&page=2](http://ubuntuforums.org/showthread.php?t=854746&highlight=sensors+wrong+temperature&page=2)

---

