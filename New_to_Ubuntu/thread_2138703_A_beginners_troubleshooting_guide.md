---
title: "A beginners troubleshooting guide?"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by alhefner on 2013-04-25
Every now and again, my Ubuntu 12.04LTS will just stop responding to keyboard or mouse commands. I won't be able to switch windows and sometimes the desktop icons, and the icons on the left side, just disappear. At those times, all I can do is remove power from the system and reboot.

I would like to be able to find out what is going on at the time the "freeze" happens. So, if there's some kind of guide on how to investigate the matter, I would love to know about it!

---

### Post by mastablasta on 2013-04-25
> **alhefner said:**
> I would like to be able to find out what is going on at the time the "freeze" happens. So, if there's some kind of guide on how to investigate the matter, I would love to know about it!

there are system logs.

you can also try switching to console (crtl+alt+F1). if it works you can access logs or shutdown/restart safely.

if you can't get into console you could try using REISUB command to reboot safely.

this seems to be graphics driver issue. what are your specs?

---

### Post by alhefner on 2013-04-25
> **mastablasta said:**
> there are system logs.

you can also try switching to console (crtl+alt+F1). if it works you can access logs or shutdown/restart safely.

if you can't get into console you could try using REISUB command to reboot safely.

this seems to be graphics driver issue. what are your specs?

Oh boy, I'm a total nubie here. I don't know enough of the Linux commands to use the console even! But, when it's frozen, nothing from the keyboard has any effect anyway so, getting to the console doesn't work under that situation anyway.

As for the graphics specks, I checked using windoze device manager and all I find is "Intel HD graphics 3000 PCI bus 0, device 2, function 0". I know there's more to it but I don't know how to check.

The computer is a Toshiba Satellite C855-S5206 with 4GB ram and a 500GB HDD, two USB 2.0 ports, one USB 3.0. HDMI port, ethernet port...

Wish I could be more help to all you folks trying to help me but, until I learn more about Linux in general, I'm going to have to be led by the hand a bit...](*,)

---

### Post by Bashing-om on 2013-04-25
alhefner;
Give this a try and see if it works for ya to get a stable system;
Replace the graphics driver ->
launcher -> System Settings -> Additional Drivers. From there change the graphics driver.
[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by alhefner on 2013-04-26
> **Bashing-om said:**
> alhefner;
Give this a try and see if it works for ya to get a stable system;
Replace the graphics driver ->
launcher -> System Settings -> Additional Drivers. From there change the graphics driver.
[INDENT=2]
just try'n to help

[/INDENT]

Thank you for trying. I took a look and just get:
```
No proprietary drivers are in use on this system
```

---

### Post by mastablasta on 2013-04-26
for intel 3000 the drivers are in linux kernel. and this chip should work quite nicely with ubuntu.

hmm.. i wonder if you maybe have some hardware issue. the freezing can indicate them. it could be as simple as overheating or as complex as capacitor leak.

note that Unity uses 3D acceleration which ofcourse needs extra power. perhaps if you monitored fan speed and temperature... see if it gets high.
[http://www.webupd8.org/2012/07/monitor-hardware-temperature-in-ubuntu.html](http://www.webupd8.org/2012/07/monitor-hardware-temperature-in-ubuntu.html)

or try a different desktop interface such as Kubutnu desktop or Xubuntu desktop.

---

### Post by alhefner on 2013-04-26
> **mastablasta said:**
> for intel 3000 the drivers are in linux kernel. and this chip should work quite nicely with ubuntu.

hmm.. i wonder if you maybe have some hardware issue. the freezing can indicate them. it could be as simple as overheating or as complex as capacitor leak.

note that Unity uses 3D acceleration which ofcourse needs extra power. perhaps if you monitored fan speed and temperature... see if it gets high.
[http://www.webupd8.org/2012/07/monitor-hardware-temperature-in-ubuntu.html](http://www.webupd8.org/2012/07/monitor-hardware-temperature-in-ubuntu.html)

or try a different desktop interface such as Kubutnu desktop or Xubuntu desktop.

I'll try out that link!

I actually would like to try out different desktops just to see which I prefer. Problem is, I don't know how to switch them around and keep the additional drivers I have now for my ethernet and wireless internet...

---

### Post by alhefner on 2013-04-26
> **mastablasta said:**
> note that Unity uses 3D acceleration which ofcourse needs extra power. perhaps if you monitored fan speed and temperature... see if it gets high.
[http://www.webupd8.org/2012/07/monitor-hardware-temperature-in-ubuntu.html](http://www.webupd8.org/2012/07/monitor-hardware-temperature-in-ubuntu.html)

OK, installed Psensor and everything seems OK. At any rate, I did hear the fan speed up after my system froze the last time. One thing of interest was that I was watching video via a website at the time! Hmmmmm... could be something for me to think about...

---

### Post by mastablasta on 2013-04-26
> **alhefner said:**
> I actually would like to try out different desktops just to see which I prefer. Problem is, I don't know how to switch them around and keep the additional drivers I have now for my ethernet and wireless internet...


you can go to software center and install them there (for example kubuntu-desktop. then you just select the desktop you want to use on login. 

note that you might get some stuff duplicated (e.g dual network monitors, dual file managers etc). however you can easilly remove those later by pasting a long command into terminal and removing the desktop you do not use.

that way you proprietary drivers and such will stay where they are now.

---

### Post by mastablasta on 2013-04-26
> **alhefner said:**
>  One thing of interest was that I was watching video via a website at the time! 


what browser were you using? you could try another one.  do you have restricted extras package installed?

---

### Post by alhefner on 2013-04-26
> **mastablasta said:**
> what browser were you using? you could try another one.  do you have restricted extras package installed?

I was using Firefox. I do have the restricted areas enabled in the software center.

---

