---
title: "Temp monitor"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by iceman1992 on 2012-05-06
Is there a reliable temp monitor for Ubuntu? I downloaded lmsensors but I don't know how to install it :(

---

### Post by cmont899 on 2012-05-06
You can install lm-sensors from the apt repos:

```
sudo apt-get install lm-sensors
```

or

```
sudo aptitude install lm-sensors
```

---

### Post by iceman1992 on 2012-05-06
> **cmont899 said:**
> You can install lm-sensors from the apt repos:

```
sudo apt-get install lm-sensors
```or

```
sudo aptitude install lm-sensors
```That's it? I thought I had to do sensors detection and whatever else?

Oh and by the way I'm using a laptop

---

### Post by pqwoerituytrueiwoq on 2012-05-06
i think the installer now runs the detect-sensors program
if the sensors don't work run 
sudo sensors-detect and say yes to all

---

### Post by Enigmapond on 2012-05-06
Right...it will run the detect during installation. Just be aware that there is no GUI for lm-sensors. I would just use one of the screenlets for that. I have hddtemp reading out on my conky.

---

### Post by iceman1992 on 2012-05-06
Well I ran ```
sudo apt-get install lm-sensors
```
And ```
sudo sensors-detect
```
And I got this ```
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading cpuid... OK

```
Now do I follow what it says and enter 'service module-init-tools start' ?

---

### Post by iceman1992 on 2012-05-06
> **Enigmapond said:**
> Right...it will run the detect during installation. Just be aware that there is no GUI for lm-sensors. I would just use one of the screenlets for that. I have hddtemp reading out on my conky.
I ran the sensors-detect already, is that gonna be a problem? :???::???:
And now how do I make it show the readings? Just type 'sensors'?
Typing 'sensors' gives me this ```
ubuntu@ubuntu-K40IN:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +74.0°C  (crit = +111.0°C)

nouveau-pci-0200
Adapter: PCI adapter
temp1:        +79.0°C  (high = +100.0°C, crit = +95.0°C)

```Which one is the CPU temp? And what is the other?? :???:

---

### Post by shuttleworthwannabe on 2012-05-06
Not a direct solution to your needs--if you are willing to change to Gnome Shell, then there is an extension that will place a panel icon with the thermals showing all the time (realtime). I am not aware of similar panel icon in Unity. I may be wrong.

---

### Post by iceman1992 on 2012-05-07
> **shuttleworthwannabe said:**
> Not a direct solution to your needs--if you are willing to change to Gnome Shell, then there is an extension that will place a panel icon with the thermals showing all the time (realtime). I am not aware of similar panel icon in Unity. I may be wrong.
Are you referring to the computertemp applet? I don't need real time monitoring. Manually checking once in a while is okay for me. Is lmsensors reliable and accurate?

---

### Post by Lars Noodén on 2012-05-07
lm-sensors will reliably report what the sensors report.  As to how accurate they are is a different matter.  However, for the most part they should be close enough to the right temperature not to worry.

---

### Post by iceman1992 on 2012-05-07
Right. Can you help me identify which reading is which?
```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +72.0°C  (crit = +111.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +68.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +70.0°C  (high = +105.0°C, crit = +105.0°C)

nouveau-pci-0200
Adapter: PCI adapter
temp1:        +79.0°C  (high = +100.0°C, crit = +95.0°C)
```The coretemp-isa-0000 is obviously the CPU core temps.
What about the acpitz-virtual-0? What is it and why is it named virtual?
And what about the nouveau-pci-0200? 
Which one is the GPU temp?
Sorry for asking too many questions. I'm confused

---

