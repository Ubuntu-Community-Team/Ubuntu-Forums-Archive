---
title: "find out GPU temperatures"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by nerdinator on 2012-06-26
[CENTER][LEFT]I have an Nvidia GT 540M graphics card in my Dell XPS ,whose fan is making a lot of noise.
I want to check the GPU temperature.

I did ```
sudo apt-get-install lm-sensors 
```and ran ```
sensors
```.
[LEFT]It only gives me 
[/LEFT]

```
Adapter: Virtual device
temp1:        +95.0°C  (crit = +100.0°C)
temp2:        +95.0°C  (crit = +100.0°C)

nouveau-pci-0100

Adapter: PCI adapter

temp1:        +72.0°C  (high = +100.0°C, crit = +110.0°C)

```
How do I find the GPU temperatures?
ps : what is  "nouveau-pci-0100
 [LEFT]Adapter: PCI adapter"?[/LEFT]
[/LEFT]
[/CENTER]

---

### Post by MG&amp;TL on 2012-06-26
> **nerdinator said:**
> [CENTER][LEFT]I have an Nvidia GT 540M graphics card in my Dell XPS ,whose fan is making a lot of noise.
I want to check the GPU temperature.

I did ```
sudo apt-get-install lm-sensors 
```and ran ```
sensors
```.
[LEFT]It only gives me 
[/LEFT]

```
Adapter: Virtual device
temp1:        +95.0°C  (crit = +100.0°C)
temp2:        +95.0°C  (crit = +100.0°C)

nouveau-pci-0100

Adapter: PCI adapter

temp1:        +72.0°C  (high = +100.0°C, crit = +110.0°C)

```How do I find the GPU temperatures?
ps : what is  "nouveau-pci-0100
 [LEFT]Adapter: PCI adapter"?[/LEFT]
[/LEFT]
[/CENTER]



*nouveau *is an open-source driver set for Nvidia cards. Unless much mistaken, that *is* your GPU temp.

---

### Post by audiomick on 2012-06-26
And it is running very hot. My laptop has an nVidia card in it that runs very warm, but it rarely shows more than around 80°C for any of it's sensors.

I think it is time to consider opening the box and blowing out the dust, and maybe renewing the thermal paste between the heat sink and the hot bits.

---

### Post by jmfal on 2012-06-26
A+  to Audiomick

You can install "psensors"

```
  sudo apt-get install psensors    
```

It show gpu temp  and is just a gui for the terminal output.

install it,  open it up,  select what you want to display , then you close the window and there will be a thermometer icon in the top toolbar that you can click on 

this way you don't have a terminal open all the time

---

### Post by Cheesemill on 2012-06-26
Try running:
```
sudo sensors-detect
```to make sure that all of your sensors are properly configured.

You can select the default for all answers but answering yes to:
```
Do you want to add these lines automatically to /etc/modules? (yes/NO)
```Will save you from having to do any manual configuration.

After a reboot run 'sensors' again and you should get a more detailed output.

---

### Post by pqwoerituytrueiwoq on 2012-06-26
```
nvidia-settings -q GPUCoreTemp
```if you are using the closed source driver
```

me@lucid-desktop:~$ nvidia-settings -q GPUCoreTemp

  Attribute 'GPUCoreTemp' (lucid-desktop:0.0): **28**.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

```you can open [FONT=Courier New]nvida-settings[/FONT] and go down to "PowerMizer" and "Thermal Settings"
if you are using 2 or more screens disconnect one and log out and in the temp should drop some (drops 5C for my moms system)

---

### Post by nerdinator on 2012-06-26
thank you for you replies.
@audiomick, it is very new laptop. I don't think dust should be an issue.
@jmfal , I did that. Thanks
@CheeseMill, yes I do get a more detailed output now.
@pqwoerituytrueiwoq  ,  I get this when I open nvidia-settings, 
```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```
and no I use only one screen (my laptop's).

---

### Post by nerdinator on 2012-06-26
Turns out,after the restart, it got cooler and the fan sound is gone.

```

acpitz-virtual-0
Adapter: Virtual device
temp1:        +65.0°C  (crit = +100.0°C)
temp2:        +65.0°C  (crit = +100.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +57.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +57.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +57.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:         +57.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:         +57.0°C  (high = +86.0°C, crit = +100.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +56.0°C  (high = +100.0°C, crit = +110.0°C)

```

 Core 0 to 3 must be the 4 cores of my quad core processor ,if I'm right.
and nouveau-pci-0100 is the GPU's as MG&TL told.

What are temp1,and temp2?

---

