---
title: "Need help to install lm-sensors"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by wariskampar on 2008-08-04
I installed lm-sensor and run the detection wizard. However, in the end there was no sensor available in my sytem. Therefore, I follow the other step like in this page [http://www.lm-sensors.org/wiki/iwizard/NoSensorsDetected](http://www.lm-sensors.org/wiki/iwizard/NoSensorsDetected). When I run the detection wizard once again, I got this message at the end (see below). What does it mean? Do I need to do anything (copy file to other location etc..) or do I just restart my system. Thanks

Do you want to generate /etc/sysconfig/lm_sensors? (yes/NO): y
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.

ps: btw, how do I start the lm-sensors service

---

### Post by eightmillion on 2008-08-04
> sudo /etc/init.d/lm_sensors start.

---

### Post by tamoneya on 2008-08-04
for startup services it is easiest to go to system->administration->services.

Also the command to startup lm-sensors manually is:```
sudo /etc/init.d/lm-sensors start
```

---

### Post by Krydahl on 2008-08-04
As far as I know you have to restart the system to load the new kernel modules.

As for actually getting temp data once the system is restarted, you have several options:

Add the hardware sensors monitor to your panel

Type sensors into a terminal

Install a GUI based app - eg gkrellm (in the repositories).

---

### Post by wariskampar on 2008-08-04
After restart, I try to run sensors. I got below message. What does it mean. Is my lm-sensor no good for my system (mean can not be used)

aznan@aznan-laptop:~$ sensors 
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
aznan@aznan-laptop:~$

---

### Post by halitech on 2008-08-04
its possible depending on the age of your hardware. I have an old compaq laptop that lm-sensors can't see any sensors for so won't work

---

### Post by philinux on 2008-08-04
When you ran sensors-detect did it find any?

---

### Post by barney385 on 2008-08-04
> **philinux said:**
> When you ran sensors-detect did it find any?

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or [http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ)
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.
barney@barney-laptop:~$ 

I have the same problem. This  output is what I get after the sensors-detect command.

I have a T-9300 processor, but this is probably a Motherboard issue?

---

### Post by wariskampar on 2008-08-04
I also think it is simply because my mobo do not support it. Nevermind, I can live with that. Thanks guys

---

### Post by barney385 on 2008-08-04
> **wariskampar said:**
> I also think it is simply because my mobo do not support it. Nevermind, I can live with that. Thanks guys

Right-click your upper panel. Select "add to panel".

Scroll down to hardware monitor and click add...

My GPU is detected, but not my Cpu thermals...

ETA: Computer Temperature monitor is also on the scroll down list...

---

### Post by alecz20 on 2008-09-15
> **barney385 said:**
> Right-click your upper panel. Select "add to panel".

Scroll down to hardware monitor and click add...

My GPU is detected, but not my Cpu thermals...

ETA: Computer Temperature monitor is also on the scroll down list...

I managed to install and configure lm-sensors, and I can use the program gkrellm to get the readings.

I don't have any applets for the panel though!

---

